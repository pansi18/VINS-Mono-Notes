cmake_minimum_required(VERSION 2.8.3)
project(ar_demo)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++14 -DEIGEN_DONT_PARALLELIZE")
#-DEIGEN_USE_MKL_ALL")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall -g")

set(cv3_bridge_DIR "/home/pansi/ws_vio/devel/share/cv3_bridge/cmake/")
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  image_transport
  sensor_msgs
  cv3_bridge
  message_filters
  camera_model
)

set(OpenCV_DIR "/home/pansi/open_projects/opencv-3.4.5/install_dir/share/OpenCV/")
find_package(OpenCV REQUIRED)

catkin_package(

)


include_directories(
  ${catkin_INCLUDE_DIRS}
)

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
find_package(Eigen3)
include_directories(
  ${catkin_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIR}
)

add_executable(ar_demo_node src/ar_demo_node.cpp)

 target_link_libraries(ar_demo_node
   ${catkin_LIBRARIES} ${OpenCV_LIBS}
 )


