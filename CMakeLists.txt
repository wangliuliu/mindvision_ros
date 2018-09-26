cmake_minimum_required(VERSION 2.8.3)
set( CMAKE_CXX_FLAGS "-std=c++11 -O3" )
project(mindVision)

find_package(catkin REQUIRED COMPONENTS
  roscpp
)



catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES mindVision
#  CATKIN_DEPENDS roscpp
#  DEPENDS system_lib
)

find_package(OpenCV  REQUIRED)
link_libraries("/lib/libMVSDK.so")
include_directories("include/")

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
)

add_executable(image_publisher src/image_publisher.cpp)
target_link_libraries(image_publisher
  ${catkin_LIBRARIES} ${OpenCV_LIBS}
)

