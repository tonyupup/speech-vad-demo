cmake_minimum_required(VERSION 2.8)
set(CMAKE_VERBOSE_MAKEFILE on)
project(vad-demo)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
#set(CMAKE_C_STANDARD 99)
file(GLOB SRC_FILES src/*.c src/*.h thirdparty/webrtc/common_audio/*/*.c thirdparty/webrtc/rtc_base/*.c*)
include_directories(thirdparty/webrtc) #thirdparty/include/webrtc
add_library(vad SHARED ${SRC_FILES})
add_executable(vad-demo main.c)
target_link_libraries(vad-demo vad pthread)
