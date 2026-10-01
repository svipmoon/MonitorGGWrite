cmake_minimum_required(VERSION 3.10)
project(HookWrite LANGUAGES CXX)

set(CMAKE_BUILD_TYPE Release)

string(REPLACE "-g" "" CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE}")
string(REPLACE "-g" "" CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

add_library(HookWrite SHARED Hook_GG.cpp)

target_compile_options(HookWrite PRIVATE
    -Os
    -fPIC
)

target_link_options(HookWrite PRIVATE
    -static-libstdc++
)

# Android log library (for __android_log_print)
target_link_libraries(HookWrite PRIVATE log)