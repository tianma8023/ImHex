cmake_minimum_required(VERSION 3.16)
project(libimhex)

set(CMAKE_CXX_STANDARD 20)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../../external/ImGui ${CMAKE_CURRENT_BINARY_DIR}/external/ImGui)

if (WIN32)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static-libstdc++ -static-libgcc -static")
endif()

add_library(libimhex STATIC
        source/helpers/event.cpp
        source/helpers/utils.cpp

        source/providers/provider.cpp

        source/views/view.cpp
        )

target_include_directories(libimhex PUBLIC include)
target_link_libraries(libimhex PUBLIC imgui)
