cmake_minimum_required(VERSION 3.2)
project(Chip8_Emulator)

set(CMAKE_CXX_STANDARD 11)

# Prepare "Catch" library for other executables
set(CATCH_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/catch)
add_library(Catch INTERFACE)
target_include_directories(Catch INTERFACE ${CATCH_INCLUDE_DIR})


INCLUDE(FindPkgConfig)
PKG_SEARCH_MODULE(SDL2 REQUIRED sdl2)
set(SOURCE_FILES src/main.cpp src/chip8.cpp src/chip8.h)
add_executable(Chip8_Emulator ${SOURCE_FILES})
target_link_directories(${PROJECT_NAME} PUBLIC ${SDL2_LIBRARY_DIRS})
INCLUDE_DIRECTORIES(${SDL2_INCLUDE_DIRS})
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${SDL2_LIBRARIES})