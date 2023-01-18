cmake_minimum_required(VERSION 3.10)

project(sdlTEST)

set(SRC "${PROJECT_SOURCE_DIR}/source/main.cpp")

include_directories(
	${PROJECT_SOURCE_DIR}/src
	${PROJECT_SOURCE_DIR}/include
)

file(GLOB all_SRCS
	"${PROJECT_SOURCE_DIR}/include/*.h"
	"${PROJECT_SOURCE_DIR}/include/*.hpp"
	"${PROJECT_SOURCE_DIR}/source/*.c"
	"${PROJECT_SOURCE_DIR}/source/*.cpp"
)

link_directories(
	${PROJECT_SOURCE_DIR}/src
	${PROJECT_SOURCE_DIR}/include
)

find_package (SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})

add_executable(sdlTEST ${all_SRCS})

target_link_libraries(
	sdlTEST
	PUBLIC
	${SDL2_LIBRARIES}
)

target_compile_features(sdlTEST PUBLIC cxx_std_17)
