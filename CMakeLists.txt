cmake_minimum_required (VERSION 3.4.3)

# Name your project. Can be anything.
project (TEdit)

# Minimal supported C++ version.
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Set binary output directories. Changing these paths will require you adjusting your resource path configuration!
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)


# Disable unused features to speed up build
set (URHO3D_CSHARP OFF CACHE BOOL "")
set (URHO3D_GLOW OFF CACHE BOOL "")
set (URHO3D_IK OFF CACHE BOOL "")
set (URHO3D_NETWORK OFF CACHE BOOL "")
set (URHO3D_URHO2D OFF CACHE BOOL "")
set (URHO3D_PHYSICS2D OFF CACHE BOOL "")
set (URHO3D_SAMPLES OFF CACHE BOOL "")
set (URHO3D_PROFILING OFF CACHE BOOL "")
set (URHO3D_TESTING OFF CACHE BOOL "")

# Include cloned engine directory in a build.
add_subdirectory(rbfx)

file(GLOB_RECURSE MY_CPP_FILES CONFIGURE_DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/Source/*.cpp)
file(GLOB_RECURSE MY_H_FILES CONFIGURE_DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/Source/*.h)

set(MY_SOURCE_FILES ${MY_CPP_FILES} ${MY_H_FILES})
add_executable(TEdit WIN32 ${MY_SOURCE_FILES})
target_link_libraries(TEdit Urho3D)
