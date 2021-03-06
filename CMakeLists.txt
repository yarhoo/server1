# Minimum required version of CMake
CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
IF(COMMAND CMAKE_POLICY)
	CMAKE_POLICY(SET CMP0003 NEW)
ENDIF(COMMAND CMAKE_POLICY)

# Set CMake project name
PROJECT(SERVER1)

FIND_PACKAGE(Threads)
#IF(CMAKE_HAVE_PTHREAD_CREATE)
#	SET(HAVE_PTHREAD 1)
#ENDIF(CMAKE_HAVE_PTHREAD_CREATE)

FIND_PACKAGE(OpenSSL)

include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}
	${OPENSSL_INCLUDE_DIR}
	${PROTOBUF_INCLUDE_DIR}
	${PROTOBUF_INCLUDE_DIR}/google
	${CMAKE_SOURCE_DIR}/src/other/boost
	${home_dir}/third_party/glog/include
	${home_dir}/third_party/gflags/include
	${home_dir}/third_party/gtest
	${CMAKE_CURRENT_BINARY_DIR}
	)

ADD_SUBDIRECTORY(base)
ADD_SUBDIRECTORY(proto)
ADD_SUBDIRECTORY(server)
ADD_SUBDIRECTORY(services)
