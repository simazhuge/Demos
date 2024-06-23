cmake_minimum_required(VERSION 3.5)

project(ormppdemo VERSION 0.1 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

##主要设置以下变量
set(ENABLE_SQLITE3 ON)
add_definitions(-DORMPP_ENABLE_SQLITE3)
add_subdirectory(ormpp)
include_directories(ormpp)
include_directories(ormpp/ormpp)

set(PROJECT_SOURCES
        main.cpp
)

add_executable(ormppdemo
    ${PROJECT_SOURCES}
)

#这里使用的是sqlite3
target_link_libraries(ormppdemo PRIVATE sqlite3)

# set_target_properties(ormppdemo PROPERTIES
#     ${BUNDLE_ID_OPTION}
#     MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
#     MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
#     MACOSX_BUNDLE TRUE
#     WIN32_EXECUTABLE TRUE
# )

# include(GNUInstallDirs)
# install(TARGETS ormppdemo
#     BUNDLE DESTINATION .
#     LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
#     RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
# )

# if(QT_VERSION_MAJOR EQUAL 6)
#     qt_finalize_executable(untitled)
# endif()
