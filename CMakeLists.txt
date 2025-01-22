cmake_minimum_required(VERSION 3.5.0)
project(kafka_tool VERSION 0.1.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED off)
set(CMAKE_CXX_EXTENSIONS off)

set(THREADS_PREFER_PTHREAD_FLAG ON)


find_package(PkgConfig REQUIRED)
pkg_check_modules(rdkafka REQUIRED IMPORTED_TARGET rdkafka)


find_package(PkgConfig REQUIRED)
pkg_check_modules(rdkafka++ REQUIRED IMPORTED_TARGET rdkafka++)


set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

add_executable(kafka_tool main.cpp)
target_link_libraries(${PROJECT_NAME} PUBLIC PkgConfig::rdkafka)
target_link_libraries(${PROJECT_NAME}  PUBLIC PkgConfig::rdkafka++)
target_link_libraries(${PROJECT_NAME} PRIVATE Threads::Threads)
