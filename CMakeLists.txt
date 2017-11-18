cmake_minimum_required (VERSION 3.2.3)
if (COMMAND cmake_policy)
    # Libraries linked via full path no longer produce linker search paths
    cmake_policy (SET CMP0003 NEW)
    # INTERFACE_LINK_LIBRARIES defines the link interface
    cmake_policy (SET CMP0022 NEW)
    # Disallow use of the LOCATION target property - so we set to OLD as we still need it
    cmake_policy (SET CMP0026 OLD)
    # MACOSX_RPATH is enabled by default
    cmake_policy (SET CMP0042 NEW)
    # Honor the visibility properties for SHARED target types only
    cmake_policy (SET CMP0063 OLD)
endif ()

project (Urho3DToolbox)
set (CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/CMake/Modules)
include (UrhoCommon)


create_symlink(${URHO3D_HOME}/bin/Autoload ${CMAKE_BINARY_DIR}/bin/Autoload)
create_symlink(${URHO3D_HOME}/bin/Data ${CMAKE_BINARY_DIR}/bin/Data)
create_symlink(${URHO3D_HOME}/bin/CoreData ${CMAKE_BINARY_DIR}/bin/CoreData)
create_symlink(bin/EditorData ${CMAKE_BINARY_DIR}/bin/EditorData)

include_directories(ThirdParty .)

add_subdirectory(ThirdParty)
add_subdirectory(Toolbox)
add_subdirectory(Editor)
add_subdirectory(UIEditor)
add_subdirectory(AssetViewer)
