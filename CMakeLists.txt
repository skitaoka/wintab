cmake_minimum_required(VERSION 2.4)
cmake_policy(SET CMP0015 NEW)
project(wintab)

set(CMAKE_BUILD_TYPE_INIT Release)

if(WIN32)
    add_definitions(
        -DVC_EXTRALEAN
        -DWIN32_LEAN_AND_MEAN
        -DNOMINMAX
        -D_USE_MATH_DEFINES
        -D_NO_DEBUG_HEAP
        -D_CRT_SECURE_NO_DEPRECATE
        -D_CRT_SECURE_NO_WARNINGS
        -D_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
        -D_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
    )

    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MD")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MDd")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /MP /openmp /bigobj")
endif(WIN32)

include_directories(
    "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

set(HEADERS
    include/wintab.h
    include/Utils.h
)

set(SOURCES
    src/Utils.c
)

add_library(
    wintab STATIC
        ${SOURCES}
        ${HEADERS}
)
