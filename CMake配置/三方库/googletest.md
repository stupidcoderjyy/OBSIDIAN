### MinGw
##### 1. googletest配置
获取googletest源码 → 使用`add_subdirectory`将源码目录加入cmake项目
##### 2. 测试目标
1. `enable_testing()`
2. `include(GoogleTest)`
3. 创建[[动态库、静态库、可执行目标|测试可执行目标]]
4. `gtest_discover_tests(${TARGET} WORKING_DIRECTORY ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})`
完整示例：
```CMake
enable_testing()
include(GoogleTest)

set(TARGET target)
add_executable(${TARGET}
	test.cpp
)
target_link_libraries(${TARGET} PRIVATE
    GTest::gtest_main
)

gtest_discover_tests(${TARGET}
	WORKING_DIRECTORY ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})
```
