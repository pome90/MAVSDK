add_library(mavsdk_geofence
    geofence.cpp
    geofence_impl.cpp
)

target_link_libraries(mavsdk_geofence
    mavsdk
)

set_target_properties(mavsdk_geofence
    PROPERTIES COMPILE_FLAGS ${warnings}
)

target_include_directories(mavsdk_geofence PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include/mavsdk>
    )

install(TARGETS mavsdk_geofence
    EXPORT mavsdk-targets
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    )

install(FILES
    include/plugins/geofence/geofence.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/mavsdk/plugins/geofence
)
