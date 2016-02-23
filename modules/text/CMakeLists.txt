set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR})

find_package(tesseract CONFIG REQUIRED)
set(HAVE_TESSERACT 1)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/text_config.hpp.in
               ${CMAKE_BINARY_DIR}/text_config.hpp @ONLY)

include_directories(${CMAKE_CURRENT_BINARY_DIR})

set(the_description "Text Detection and Recognition")
ocv_define_module(text opencv_ml opencv_highgui opencv_imgproc opencv_core opencv_features2d WRAP python)

target_include_directories(opencv_text ${CMAKE_INSTALL_PREFIX}/include/)
target_link_libraries(opencv_text tesseract::tesseract)
