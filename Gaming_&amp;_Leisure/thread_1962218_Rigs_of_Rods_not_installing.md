---
title: "Rigs of Rods not installing"
date: 2012-04-20
forum: Gaming &amp; Leisure
---

### Post by gandalf3 on 2012-04-20
i was attempting to install Rigs of Rods following this howto, [http://www.rigsofrods.com/wiki/pages/Installation_Guide](http://www.rigsofrods.com/wiki/pages/Installation_Guide) but when i attempted to add the repository apt link ```
deb [http://apt.rigsofrods.com/](http://apt.rigsofrods.com/) /
``` to /etc/apt/sources.list, it seemed to work until i got this error in synaptic package manager when it was reloading:

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```
Failed to fetch http://apt.rigsofrods.com/Sources  404  File not found
Failed to fetch http://apt.rigsofrods.com/Packages  404  File not found
Some index files failed to download. They have been ignored, or old ones used instead.

```here is the results of cat /etc/apt/sources.list:
```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://apt.rigsofrods.com/ /
deb-src http://apt.rigsofrods.com/ /

```all help appreciated..

---

### Post by Perfect Storm on 2012-04-23
Looks like they took down the repository or couldn't find any to maintain it.

---

### Post by gandalf3 on 2012-04-23
hm..
i also tried this installer [http://www.rigsofrods.com/threads/60338-new-installer-testing-for-Ubuntu-9.10-users!?highlight=Ubuntu+9.10+beta+installer]("http://www.rigsofrods.com/threads/60338-new-installer-testing-for-Ubuntu-9.10-users%21?highlight=Ubuntu+9.10+beta+installer") , not exactly expecting it to work..
(it didn't, but it looks like it downloaded all the files and everything, it just won't run..)
Thanks anyway..

---

### Post by Perfect Storm on 2012-04-24
You can try to compile the source.

---

### Post by gandalf3 on 2012-04-30
um
erm..
how do i do that?
(sorry to be such a noob.. :oops:)

---

### Post by gandalf3 on 2012-05-09
okay.. i followed the instructions on these pages: 
[http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries]("http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries")
[URL="http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux"]http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux
[/URL][http://www.rigsofrods.com/wiki/pages/Starting_RoR_under_Linux](http://www.rigsofrods.com/wiki/pages/Starting_RoR_under_Linux)
and i think i messed up the directories, or something.
when i tried to run the make command for the whole thing, i got an error.. "```
[ 50%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/DashBoardManager.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/RTTLayer.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/HighScoreWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/SelectorWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp: In member function ‘void Console::onLineClicked(MyGUI::Widget*)’:
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp:1048:61: error: ‘class MyGUI::InputManager’ has no member named ‘getLastPressedPosition’
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o] Error 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2
```"
and here is the terminal output as far back as it will scroll:
```

A    ror-trunk/source/main/utils/fontTextureHelper.h
A    ror-trunk/source/main/audio
A    ror-trunk/source/main/audio/SoundManager.cpp
A    ror-trunk/source/main/audio/Sound.cpp
A    ror-trunk/source/main/audio/SoundManager.h
A    ror-trunk/source/main/audio/SoundScriptManager.cpp
A    ror-trunk/source/main/audio/Sound.h
A    ror-trunk/source/main/audio/SoundScriptManager.h
A    ror-trunk/source/main/sqlite
A    ror-trunk/source/main/sqlite/sqlite3.c
A    ror-trunk/source/main/sqlite/sqlite3.h
A    ror-trunk/source/main/sqlite/sqlite3ext.h
A    ror-trunk/source/main/scripting
A    ror-trunk/source/main/scripting/GameScript.cpp
A    ror-trunk/source/main/scripting/LocalStorage.cpp
A    ror-trunk/source/main/scripting/ScriptEngine.h
A    ror-trunk/source/main/scripting/as_ogre.cpp
A    ror-trunk/source/main/scripting/CBytecodeStream.h
A    ror-trunk/source/main/scripting/GameScript.h
A    ror-trunk/source/main/scripting/LocalStorage.h
A    ror-trunk/source/main/scripting/as_ogre.h
A    ror-trunk/source/main/scripting/OgreScriptBuilder.cpp
A    ror-trunk/source/main/scripting/ScriptEngine.cpp
A    ror-trunk/source/main/scripting/CBytecodeStream.cpp
A    ror-trunk/source/main/scripting/OgreScriptBuilder.h
A    ror-trunk/source/main/COPYING
A    ror-trunk/source/main/json
A    ror-trunk/source/main/json/JSON.h
A    ror-trunk/source/main/json/LICENSE
A    ror-trunk/source/main/json/JSONValue.cpp
A    ror-trunk/source/main/json/JSON.cpp
A    ror-trunk/source/main/json/JSONValue.h
A    ror-trunk/source/main/json/README
A    ror-trunk/source/main/json/source.txt
A    ror-trunk/source/main/RoRPrerequisites.h
A    ror-trunk/source/main/CMakeLists.txt
A    ror-trunk/source/updater
A    ror-trunk/source/updater/wthread.cpp
A    ror-trunk/source/updater/installerlog.cpp
A    ror-trunk/source/updater/action.xpm
A    ror-trunk/source/updater/streams.xpm
A    ror-trunk/source/updater/wsyncdownload.h
A    ror-trunk/source/updater/VersionCompare.h
A    ror-trunk/source/updater/ConfigManager.h
A    ror-trunk/source/updater/utils.h
A    ror-trunk/source/updater/wizard.h
A    ror-trunk/source/updater/threadpool.h
A    ror-trunk/source/updater/checked.xpm
A    ror-trunk/source/updater/wxStrel.cpp
A    ror-trunk/source/updater/icon.rc
A    ror-trunk/source/updater/unchecked_dis.xpm
A    ror-trunk/source/updater/finished.xpm
A    ror-trunk/source/updater/checkedlistctrl.h
A    ror-trunk/source/updater/welcome.xpm
A    ror-trunk/source/updater/dest.xpm
A    ror-trunk/source/updater/cevent.cpp
A    ror-trunk/source/updater/Timer.h
A    ror-trunk/source/updater/symlink.cpp
A    ror-trunk/source/updater/download.xpm
A    ror-trunk/source/updater/platform.h
A    ror-trunk/source/updater/wsyncdownload.cpp
A    ror-trunk/source/updater/CMakeLists.txt
A    ror-trunk/source/updater/resource.h
A    ror-trunk/source/updater/tokenize.h
A    ror-trunk/source/updater/wizard.cpp
A    ror-trunk/source/updater/utils.cpp
A    ror-trunk/source/updater/ConfigManager.cpp
A    ror-trunk/source/updater/SHA1.h
A    ror-trunk/source/updater/threadpool.cpp
A    ror-trunk/source/updater/wthread.h
A    ror-trunk/source/updater/installerlog.h
A    ror-trunk/source/updater/extrapack.xpm
A    ror-trunk/source/updater/mainpack.xpm
A    ror-trunk/source/updater/checked_dis.xpm
A    ror-trunk/source/updater/checkedlistctrl.cpp
A    ror-trunk/source/updater/unchecked.xpm
A    ror-trunk/source/updater/wxStrel.h
A    ror-trunk/source/updater/unknown.xpm
A    ror-trunk/source/updater/licence.xpm
A    ror-trunk/source/updater/cevent.h
A    ror-trunk/source/updater/ror.ico
A    ror-trunk/source/updater/symlink.h
A    ror-trunk/source/updater/SHA1.cpp
A    ror-trunk/source/OgreCanvas
A    ror-trunk/source/OgreCanvas/CanvasContext.cpp
A    ror-trunk/source/OgreCanvas/CanvasTexture.h
A    ror-trunk/source/OgreCanvas/CanvasContext.h
A    ror-trunk/source/OgreCanvas/CanvasPrerequisites.h
A    ror-trunk/source/OgreCanvas/DynamicTexture.cpp
A    ror-trunk/source/OgreCanvas/DynamicTexture.h
A    ror-trunk/source/OgreCanvas/CMakeLists.txt
A    ror-trunk/source/OgreCanvas/CanvasTexture.cpp
A    ror-trunk/source/OgreCanvas/source.txt
A    ror-trunk/source/CMakeLists.txt
A    ror-trunk/tools
A    ror-trunk/tools/linux
A    ror-trunk/tools/linux/debian
A    ror-trunk/tools/linux/debian/angelscripti386
A    ror-trunk/tools/linux/debian/angelscripti386/DEBIAN
A    ror-trunk/tools/linux/debian/angelscripti386/DEBIAN/control
A    ror-trunk/tools/linux/debian/angelscripti386/usr
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local/include
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local/include/angelscript.h
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local/lib
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local/lib/libangelscript.so
A    ror-trunk/tools/linux/debian/angelscripti386/usr/local/lib/libangelscript-2.18.2.so
A    ror-trunk/tools/linux/debian/pagedGeometryi386
A    ror-trunk/tools/linux/debian/pagedGeometryi386/DEBIAN
A    ror-trunk/tools/linux/debian/pagedGeometryi386/DEBIAN/control
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/ImpostorPage.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/PagedGeometry.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/TreeLoader2D.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/TreeLoader3D.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/BatchPage.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/MersenneTwister.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/StaticBillboardSet.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/WindBatchPage.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/PagedGeometryConfig.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/PropertyMaps.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/BatchedGeometry.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/GrassLoader.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/RandomTable.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/include/PagedGeometry/WindBatchedGeometry.h
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/lib
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/lib/libPagedGeometry.a
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/lib/pkgconfig
A    ror-trunk/tools/linux/debian/pagedGeometryi386/usr/local/lib/pkgconfig/PagedGeometry.pc
A    ror-trunk/tools/linux/debian/MoFILEReaderi386
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/DEBIAN
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/DEBIAN/control
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local/include
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local/include/moFileReader.h
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local/include/moFileConfig.h
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local/lib
A    ror-trunk/tools/linux/debian/MoFILEReaderi386/usr/local/lib/libmoFileReader.so
A    ror-trunk/tools/linux/debian/README
A    ror-trunk/tools/linux/debian/PACKAGES
A    ror-trunk/tools/linux/debian/PACKAGES/angelscript-2.19.0-i386.deb
A    ror-trunk/tools/linux/debian/PACKAGES/moFileReader-stable-i386.deb
A    ror-trunk/tools/linux/debian/PACKAGES/pagedGeometry-1.5-i386.deb
A    ror-trunk/tools/linux/binaries
A    ror-trunk/tools/linux/binaries/plugins.cfg
A    ror-trunk/tools/linux/findDist.sh
A    ror-trunk/tools/mutexdebug.py
A    ror-trunk/tools/buildbot
A    ror-trunk/tools/buildbot/bootstrap.bat
A    ror-trunk/tools/buildbot/test.bat
A    ror-trunk/tools/buildbot/clean.bat
A    ror-trunk/tools/buildbot/install.bat
A    ror-trunk/tools/buildbot/compile.bat
A    ror-trunk/tools/getLayoutsStringsForTranslation.py
A    ror-trunk/tools/createCMakeLists.py
A    ror-trunk/tools/windows
A    ror-trunk/tools/windows/binaries
A    ror-trunk/tools/windows/binaries/Release
A    ror-trunk/tools/windows/binaries/Release/plugins.cfg
A    ror-trunk/tools/windows/binaries/RelWithDebInfo
A    ror-trunk/tools/windows/binaries/RelWithDebInfo/plugins.cfg
A    ror-trunk/tools/windows/binaries/Debug
A    ror-trunk/tools/windows/binaries/Debug/plugins_d.cfg
A    ror-trunk/CMakeMacros.txt
A    ror-trunk/doc
A    ror-trunk/doc/Doxyfile.angelscript.linux.conf
A    ror-trunk/doc/Doxyfile.source.windows.conf
A    ror-trunk/doc/Things you can do in Rigs of Rods.pdf
A    ror-trunk/doc/footer.html
A    ror-trunk/doc/updateDoc.sh
A    ror-trunk/doc/Doxyfile.source.linux.conf
A    ror-trunk/doc/Doxyfile.configurator.linux.conf
A    ror-trunk/doc/Doxyfile.updater.linux.conf
A    ror-trunk/doc/keysheet.pdf
A    ror-trunk/doc/angelscript
A    ror-trunk/doc/angelscript/game.h
A    ror-trunk/doc/angelscript/races.as
A    ror-trunk/doc/angelscript/BeamClass.h
A    ror-trunk/doc/angelscript/LocalStorage.h
A    ror-trunk/doc/angelscript/SettingsClass.h
A    ror-trunk/doc/angelscript/global_functions.h
A    ror-trunk/.svnignore
A    ror-trunk/COPYING
A    ror-trunk/bin
A    ror-trunk/bin/resources
A    ror-trunk/bin/resources/paged.zip
A    ror-trunk/bin/resources/materials.zip
A    ror-trunk/bin/resources/pssm.zip
A    ror-trunk/bin/resources/textures.zip
A    ror-trunk/bin/resources/skeleton.zip
A    ror-trunk/bin/resources/meshes.zip
A    ror-trunk/bin/resources/particles.zip
A    ror-trunk/bin/resources/scripts.zip
A    ror-trunk/bin/resources/heathaze.zip
A    ror-trunk/bin/resources/mygui.zip
A    ror-trunk/bin/resources/sunburn.zip
A    ror-trunk/bin/resources/flags.zip
A    ror-trunk/bin/resources/famicons.zip
A    ror-trunk/bin/resources/hydrax.zip
A    ror-trunk/bin/resources/overlays.zip
A    ror-trunk/bin/resources/blur.zip
A    ror-trunk/bin/resources/OgreCore.zip
A    ror-trunk/bin/resources/caelum.zip
A    ror-trunk/bin/resources/glow.zip
A    ror-trunk/bin/resources/dof.zip
A    ror-trunk/bin/resources/airfoils.zip
A    ror-trunk/bin/resources/dashboards.zip
A    ror-trunk/bin/resources/wallpapers.zip
A    ror-trunk/bin/resources/icons.zip
A    ror-trunk/bin/resources/sounds.zip
A    ror-trunk/bin/resources/rtshader.zip
A    ror-trunk/bin/resources/hdr.zip
A    ror-trunk/CMakeDependenciesConfig.txt
A    ror-trunk/readme.txt
A    ror-trunk/CMakeLists.txt
 U   ror-trunk

Fetching external item into 'ror-trunk/source/main/network/protocol'
A    ror-trunk/source/main/network/protocol/rornet.h
Checked out external at revision 561.

Checked out revision 2534.
username@ubuntu01:~/ror-deps$ cd ror-trunk
username@ubuntu01:~/ror-deps/ror-trunk$ cmake -DROR_USE_MYGUI="TRUE" \
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.6
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.24.0
-- checking for module 'OGRE'
--   found OGRE, version 1.7.3
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.7.3
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.7.3
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.7.3
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Found CURL: /usr/lib/i386-linux-gnu/libcurl.so 
-- Found OpenAL: /usr/lib/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:      	YES
-- MYGUI_INCLUDE_DIRS: 	/usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS: 	/usr/local/lib
-- MYGUI_LIBRARIES:    	MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:      	YES
-- OPENAL_INCLUDE_DIRS: 	/usr/include/AL
-- OPENAL_LIBRARY_DIRS: 	
-- OPENAL_LIBRARIES:    	/usr/lib/libopenal.so
-- CURL Enabled:      	YES
-- CURL_INCLUDE_DIRS: 	/usr/include
-- CURL_LIBRARY_DIRS: 	
-- CURL_LIBRARIES:    	/usr/lib/i386-linux-gnu/libcurl.so
-- SOCKETW Enabled:      	YES
-- SOCKETW_INCLUDE_DIRS: 	/usr/local/include
-- SOCKETW_LIBRARY_DIRS: 	
-- SOCKETW_LIBRARIES:    	/usr/local/lib/libSocketW.so
-- PAGED Enabled:      	YES
-- PAGED_INCLUDE_DIRS: 	/usr/local/include;/usr/local/include/PagedGeometry
-- PAGED_LIBRARY_DIRS: 	
-- PAGED_LIBRARIES:    	/usr/local/lib/libPagedGeometry.a
-- CAELUM Enabled:      	YES
-- CAELUM_INCLUDE_DIRS: 	/usr/local/include/Caelum
-- CAELUM_LIBRARY_DIRS: 	
-- CAELUM_LIBRARIES:    	/usr/local/lib/libCaelum.so
-- ANGELSCRIPT Enabled:      	YES
-- ANGELSCRIPT_INCLUDE_DIRS: 	/usr/local/include;/home/username/ror-deps/ror-trunk/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS: 	
-- ANGELSCRIPT_LIBRARIES:    	/usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
-- Configuring done
-- Generating done
CMake Warning:
  Manually-specified variables were not used by the project:

    ROR_USE_LUA
    ROR_USE_MOFILEREADER


-- Build files have been written to: /home/username/ror-deps/ror-trunk
username@ubuntu01:~/ror-deps/ror-trunk$ make
Scanning dependencies of target angelscript_addons
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptbuilder/scriptbuilder.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptany/scriptany.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/autowrapper/generator/generateheader.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath3d/scriptmath3d.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/debugger/debugger.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthandle/scripthandle.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptfile/scriptfile.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/serializer/serializer.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring_utils.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring_utils.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthelper/scripthelper.cpp.o
[  9%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptdictionary/scriptdictionary.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptarray/scriptarray.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/contextmgr/contextmgr.cpp.o
[ 11%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmath.cpp.o
[ 11%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmathcomplex.cpp.o
Linking CXX static library ../../bin/libangelscript_addons.a
[ 11%] Built target angelscript_addons
Scanning dependencies of target RoR
[ 11%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundScriptManager.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundManager.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/Sound.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/SceneMouse.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/skin.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Savegame.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CharacterFactory.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/editor.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/DotSceneLoader.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Road.cpp.o
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/OutProtocol.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/road2.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Replay.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RigsOfRods.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Character.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ProceduralManager.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Landusemap.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PositionStorage.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/autopilot.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/skinmanager.cpp.o
[ 24%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TwoDReplay.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PlayerColours.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o
[ 26%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TorqueCurve.cpp.o
[ 27%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CacheSystem.cpp.o
[ 27%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/BeamEngine.cpp.o
[ 28%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/MaterialReplacer.cpp.o
[ 28%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/DepthOfFieldEffect.cpp.o
[ 29%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/Lens.cpp.o
[ 30%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DynamicRenderable.cpp.o
[ 30%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Skidmark.cpp.o
[ 31%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/envmap.cpp.o
[ 31%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ColoredTextAreaOverlayElement.cpp.o
[ 32%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DustManager.cpp.o
[ 33%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DecalManager.cpp.o
[ 33%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DynamicLines.cpp.o
[ 34%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/MovableText.cpp.o
[ 35%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DustPool.cpp.o
[ 35%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/WaterOld.cpp.o
[ 36%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ShadowManager.cpp.o
[ 36%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleCineCam.cpp.o
[ 37%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleSpline.cpp.o
[ 38%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleOrbit.cpp.o
[ 38%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorCharacter.cpp.o
[ 39%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorOrbit.cpp.o
[ 40%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorFree.cpp.o
[ 40%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraManager.cpp.o
[ 41%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorFixed.cpp.o
[ 41%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehavior.cpp.o
[ 42%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/SkyManager.cpp.o
[ 43%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Heathaze.cpp.o
[ 43%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/materialFunctionMapper.cpp.o
[ 44%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/PreviewRenderer.cpp.o
[ 44%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/FireExtinguisherAffector.cpp.o
[ 45%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreAreaEmitter.cpp.o
[ 46%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreBoxEmitter.cpp.o
[ 46%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/ExtinguishableFireAffector.cpp.o
[ 47%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreShaderParticleRenderer.cpp.o
[ 48%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/hdrlistener.cpp.o
[ 48%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/vidcam.cpp.o
[ 49%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/LoadingWindow.cpp.o
[ 49%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/dashboard.cpp.o
[ 50%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/DashBoardManager.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/RTTLayer.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/HighScoreWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/SelectorWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp: In member function ‘void Console::onLineClicked(MyGUI::Widget*)’:
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp:1048:61: error: ‘class MyGUI::InputManager’ has no member named ‘getLastPressedPosition’
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o] Error 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2
A    ror-trunk/bin/resources/mygui.zip
A    ror-trunk/bin/resources/sunburn.zip
A    ror-trunk/bin/resources/flags.zip
A    ror-trunk/bin/resources/famicons.zip
A    ror-trunk/bin/resources/hydrax.zip
A    ror-trunk/bin/resources/overlays.zip
A    ror-trunk/bin/resources/blur.zip
A    ror-trunk/bin/resources/OgreCore.zip
A    ror-trunk/bin/resources/caelum.zip
A    ror-trunk/bin/resources/glow.zip
A    ror-trunk/bin/resources/dof.zip
A    ror-trunk/bin/resources/airfoils.zip
A    ror-trunk/bin/resources/dashboards.zip
A    ror-trunk/bin/resources/wallpapers.zip
A    ror-trunk/bin/resources/icons.zip
A    ror-trunk/bin/resources/sounds.zip
A    ror-trunk/bin/resources/rtshader.zip
A    ror-trunk/bin/resources/hdr.zip
A    ror-trunk/CMakeDependenciesConfig.txt
A    ror-trunk/readme.txt
A    ror-trunk/CMakeLists.txt
 U   ror-trunk

Fetching external item into 'ror-trunk/source/main/network/protocol'
A    ror-trunk/source/main/network/protocol/rornet.h
Checked out external at revision 561.

Checked out revision 2534.
username@ubuntu01:~/ror-deps$ cd ror-trunk
username@ubuntu01:~/ror-deps/ror-trunk$ cmake -DROR_USE_MYGUI="TRUE" \
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.6
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.24.0
-- checking for module 'OGRE'
--   found OGRE, version 1.7.3
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.7.3
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.7.3
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.7.3
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Found CURL: /usr/lib/i386-linux-gnu/libcurl.so 
-- Found OpenAL: /usr/lib/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:      	YES
-- MYGUI_INCLUDE_DIRS: 	/usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS: 	/usr/local/lib
-- MYGUI_LIBRARIES:    	MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:      	YES
-- OPENAL_INCLUDE_DIRS: 	/usr/include/AL
-- OPENAL_LIBRARY_DIRS: 	
-- OPENAL_LIBRARIES:    	/usr/lib/libopenal.so
-- CURL Enabled:      	YES
-- CURL_INCLUDE_DIRS: 	/usr/include
-- CURL_LIBRARY_DIRS: 	
-- CURL_LIBRARIES:    	/usr/lib/i386-linux-gnu/libcurl.so
-- SOCKETW Enabled:      	YES
-- SOCKETW_INCLUDE_DIRS: 	/usr/local/include
-- SOCKETW_LIBRARY_DIRS: 	
-- SOCKETW_LIBRARIES:    	/usr/local/lib/libSocketW.so
-- PAGED Enabled:      	YES
-- PAGED_INCLUDE_DIRS: 	/usr/local/include;/usr/local/include/PagedGeometry
-- PAGED_LIBRARY_DIRS: 	
-- PAGED_LIBRARIES:    	/usr/local/lib/libPagedGeometry.a
-- CAELUM Enabled:      	YES
-- CAELUM_INCLUDE_DIRS: 	/usr/local/include/Caelum
-- CAELUM_LIBRARY_DIRS: 	
-- CAELUM_LIBRARIES:    	/usr/local/lib/libCaelum.so
-- ANGELSCRIPT Enabled:      	YES
-- ANGELSCRIPT_INCLUDE_DIRS: 	/usr/local/include;/home/username/ror-deps/ror-trunk/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS: 	
-- ANGELSCRIPT_LIBRARIES:    	/usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
-- Configuring done
-- Generating done
CMake Warning:
  Manually-specified variables were not used by the project:

    ROR_USE_LUA
    ROR_USE_MOFILEREADER


-- Build files have been written to: /home/username/ror-deps/ror-trunk
username@ubuntu01:~/ror-deps/ror-trunk$ make
Scanning dependencies of target angelscript_addons
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptbuilder/scriptbuilder.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptany/scriptany.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/autowrapper/generator/generateheader.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath3d/scriptmath3d.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/debugger/debugger.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthandle/scripthandle.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptfile/scriptfile.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/serializer/serializer.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring_utils.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring_utils.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthelper/scripthelper.cpp.o
[  9%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptdictionary/scriptdictionary.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptarray/scriptarray.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/contextmgr/contextmgr.cpp.o
[ 11%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmath.cpp.o
[ 11%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmathcomplex.cpp.o
Linking CXX static library ../../bin/libangelscript_addons.a
[ 11%] Built target angelscript_addons
Scanning dependencies of target RoR
[ 11%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundScriptManager.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundManager.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/Sound.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/SceneMouse.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/skin.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Savegame.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CharacterFactory.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/editor.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/DotSceneLoader.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Road.cpp.o
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/OutProtocol.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/road2.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Replay.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RigsOfRods.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Character.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ProceduralManager.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Landusemap.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PositionStorage.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/autopilot.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/skinmanager.cpp.o
[ 24%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TwoDReplay.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PlayerColours.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o
[ 26%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TorqueCurve.cpp.o
[ 27%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CacheSystem.cpp.o
[ 27%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/BeamEngine.cpp.o
[ 28%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/MaterialReplacer.cpp.o
[ 28%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/DepthOfFieldEffect.cpp.o
[ 29%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/Lens.cpp.o
[ 30%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DynamicRenderable.cpp.o
[ 30%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Skidmark.cpp.o
[ 31%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/envmap.cpp.o
[ 31%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ColoredTextAreaOverlayElement.cpp.o
[ 32%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DustManager.cpp.o
[ 33%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DecalManager.cpp.o
[ 33%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DynamicLines.cpp.o
[ 34%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/MovableText.cpp.o
[ 35%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DustPool.cpp.o
[ 35%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/WaterOld.cpp.o
[ 36%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ShadowManager.cpp.o
[ 36%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleCineCam.cpp.o
[ 37%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleSpline.cpp.o
[ 38%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicleOrbit.cpp.o
[ 38%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorCharacter.cpp.o
[ 39%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorOrbit.cpp.o
[ 40%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorFree.cpp.o
[ 40%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraManager.cpp.o
[ 41%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorFixed.cpp.o
[ 41%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehavior.cpp.o
[ 42%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/SkyManager.cpp.o
[ 43%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Heathaze.cpp.o
[ 43%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/materialFunctionMapper.cpp.o
[ 44%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/PreviewRenderer.cpp.o
[ 44%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/FireExtinguisherAffector.cpp.o
[ 45%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreAreaEmitter.cpp.o
[ 46%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreBoxEmitter.cpp.o
[ 46%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/ExtinguishableFireAffector.cpp.o
[ 47%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreShaderParticleRenderer.cpp.o
[ 48%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/hdrlistener.cpp.o
[ 48%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/vidcam.cpp.o
[ 49%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/LoadingWindow.cpp.o
[ 49%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/dashboard.cpp.o
[ 50%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/DashBoardManager.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/RTTLayer.cpp.o
[ 51%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/HighScoreWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/SelectorWindow.cpp.o
[ 52%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp: In member function ‘void Console::onLineClicked(MyGUI::Widget*)’:
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp:1048:61: error: ‘class MyGUI::InputManager’ has no member named ‘getLastPressedPosition’
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o] Error 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2
username@ubuntu01:~/ror-deps/ror-trunk$ mkdir ~/.rigsofrods 
username@ubuntu01:~/ror-deps/ror-trunk$ unzip ~/ror-trunk/bin/resources/skeleton.zip  -d ~/.rigsofrods/
unzip:  cannot find or open /home/username/ror-trunk/bin/resources/skeleton.zip, /home/username/ror-trunk/bin/resources/skeleton.zip.zip or /home/username/ror-trunk/bin/resources/skeleton.zip.ZIP.
username@ubuntu01:~/ror-deps/ror-trunk$ mkdir ~/.rigsofrods 
mkdir: cannot create directory `/home/username/.rigsofrods': File exists
username@ubuntu01:~/ror-deps/ror-trunk$ unzip ~/ror-deps/ror-trunk/bin/resources/skeleton.zip  -d ~/.rigsofrods/
Archive:  /home/username/ror-deps/ror-trunk/bin/resources/skeleton.zip
   creating: /home/username/.rigsofrods/packs/
  inflating: /home/username/.rigsofrods/packs/agora.zip  
  inflating: /home/username/.rigsofrods/packs/dafsemi.zip  
  inflating: /home/username/.rigsofrods/packs/simple-terrain.zip  
   creating: /home/username/.rigsofrods/terrains/
   creating: /home/username/.rigsofrods/vehicles/
   creating: /home/username/.rigsofrods/cache/
   creating: /home/username/.rigsofrods/config/
  inflating: /home/username/.rigsofrods/config/categories.cfg  
  inflating: /home/username/.rigsofrods/config/editor.cfg  
  inflating: /home/username/.rigsofrods/config/ground_models.cfg  
  inflating: /home/username/.rigsofrods/config/inertia_models.cfg  
  inflating: /home/username/.rigsofrods/config/input.map  
 extracting: /home/username/.rigsofrods/config/ogre.cfg  
 extracting: /home/username/.rigsofrods/config/RoR.cfg  
  inflating: /home/username/.rigsofrods/config/skidmarks.cfg  
  inflating: /home/username/.rigsofrods/config/torque_models.cfg  
  inflating: /home/username/.rigsofrods/config/wavefield.cfg  
   creating: /home/username/.rigsofrods/logs/
username@ubuntu01:~/ror-deps/ror-trunk$ wget http://sourceforge.net/projects/rigsofrods/files/rigsofrods/0.37/content-pack-0.37.zip/download -O content-pack-0.37.zip
--2012-05-09 12:18:33--  http://sourceforge.net/projects/rigsofrods/files/rigsofrods/0.37/content-pack-0.37.zip/download
Resolving sourceforge.net... 216.34.181.60
Connecting to sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/project/rigsofrods/rigsofrods/0.37/content-pack-0.37.zip?r=&ts=1336591113&use_mirror=softlayer [following]
--2012-05-09 12:18:33--  http://downloads.sourceforge.net/project/rigsofrods/rigsofrods/0.37/content-pack-0.37.zip?r=&ts=1336591113&use_mirror=softlayer
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://softlayer.dl.sourceforge.net/project/rigsofrods/rigsofrods/0.37/content-pack-0.37.zip [following]
--2012-05-09 12:18:34--  http://softlayer.dl.sourceforge.net/project/rigsofrods/rigsofrods/0.37/content-pack-0.37.zip
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 426693318 (407M) [application/octet-stream]
Saving to: `content-pack-0.37.zip'

100%[======================================>] 426,693,318  237K/s   in 39m 9s  

2012-05-09 12:57:48 (177 KB/s) - `content-pack-0.37.zip' saved [426693318/426693318]

username@ubuntu01:~/ror-deps/ror-trunk$ unzip content-pack-0.37.zip -d ~/.rigsofrods/packs/
Archive:  content-pack-0.37.zip
unpack this folder to your RoR installation folder
   creating: /home/username/.rigsofrods/packs/streams/
   creating: /home/username/.rigsofrods/packs/streams/aircraft/
  inflating: /home/username/.rigsofrods/packs/streams/aircraft/Boeing-CH47-Chinook.zip  
  inflating: /home/username/.rigsofrods/packs/streams/aircraft/SU-37_2.1.zip  
   creating: /home/username/.rigsofrods/packs/streams/buses/
  inflating: /home/username/.rigsofrods/packs/streams/buses/46a6UID-FlxibleMetroD.zip  
  inflating: /home/username/.rigsofrods/packs/streams/buses/S53RX_V2.zip  
  inflating: /home/username/.rigsofrods/packs/streams/buses/S53R_V2.zip  
  inflating: /home/username/.rigsofrods/packs/streams/buses/Saviem_S53.zip  
   creating: /home/username/.rigsofrods/packs/streams/cars/
  inflating: /home/username/.rigsofrods/packs/streams/cars/accord.zip  
  inflating: /home/username/.rigsofrods/packs/streams/cars/Box69Camaro.zip  
  inflating: /home/username/.rigsofrods/packs/streams/cars/BoxDodgeRam.zip  
  inflating: /home/username/.rigsofrods/packs/streams/cars/BurnsideV3.zip  
   creating: /home/username/.rigsofrods/packs/streams/crawlers/
  inflating: /home/username/.rigsofrods/packs/streams/crawlers/Spidertrax_1.zip  
  inflating: /home/username/.rigsofrods/packs/streams/crawlers/squishycjtuber.zip  
  inflating: /home/username/.rigsofrods/packs/streams/crawlers/SquishyIndy.zip  
   creating: /home/username/.rigsofrods/packs/streams/extra-terrains/
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/abajo.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/acker.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/acty.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/angle.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/asphalt.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/avitaquin.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/Cascades.zip  
  inflating: /home/username/.rigsofrods/packs/streams/extra-terrains/oahu.zip  
   creating: /home/username/.rigsofrods/packs/streams/loads/
  inflating: /home/username/.rigsofrods/packs/streams/loads/0b86UID-ArrowBoardTrailer.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/45foottrailer_2.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/4fb9UID-jerseybarrier.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/Container-Packv1a_1.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/K100lowboy.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/oildrum_1.zip  
  inflating: /home/username/.rigsofrods/packs/streams/loads/twentyfootcontainer.zip  
   creating: /home/username/.rigsofrods/packs/streams/misc-land/
  inflating: /home/username/.rigsofrods/packs/streams/misc-land/AT-TE.zip  
  inflating: /home/username/.rigsofrods/packs/streams/misc-land/rofanzd4_dieseltug.zip  
  inflating: /home/username/.rigsofrods/packs/streams/misc-land/zetor.zip  
   creating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/
  inflating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/182bUID-MML201.zip  
  inflating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/1980Yota.zip  
  inflating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/BoxSamurai.zip  
  inflating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/RipSaw.zip  
  inflating: /home/username/.rigsofrods/packs/streams/offroad-vehicles/SIIILW.zip  
   creating: /home/username/.rigsofrods/packs/streams/terrains/
  inflating: /home/username/.rigsofrods/packs/streams/terrains/aspen.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/bajarama.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/BajaTrack.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/BakersRanch.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/dega1.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/f1track.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/Flatmap.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/grenoble.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/island.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/nhelens.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/Penguinville.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/simple.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/smallisland.zip  
  inflating: /home/username/.rigsofrods/packs/streams/terrains/squishymonsterstadium.zip  
   creating: /home/username/.rigsofrods/packs/streams/testing/
  inflating: /home/username/.rigsofrods/packs/streams/testing/Box5SledPull.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/Caterpillar-D9.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/coaster.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/dodgechargerv2.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/hovertest-pernodefrictin.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/MudFest.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/tracktestv15.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/TractionTest.zip  
  inflating: /home/username/.rigsofrods/packs/streams/testing/W900_with_glow.zip  
   creating: /home/username/.rigsofrods/packs/streams/trucks/
  inflating: /home/username/.rigsofrods/packs/streams/trucks/Box5W900.zip  
  inflating: /home/username/.rigsofrods/packs/streams/trucks/ScaniaR480TLc5b5UID.zip  
   creating: /home/username/.rigsofrods/packs/streams/vehicles/
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/1stGenDodges.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/767.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/agora.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/ampliroll.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/An-12.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/An225.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/AST1Xplanetowtruck.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/BobcatS130.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/C1boat.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/Chemicaltrailer.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/ChevyS10.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/CMTmisc.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/concorde.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/cranedaf.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/dafsemi.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/dakardaf.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/Dodge1500.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/dodgecharger.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/dodgepolice.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/dodgeviper.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/DryVanTrailer.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/euro-signs.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/hilux.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/HouseBoat.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/jerseybarrier.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/k100.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/kerax.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/Lexus.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/liebherr.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/MANTGX.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/meanmachines.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/Mig-25.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/MTVR.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/P51.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/Panther.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/renaultcrane.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/scaniawreckers.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/skiploader.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/smit.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/SprinterVans.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/squishycrushstuff.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/tatra813.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/travelgo.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/turbotwin.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/twinotter.zip  
  inflating: /home/username/.rigsofrods/packs/streams/vehicles/wahoo.zip  
  inflating: /home/username/.rigsofrods/packs/readme-content-pack-0.37.txt  
username@ubuntu01:~/ror-deps/ror-trunk$ mv   ~/.rigsofrods/packs/streams/* -t ~/.rigsofrods/packs/
username@ubuntu01:~/ror-deps/ror-trunk$ rmdir ~/.rigsofrods/packs/streams
username@ubuntu01:~/ror-deps/ror-trunk$ cd ror-trunk/bin
bash: cd: ror-trunk/bin: No such file or directory
username@ubuntu01:~/ror-deps/ror-trunk$ ./rorconfig
bash: ./rorconfig: No such file or directory
username@ubuntu01:~/ror-deps/ror-trunk$ ./RoR^C
username@ubuntu01:~/ror-deps/ror-trunk$ 

```
when i tried to find the configure file in /ror-trunk/bin, it wasn't there.. i also couldn't find the .exe or the .rogsofrods directory.. what did i do wrong?
if anyone can help, please do..:confused:
thanks

---

### Post by Perfect Storm on 2012-05-10
> /home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp: In member function ‘void Console::onLineClicked(MyGUI::Widget*)’:
/home/username/ror-deps/ror-trunk/source/main/gui/Console.cpp:1048:61: error: ‘class MyGUI::InputManager’ has no member named ‘getLastPressedPosition’
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gui/Console.cpp.o] Error 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2

Seems there's a bug in the source code. Better to contact the creator/devs of the game.

---

### Post by gandalf3 on 2012-07-09
thanks.. i didn't get it to work though..

now im trying wine, which  according to this :[URL="http://appdb.winehq.org/objectManager.php?sClass=version&iId=26074"] http://appdb.winehq.org/objectManager.php?sClass=version&iId=26074
[/URL] should work. but when i tried to install directx from here
[http://www.microsoft.com/en-us/download/confirmation.aspx?id=9033](http://www.microsoft.com/en-us/download/confirmation.aspx?id=9033)
wine just dumped a bunch of .CAB files in the directory i selected, then crashed.
could that be because i don't know what a "wine prefix" is? (when im prompted to select an installation directory, i just make a new folder in my home just so i can be sure it won't mess up my real C\ drive) but if that means it won't work..
the only difference i can see between my system and the example on wineHQ is im using 11.10 and different hardware.
all help appreciated:confused:

---

### Post by fallenshadow on 2012-07-11
I successfully compiled this game ages ago back when it was 0.35. I wouldn't mind having a go at compiling this new version, as I have it on Windows but not Ubuntu sadly.

If it is a success I can just pass on the compiled folder zipped up or something like that. :)

---

### Post by gandalf3 on 2012-07-11
really? let me know if you get it to work! that would be great!
thanks! :D
if you can, post some updates here on your progress.. 
thanks again!
(it will be interesting to see if it works on 11.10 after compiling in 12.04)

---

### Post by fallenshadow on 2012-07-12
Yes really, I want it on Ubuntu as much as you do! :)

I spent a rather large portion of the day installing required libs as their list is very incomplete. Now im onto compiling the required custom libs, I have about 3 of these left.

Im doing everything in a virtual machine so I don't go messing up my own system! :)

---

### Post by fallenshadow on 2012-07-12
:)

> [100%] Built target RoR

Now I just need to figure out how to get it to you! :D

---

### Post by gandalf3 on 2012-07-12
cool!
so i wonder what you did that made it work where mine didn't..? (those extra libs?)
well you definitely have more compiling experience than me, thats for sure
hmm... is there somewhere you could host it? then i could just download it..
or..

---

### Post by fallenshadow on 2012-07-12
The trick is to follow those directions loosely and make sure to read the important bits like Lua not being used anymore, so set that compile feature to FALSE. I followed the instructions loosely because some of that info is out of date.

Here is the download link from my UbuntuOne:

[http://ubuntuone.com/5nUxE3e0Jeo9fbYUDbyXEA](http://ubuntuone.com/5nUxE3e0Jeo9fbYUDbyXEA)

The launch executable and config executable are inside the bin folder.

Just a warning that it won't run unless you have the required libraries installed and its compiled for 32bit systems.

If it does not launch get back to me! :)

---

### Post by gandalf3 on 2012-07-13
it seems i don't have the all the correct libs..
in ror-trunk/bin/

```
./rorconfig 
./rorconfig: error while loading shared libraries: libOgreMain.so.1.7.4: cannot open shared object file: No such file or directory
```so i cd out and do

```
sudo apt-get install libOgreMain.so.1.7.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package libOgreMain.so.1.7.4
E: Couldn't find any package by regex 'libOgreMain.so.1.7.4'

```obviously it's not going to let me get easily.. but i suspect im doing something dumb..
or do i have to compile this one?
i thought i had every thing compiled from my previous attempts..

EDIT: oops..:oops: i had it installed just the wrong version.. 
i fixed that, and now the configurator starts, but it can't find any render systems
```
username@ubuntu01:~/ror-trunk2/bin$ ./rorconfig
 * log path:         /home/username/.rigsofrods/logs/
 * config path:      /home/username/.rigsofrods/config/
 * user path:        /home/username/.rigsofrods/
 * program path:     /home/username/ror-trunk2/bin/
 * used plugins.cfg: /home/username/ror-trunk2/bin/resources/plugins.cfg
 * used ogre.cfg:    /home/username/.rigsofrods/config/ogre.cfg
 * used ogre.log:    /home/username/.rigsofrods/logs/RoR.log
11:54:34 AM: log started
11:54:34 AM: searching languages in languages
11:54:34 AM: no Languages found!
11:54:34 AM: asking system for default language.
11:54:34 AM:  system returned: English (U.S.)(en_US)
11:54:34 AM: preferred language: English (U.S.)
11:54:34 AM: lang file: languages/en/LC_MESSAGES/ror.mo
11:54:34 AM: looking for catalog 'wxstd' in path 'languages/en_US.UTF-8/LC_MESSAGES:languages/:languages/en_US.UTF-8:/home/username/ror-trunk2/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US.UTF-8:languages/en_US/LC_MESSAGES:languages/:languages/en_US:/home/username/ror-trunk2/share/locale/en_US/LC_MESSAGES:/usr/share/locale/en_US/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US:languages/en/LC_MESSAGES:languages/:languages/en:/home/username/ror-trunk2/share/locale/en/LC_MESSAGES:/usr/share/locale/en/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en'.
11:54:34 AM: catalog file for domain 'wxstd' not found.
11:54:34 AM: looking for catalog 'wxgtk' in path 'languages/en_US.UTF-8/LC_MESSAGES:languages/:languages/en_US.UTF-8:/home/username/ror-trunk2/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US.UTF-8:languages/en_US/LC_MESSAGES:languages/:languages/en_US:/home/username/ror-trunk2/share/locale/en_US/LC_MESSAGES:/usr/share/locale/en_US/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US:languages/en/LC_MESSAGES:languages/:languages/en:/home/username/ror-trunk2/share/locale/en/LC_MESSAGES:/usr/share/locale/en/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en'.
11:54:34 AM: catalog file for domain 'wxgtk' not found.
11:54:34 AM: language not existing, no lang_locale support!
11:54:34 AM: Creating dialog

(rorconfig:3491): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `width > 0' failed
11:54:34 AM: Known Audio Devices: 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
11:54:35 AM:  *PulseAudio Default
11:54:35 AM:  *SB Live! EMU10k1 Analog Stereo via PulseAudio
11:54:35 AM:  *ALSA Default
11:54:35 AM:  *SB Live! Value [CT4780] [ADC Capture/Standard PCM Playback] (hw:0,0) via ALSA
11:54:35 AM:  *SB Live! Value [CT4780] [Multichannel Capture/PT Playback] (hw:0,2) via ALSA
11:54:35 AM:  *SB Live! Value [CT4780] [Multichannel Playback] (hw:0,3) via ALSA
11:54:35 AM:  *PortAudio Default
11:54:35 AM:  *No Output
11:54:35 AM: Sound Extensions: 
11:54:35 AM: Setting default values
11:54:35 AM: Loading config
11:54:35 AM: Loading RoR.cfg
11:54:35 AM: reading from Config file: /home/username/.rigsofrods//config/RoR.cfg
11:54:35 AM: Creating Ogre root
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.15.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
/home/username/ror-trunk2/bin//plugins.cfg not found, automatic plugin loading disabled.
11:54:35 AM: Root restore config
11:55:09 AM: Showing dialog
11:55:09 AM: App ready
``````
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
/home/username/ror-trunk2/bin//plugins.cfg not found, automatic plugin loading disabled.
```i'll keep googleing.. and hope i find out what to do:razz:
thanks
EDIT2:
i found the plugins.cfg file thanks to this: [http://www.rigsofrods.com/threads/86778-No-render-systems-error-and-no-skeleton-folder](http://www.rigsofrods.com/threads/86778-No-render-systems-error-and-no-skeleton-folder)
now i don't get any errors, but when i try to save and exit or save and play, it just gets stuck..
```
username@ubuntu01:~/ror-trunk2/bin$ ./rorconfig
 * log path:         /home/username/.rigsofrods/logs/
 * config path:      /home/username/.rigsofrods/config/
 * user path:        /home/username/.rigsofrods/
 * program path:     /home/username/ror-trunk2/bin/
 * used plugins.cfg: /home/username/ror-trunk2/bin/resources/plugins.cfg
 * used ogre.cfg:    /home/username/.rigsofrods/config/ogre.cfg
 * used ogre.log:    /home/username/.rigsofrods/logs/RoR.log
12:21:11 PM: log started
12:21:11 PM: searching languages in languages
12:21:11 PM: no Languages found!
12:21:11 PM: preferred language: English (U.S.)
12:21:11 PM: lang file: languages/en/LC_MESSAGES/ror.mo
12:21:11 PM: looking for catalog 'wxstd' in path 'languages/en_US.UTF-8/LC_MESSAGES:languages/:languages/en_US.UTF-8:/home/username/ror-trunk2/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US.UTF-8:languages/en_US/LC_MESSAGES:languages/:languages/en_US:/home/username/ror-trunk2/share/locale/en_US/LC_MESSAGES:/usr/share/locale/en_US/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US:languages/en/LC_MESSAGES:languages/:languages/en:/home/username/ror-trunk2/share/locale/en/LC_MESSAGES:/usr/share/locale/en/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en'.
12:21:11 PM: catalog file for domain 'wxstd' not found.
12:21:11 PM: looking for catalog 'wxgtk' in path 'languages/en_US.UTF-8/LC_MESSAGES:languages/:languages/en_US.UTF-8:/home/username/ror-trunk2/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/en_US.UTF-8/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US.UTF-8:languages/en_US/LC_MESSAGES:languages/:languages/en_US:/home/username/ror-trunk2/share/locale/en_US/LC_MESSAGES:/usr/share/locale/en_US/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en_US:languages/en/LC_MESSAGES:languages/:languages/en:/home/username/ror-trunk2/share/locale/en/LC_MESSAGES:/usr/share/locale/en/LC_MESSAGES:/usr/share/locale/:/usr/share/locale/en'.
12:21:11 PM: catalog file for domain 'wxgtk' not found.
12:21:11 PM: language not existing, no lang_locale support!
12:21:11 PM: Creating dialog

(rorconfig:3749): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `width > 0' failed
12:21:11 PM: Known Audio Devices: 
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:21:11 PM:  *PulseAudio Default
12:21:11 PM:  *SB Live! EMU10k1 Analog Stereo via PulseAudio
12:21:11 PM:  *ALSA Default
12:21:11 PM:  *SB Live! Value [CT4780] [ADC Capture/Standard PCM Playback] (hw:0,0) via ALSA
12:21:11 PM:  *SB Live! Value [CT4780] [Multichannel Capture/PT Playback] (hw:0,2) via ALSA
12:21:11 PM:  *SB Live! Value [CT4780] [Multichannel Playback] (hw:0,3) via ALSA
12:21:11 PM:  *PortAudio Default
12:21:11 PM:  *No Output
12:21:11 PM: Sound Extensions: 
12:21:11 PM: Setting default values
12:21:11 PM: Loading config
12:21:11 PM: Loading RoR.cfg
12:21:11 PM: reading from Config file: /home/username/.rigsofrods//config/RoR.cfg
12:21:12 PM: Creating Ogre root
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.15.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
Loading library /usr/local/lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
12:21:12 PM: Root restore config
12:21:12 PM: parsed resolution " 320 x  240" as "320 x 240 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  320 x  240
12:21:12 PM: parsed resolution " 400 x  300" as "400 x 300 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  400 x  300
12:21:12 PM: parsed resolution " 416 x  312" as "416 x 312 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  416 x  312
12:21:12 PM: parsed resolution " 512 x  384" as "512 x 384 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  512 x  384
12:21:12 PM: parsed resolution " 576 x  432" as "576 x 432 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  576 x  432
12:21:12 PM: parsed resolution " 640 x  480" as "640 x 480 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  640 x  480
12:21:12 PM: parsed resolution " 640 x  512" as "640 x 512 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  640 x  512
12:21:12 PM: parsed resolution " 680 x  384" as "680 x 384 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  680 x  384
12:21:12 PM: parsed resolution " 720 x  450" as "720 x 450 @ -1-bit"
12:21:12 PM: discarding resolution as the x res is below 800 pixels:  720 x  450
12:21:12 PM: parsed resolution " 800 x  512" as "800 x 512 @ -1-bit"
12:21:12 PM: parsed resolution " 800 x  600" as "800 x 600 @ -1-bit"
12:21:12 PM: parsed resolution " 832 x  624" as "832 x 624 @ -1-bit"
12:21:12 PM: parsed resolution " 840 x  525" as "840 x 525 @ -1-bit"
12:21:12 PM: parsed resolution " 896 x  672" as "896 x 672 @ -1-bit"
12:21:12 PM: parsed resolution " 960 x  540" as "960 x 540 @ -1-bit"
12:21:12 PM: parsed resolution " 960 x  600" as "960 x 600 @ -1-bit"
12:21:12 PM: parsed resolution "1024 x  768" as "1024 x 768 @ -1-bit"
12:21:12 PM: parsed resolution "1152 x  864" as "1152 x 864 @ -1-bit"
12:21:12 PM: parsed resolution "1280 x  960" as "1280 x 960 @ -1-bit"
12:21:12 PM: parsed resolution "1280 x 1024" as "1280 x 1024 @ -1-bit"
12:21:12 PM: parsed resolution "1360 x  768" as "1360 x 768 @ -1-bit"
12:21:12 PM: parsed resolution "1400 x 1050" as "1400 x 1050 @ -1-bit"
12:21:12 PM: parsed resolution "1440 x  900" as "1440 x 900 @ -1-bit"
12:21:12 PM: parsed resolution "1600 x 1024" as "1600 x 1024 @ -1-bit"
12:21:12 PM: parsed resolution "1680 x 1050" as "1680 x 1050 @ -1-bit"
12:21:12 PM: parsed resolution "1920 x 1080" as "1920 x 1080 @ -1-bit"
12:21:12 PM: Showing dialog
12:21:12 PM: App ready
12:23:13 PM: saving to Config file: /home/username/.rigsofrods//config/RoR.cfg
^C
username@ubuntu01:~/ror-trunk2/bin$ 

``````
12:23:13 PM: saving to Config file: /home/username/.rigsofrods//config/RoR.cfg
^C
```i let it go for almost five minuts but my CPU was almost on zero, nothing happening in ram etc.. 
i looked at the RoR.cfg file and it had all the changes i made, however when i jsut wnet ahead and ran the RoR executible this happened: ```
username@ubuntu01:~/ror-trunk2/bin$ ./RoR
 * log path:         /home/username/.rigsofrods/logs/
 * config path:      /home/username/.rigsofrods/config/
 * user path:        /home/username/.rigsofrods/
 * program path:     /home/username/ror-trunk2/bin/
 * used plugins.cfg: /home/username/ror-trunk2/bin/resources/plugins.cfg
 * used ogre.cfg:    /home/username/.rigsofrods/config/ogre.cfg
 * used ogre.log:    /home/username/.rigsofrods/logs/RoR.log
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.15.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
/home/username/ror-trunk2/bin/resources/plugins.cfg not found, automatic plugin loading disabled.


Configuration error: Run the RoRconfig program first.

Segmentation fault
username@ubuntu01:~/ror-trunk2/bin$
```EDIT3:
i just noticed this error : ```
/home/username/ror-trunk2/bin/resources/plugins.cfg not found, automatic plugin loading disabled.
```how many copies of one file does this program need?? i copied it in to /ror-trunk/resources/ and ran it again, the window popped up, it started loading, then just like that it was gone... :(
```
username@ubuntu01:~/ror-trunk2/bin$ ./RoR
 * log path:         /home/username/.rigsofrods/logs/
 * config path:      /home/username/.rigsofrods/config/
 * user path:        /home/username/.rigsofrods/
 * program path:     /home/username/ror-trunk2/bin/
 * used plugins.cfg: /home/username/ror-trunk2/bin/resources/plugins.cfg
 * used ogre.cfg:    /home/username/.rigsofrods/config/ogre.cfg
 * used ogre.log:    /home/username/.rigsofrods/logs/RoR.log
\Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.15.0
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
Loading library /usr/local/lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager
Installing plugin: Cg Program Manager
Plugin successfully installed
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Pentium(R) 4 CPU 3.20GHz
 *      SSE: yes
 *     SSE2: yes
 *     SSE3: yes
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: no
 * 3DNOWEXT: no
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: yes
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::_createRenderWindow "Rigs of Rods version 0.4.0", 800x600 windowed  miscParams: FSAA=0 displayFrequency=50 MHz gamma=No vsync=No 
GLXWindow::create used FBConfigID = 153
GL_VERSION = 2.1.2 NVIDIA 173.14.30
GL_VENDOR = NVIDIA Corporation
GL_RENDERER = GeForce 7900 GT/GTO/PCI/SSE2
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
Supported GLX extensions: GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GLSL support detected
GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
FBO PF_UNKNOWN depth/stencil support: D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R5G6B5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B5G6R5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8A8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2R10G10B10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2B10G10R10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT32_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT32_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_X8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_X8B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R3G3B2 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
[GL] : Valid FBO targets PF_UNKNOWN PF_R5G6B5 PF_B5G6R5 PF_R8G8B8 PF_B8G8R8 PF_A8R8G8B8 PF_B8G8R8A8 PF_A2R10G10B10 PF_A2B10G10R10 PF_FLOAT16_RGB PF_FLOAT16_RGBA PF_FLOAT32_RGB PF_FLOAT32_RGBA PF_X8R8G8B8 PF_X8B8G8R8 PF_SHORT_RGBA PF_R3G3B2 PF_SHORT_RGB 
RenderSystem capabilities
-------------------------
RenderSystem Name: OpenGL Rendering Subsystem
GPU Vendor: nvidia
Device Name: GeForce 7900 GT/GTO/PCI/SSE2
Driver Version: 2.1.2.0
 * Fixed function pipeline: yes
 * Hardware generation of mipmaps: yes
 * Texture blending: yes
 * Anisotropic texture filtering: yes
 * Dot product texture operation: yes
 * Cube mapping: yes
 * Hardware stencil buffer: yes
   - Stencil depth: 8
   - Two sided stencil support: yes
   - Wrap stencil values: yes
 * Hardware vertex / index buffers: yes
 * Vertex programs: yes
 * Number of floating-point constants for vertex programs: 256
 * Number of integer constants for vertex programs: 0
 * Number of boolean constants for vertex programs: 0
 * Fragment programs: yes
 * Number of floating-point constants for fragment programs: 512
 * Number of integer constants for fragment programs: 0
 * Number of boolean constants for fragment programs: 0
 * Geometry programs: no
 * Number of floating-point constants for geometry programs: 2184
 * Number of integer constants for geometry programs: 58476
 * Number of boolean constants for geometry programs: 2184
 * Supported Shader Profiles: arbfp1 arbvp1 fp20 fp30 fp40 glsl vp30 vp40
 * Texture Compression: yes
   - DXT: yes
   - VTC: yes
   - PVRTC: no
 * Scissor Rectangle: yes
 * Hardware Occlusion Query: yes
 * User clip planes: yes
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: yes
 * Floating point textures: yes
 * Non-power-of-two textures: yes
 * Volume textures: yes
 * Multiple Render Targets: 4
   - With different bit depths: yes
 * Point Sprites: yes
 * Extended point parameters: yes
 * Max Point Size: 63.375
 * Vertex texture fetch: yes
 * Number of world matrices: 0
 * Number of texture units: 16
 * Stencil buffer depth: 8
 * Number of vertex blend matrices: 0
   - Max vertex textures: 4
   - Vertex textures shared: yes
 * Render to Vertex Buffer : no
 * GL 1.5 without VBO workaround: no
 * Frame Buffer objects: yes
 * Frame Buffer objects (ARB extension): no
 * Frame Buffer objects (ATI extension): no
 * PBuffer support: yes
 * GL 1.5 without HW-occlusion workaround: no
Registering ResourceManager for type Texture
DefaultWorkQueue('Root') initialising on thread 0x885b608.
DefaultWorkQueue('Root')::WorkerFunc - thread 0x8978628 starting.
Particle Renderer Type 'billboard' registered
SceneManagerFactory for type 'OctreeSceneManager' registered.
SceneManagerFactory for type 'TerrainSceneManager' registered.
Entering DummyState...
TerrainSceneManager: Registered a new PageSource for type Heightmap
system locale is: C
setting new locale to en_US
error setting new locale
* Language successfully loaded
Loading Bootstrap
Creating resource group Bootstrap
DefaultWorkQueue('Root')::WorkerFunc - thread 0x8905330 starting.
Added resource location '/home/username/ror-trunk2/bin/resources/OgreCore.zip' of type 'Zip' to resource group 'Bootstrap'
Loading Wallpapers
Creating resource group Wallpapers
Added resource location '/home/username/ror-trunk2/bin/resources/wallpapers.zip' of type 'Zip' to resource group 'Wallpapers'
creating loading bar
Initialising resource group Bootstrap
Parsing scripts for resource group Bootstrap
Parsing script OgreCore.material
Parsing script OgreProfiler.material
Parsing script cent.fontdef
Parsing script cyberbit.fontdef
Parsing script highcontrast.fontdef
Parsing script micross.fontdef
Parsing script Ogre.fontdef
Parsing script Vera.fontdef
Parsing script OgreDebugPanel.overlay
Texture: New_Ogre_Border_Center.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Texture: New_Ogre_Border.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Texture: New_Ogre_Border_Break.png: Loading 1 faces(PF_A8R8G8B8,32x32x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,32x32x1.
Texture: ogretext.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Parsing script OgreLoadingPanel.overlay
Texture: ror-promo-02b.jpg: Loading 1 faces(PF_R8G8B8,800x392x1) with 5 generated mipmaps from Image. Internal format is PF_X8R8G8B8,800x392x1.
Finished parsing scripts for resource group Bootstrap
OverlayElementFactory for type ColoredTextArea registered.
Loading main resources
Added resource location '/home/username/ror-trunk2/bin/resources/airfoils.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/materials.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/meshes.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/overlays.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/particles.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/mygui.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/dashboards.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/scripts.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/textures.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/flags.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/icons.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/famicons.zip' of type 'Zip' to resource group 'General'
Particle Affector Type 'FireExtinguisher' registered
Particle Affector Type 'ExtinguishableFire' registered
Creating Sound Manager
SoundManager: OpenAL vendor is: OpenAL Community
SoundManager: OpenAL version is: 1.1 ALSOFT 1.13
SoundManager: OpenAL renderer is: OpenAL Soft
SoundManager: OpenAL extensions are: AL_EXT_DOUBLE AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_MULAW AL_EXT_MULAW_MCFORMATS AL_EXT_OFFSET AL_EXT_source_distance_model AL_LOKI_quadriphonic AL_SOFT_buffer_sub_data AL_SOFT_loop_points
SoundManager: OpenAL device is: SB Live! EMU10k1 Analog Stereo via PulseAudio
SoundManager: OpenAL ALC extensions are: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_disconnect ALC_EXT_EFX ALC_EXT_thread_local_context
SoundScriptManager: Sound Manager started with 32 sources
Added resource location '/home/username/ror-trunk2/bin/resources/sounds.zip' of type 'Zip' to resource group 'General'
Added resource location '/home/username/ror-trunk2/bin/resources/caelum.zip' of type 'Zip' to resource group 'General'
Loading filesystems
Creating resource group cache
Added resource location '/home/username/.rigsofrods/cache' of type 'FileSystem' to resource group 'cache'
Added resource location '/home/username/.rigsofrods/config' of type 'FileSystem' to resource group 'General'
Added resource location '/home/username/.rigsofrods/alwaysload' of type 'FileSystem' to resource group 'General'
Creating resource group Scripts
Added resource location '/home/username/.rigsofrods/scripts' of type 'FileSystem' to resource group 'Scripts'
registering Skin Manager
Registering ResourceManager for type RoRVehicleSkins
registering colored text overlay factory
OverlayElementFactory for type ColoredTextArea registered.
initialiseAllResourceGroups()
Parsing scripts for resource group Autodetect
Font CyberbitEnglishusing texture size 1024x512
Info: Freetype returned null for character 127 in font CyberbitEnglish
Info: Freetype returned null for character 128 in font CyberbitEnglish
Info: Freetype returned null for character 129 in font CyberbitEnglish
Info: Freetype returned null for character 130 in font CyberbitEnglish
Info: Freetype returned null for character 131 in font CyberbitEnglish
Info: Freetype returned null for character 132 in font CyberbitEnglish
Info: Freetype returned null for character 133 in font CyberbitEnglish
Info: Freetype returned null for character 134 in font CyberbitEnglish
Info: Freetype returned null for character 135 in font CyberbitEnglish
Info: Freetype returned null for character 136 in font CyberbitEnglish
Info: Freetype returned null for character 137 in font CyberbitEnglish
Info: Freetype returned null for character 138 in font CyberbitEnglish
Info: Freetype returned null for character 139 in font CyberbitEnglish
Info: Freetype returned null for character 140 in font CyberbitEnglish
Info: Freetype returned null for character 141 in font CyberbitEnglish
Info: Freetype returned null for character 142 in font CyberbitEnglish
Info: Freetype returned null for character 143 in font CyberbitEnglish
Info: Freetype returned null for character 144 in font CyberbitEnglish
Info: Freetype returned null for character 145 in font CyberbitEnglish
Info: Freetype returned null for character 146 in font CyberbitEnglish
Info: Freetype returned null for character 147 in font CyberbitEnglish
Info: Freetype returned null for character 148 in font CyberbitEnglish
Info: Freetype returned null for character 149 in font CyberbitEnglish
Info: Freetype returned null for character 150 in font CyberbitEnglish
Info: Freetype returned null for character 151 in font CyberbitEnglish
Info: Freetype returned null for character 152 in font CyberbitEnglish
Info: Freetype returned null for character 153 in font CyberbitEnglish
Info: Freetype returned null for character 154 in font CyberbitEnglish
Info: Freetype returned null for character 155 in font CyberbitEnglish
Info: Freetype returned null for character 156 in font CyberbitEnglish
Info: Freetype returned null for character 157 in font CyberbitEnglish
Info: Freetype returned null for character 158 in font CyberbitEnglish
Info: Freetype returned null for character 159 in font CyberbitEnglish
Info: Freetype returned null for character 160 in font CyberbitEnglish
Texture: CyberbitEnglishTexture: Loading 1 faces(PF_BYTE_LA,1024x512x1) with 0 generated mipmaps from Image. Internal format is PF_BYTE_LA,1024x512x1.
Finished parsing scripts for resource group Autodetect
Parsing scripts for resource group General
Parsing script general.program
Parsing script nicemetal.program
Parsing script DepthRender.program
Parsing script GroundFog.program
Parsing script Haze.program
Parsing script MinimalCompositorVP.program
Parsing script eurosigns.material
Parsing script ferryslip.material
Parsing script floatingdocks.material
Parsing script fresnel.material
Compiler error: object unsupported by render system in fresnel.material(20)
Parsing script general.material
Parsing script grass.material
Parsing script hangar.material
Parsing script largedocks.material
Parsing script managed.material
Parsing script marina.material
Parsing script pssm.material
Parsing script ror.material
Parsing script runway.material
Parsing script trafficlights.material
Parsing script truckshop.material
Parsing script character.material
Parsing script particles.material
Parsing script DepthComposer.material
Parsing script GroundFog.material
Parsing script LayeredClouds.material
Parsing script moon.material
Parsing script PointStarfield.material
Parsing script Precipitation.material
Parsing script SkyDome.material
Parsing script Starfield.material
Parsing script Sun.material
Parsing script dust.particle
Parsing script mud.particle
Parsing script smoke.particle
Parsing script snow.particle
Parsing script water.particle
Parsing script DepthComposer.compositor
Parsing script Precipitation.compositor
Parsing script CaelumSkies.os
Parsing script RoRSkies.os
Parsing script defaults.soundscript
SoundScriptManager: Parsing script defaults.soundscript
SoundScriptManager: creating template tracks/default_diesel
SoundScriptManager: creating template tracks/default_force
SoundScriptManager: creating template tracks/default_car
SoundScriptManager: creating template tracks/default_starter
SoundScriptManager: creating template tracks/default_turbo
SoundScriptManager: creating template tracks/default_air_purge
SoundScriptManager: creating template tracks/default_horn
SoundScriptManager: creating template tracks/default_pump
SoundScriptManager: creating template tracks/default_police
SoundScriptManager: creating template tracks/default_screetch
SoundScriptManager: creating template tracks/default_brakes
SoundScriptManager: creating template tracks/default_parkbrakes
SoundScriptManager: creating template tracks/default_air
SoundScriptManager: creating template tracks/default_shift
SoundScriptManager: creating template tracks/default_break
SoundScriptManager: creating template tracks/default_creak
Bad SoundScript attribute line: 'trigger_source    creak' in defaults.soundscript
SoundScriptManager: creating template tracks/default_gear_slide
SoundScriptManager: creating template tracks/default_marine_large
SoundScriptManager: creating template tracks/default_marine_small
SoundScriptManager: creating template tracks/default_turboprop_start1
SoundScriptManager: creating template tracks/default_turboprop_lopower1
SoundScriptManager: creating template tracks/default_turboprop_hipower1
SoundScriptManager: creating template tracks/default_turboprop_start2
SoundScriptManager: creating template tracks/default_turboprop_lopower2
SoundScriptManager: creating template tracks/default_turboprop_hipower2
SoundScriptManager: creating template tracks/default_turboprop_start3
SoundScriptManager: creating template tracks/default_turboprop_lopower3
SoundScriptManager: creating template tracks/default_turboprop_hipower3
SoundScriptManager: creating template tracks/default_turboprop_start4
SoundScriptManager: creating template tracks/default_turboprop_lopower4
SoundScriptManager: creating template tracks/default_turboprop_hipower4
SoundScriptManager: creating template tracks/default_turboprop_start5
SoundScriptManager: creating template tracks/default_turboprop_lopower5
SoundScriptManager: creating template tracks/default_turboprop_hipower5
SoundScriptManager: creating template tracks/default_turboprop_start6
SoundScriptManager: creating template tracks/default_turboprop_lopower6
SoundScriptManager: creating template tracks/default_turboprop_hipower6
SoundScriptManager: creating template tracks/default_turboprop_start7
SoundScriptManager: creating template tracks/default_turboprop_lopower7
SoundScriptManager: creating template tracks/default_turboprop_hipower7
SoundScriptManager: creating template tracks/default_turboprop_start8
SoundScriptManager: creating template tracks/default_turboprop_lopower8
SoundScriptManager: creating template tracks/default_turboprop_hipower8
SoundScriptManager: creating template tracks/default_pistonprop_start1
SoundScriptManager: creating template tracks/default_pistonprop_lopower1
SoundScriptManager: creating template tracks/default_pistonprop_hipower1
SoundScriptManager: creating template tracks/default_pistonprop_start2
SoundScriptManager: creating template tracks/default_pistonprop_lopower2
SoundScriptManager: creating template tracks/default_pistonprop_hipower2
SoundScriptManager: creating template tracks/default_pistonprop_start3
SoundScriptManager: creating template tracks/default_pistonprop_lopower3
SoundScriptManager: creating template tracks/default_pistonprop_hipower3
SoundScriptManager: creating template tracks/default_pistonprop_start4
SoundScriptManager: creating template tracks/default_pistonprop_lopower4
SoundScriptManager: creating template tracks/default_pistonprop_hipower4
SoundScriptManager: creating template tracks/default_pistonprop_lopower5
SoundScriptManager: creating template tracks/default_pistonprop_hipower5
SoundScriptManager: creating template tracks/default_pistonprop_lopower6
SoundScriptManager: creating template tracks/default_pistonprop_hipower6
SoundScriptManager: creating template tracks/default_pistonprop_lopower7
SoundScriptManager: creating template tracks/default_pistonprop_hipower7
SoundScriptManager: creating template tracks/default_pistonprop_lopower8
SoundScriptManager: creating template tracks/default_pistonprop_hipower8
SoundScriptManager: creating template tracks/default_turbojet_start1
SoundScriptManager: creating template tracks/default_turbojet_lopower1
SoundScriptManager: creating template tracks/default_turbojet_hipower1
SoundScriptManager: creating template tracks/default_turbojet_afterburner1
SoundScriptManager: creating template tracks/default_turbojet_start2
SoundScriptManager: creating template tracks/default_turbojet_lopower2
SoundScriptManager: creating template tracks/default_turbojet_hipower2
SoundScriptManager: creating template tracks/default_turbojet_afterburner2
SoundScriptManager: creating template tracks/default_turbojet_start3
SoundScriptManager: creating template tracks/default_turbojet_lopower3
SoundScriptManager: creating template tracks/default_turbojet_hipower3
SoundScriptManager: creating template tracks/default_turbojet_afterburner3
SoundScriptManager: creating template tracks/default_turbojet_start4
SoundScriptManager: creating template tracks/default_turbojet_lopower4
SoundScriptManager: creating template tracks/default_turbojet_hipower4
SoundScriptManager: creating template tracks/default_turbojet_afterburner4
SoundScriptManager: creating template tracks/default_turbojet_start5
SoundScriptManager: creating template tracks/default_turbojet_lopower5
SoundScriptManager: creating template tracks/default_turbojet_hipower5
SoundScriptManager: creating template tracks/default_turbojet_afterburner5
SoundScriptManager: creating template tracks/default_turbojet_start6
SoundScriptManager: creating template tracks/default_turbojet_lopower6
SoundScriptManager: creating template tracks/default_turbojet_hipower6
SoundScriptManager: creating template tracks/default_turbojet_afterburner6
SoundScriptManager: creating template tracks/default_turbojet_start7
SoundScriptManager: creating template tracks/default_turbojet_lopower7
SoundScriptManager: creating template tracks/default_turbojet_hipower7
SoundScriptManager: creating template tracks/default_turbojet_afterburner7
SoundScriptManager: creating template tracks/default_turbojet_start8
SoundScriptManager: creating template tracks/default_turbojet_lopower8
SoundScriptManager: creating template tracks/default_turbojet_hipower8
SoundScriptManager: creating template tracks/default_turbojet_afterburner8
SoundScriptManager: creating template tracks/default_reverse_beep
SoundScriptManager: creating template tracks/default_turn_signal
SoundScriptManager: creating template tracks/default_antilock
SoundScriptManager: creating template tracks/default_tractioncontrol
SoundScriptManager: creating template tracks/default_gpws_10
SoundScriptManager: creating template tracks/default_gpws_20
SoundScriptManager: creating template tracks/default_gpws_30
SoundScriptManager: creating template tracks/default_gpws_40
SoundScriptManager: creating template tracks/default_gpws_50
SoundScriptManager: creating template tracks/default_gpws_100
SoundScriptManager: creating template tracks/default_gpws_pullup
SoundScriptManager: creating template tracks/default_gpws_minimums
SoundScriptManager: creating template tracks/default_gpws_apdisconnect
SoundScriptManager: creating template tracks/default_aoa_warning
SoundScriptManager: creating template tracks/default_aivionic_chat01
SoundScriptManager: creating template tracks/default_aivionic_chat02
SoundScriptManager: creating template tracks/default_aivionic_chat03
SoundScriptManager: creating template tracks/default_aivionic_chat04
SoundScriptManager: creating template tracks/default_aivionic_chat05
SoundScriptManager: creating template tracks/default_aivionic_chat06
SoundScriptManager: creating template tracks/default_aivionic_chat07
SoundScriptManager: creating template tracks/default_aivionic_chat08
SoundScriptManager: creating template tracks/default_aivionic_chat09
SoundScriptManager: creating template tracks/default_aivionic_chat10
SoundScriptManager: creating template tracks/default_aivionic_chat11
SoundScriptManager: creating template tracks/default_aivionic_chat12
SoundScriptManager: creating template tracks/default_aivionic_chat13
Parsing script 3d_dashblend.overlay
Texture: dashblend.dds: Loading 1 faces(PF_DXT5,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT5,128x64x1.
Parsing script 3d_dashboard_needles.overlay
Texture: redneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Parsing script 3d_dashboard.overlay
Texture: dashboard.dds: Loading 1 faces(PF_DXT1,1024x256x1) with 10 custom mipmaps from Image. Internal format is PF_DXT1,1024x256x1.
Texture: tacho.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: speedo.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script airdashboard.overlay
Texture: dashbar.dds: Loading 1 faces(PF_DXT1,512x16x1) with 9 custom mipmaps from Image. Internal format is PF_DXT1,512x16x1.
Texture: airhelp.dds: Loading 1 faces(PF_DXT1,512x32x1) with 9 custom mipmaps from Image. Internal format is PF_DXT1,512x32x1.
Texture: airspeed.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x128x1.
Texture: altimeter.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: vvi.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture: adi-tape.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: adi.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture: adi-bugs.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture: aoa.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture: hsi.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: hsi-rose.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture: hsi-bug.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture: hsi-v.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture: hsi-h.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture: thrusttrack.dds: Loading 1 faces(PF_DXT1,32x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,32x128x1.
Texture: engfire-off.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: engstart-off.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: airrpm.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x128x1.
Texture: airpitch.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x128x1.
Texture: airtorque.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x128x1.
Texture: val-bg.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: ap-up.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: ap-dn.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: hdg-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: wlv-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: nav-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: hold-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: vs-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: athr-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: gpws-on.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: brks-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Parsing script airneedles.overlay
Texture: thrusthandle.dds: Loading 1 faces(PF_DXT1,32x32x1) with 5 custom mipmaps from Image. Internal format is PF_DXT1,32x32x1.
Texture: whiteneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Parsing script beamtiming.overlay
Parsing script boatdashboard.overlay
Texture: boatspeed.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: shipsteer_bg.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: boatdepthmeter.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script boatneedles.overlay
Texture: shipsteer.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Parsing script chat.overlay
Parsing script credits.overlay
Texture: credits.dds: Loading 1 faces(PF_DXT1,1024x512x1) with 10 custom mipmaps from Image. Internal format is PF_DXT1,1024x512x1.
Parsing script dashboard.overlay
Texture: anglo.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture: instructions.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script directionarrow.overlay
Parsing script editor.overlay
Parsing script engine.overlay
Parsing script loader.overlay
Texture: unknown.dds: Loading 1 faces(PF_DXT5,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT5,256x256x1.
Parsing script machinedashboard.overlay
Parsing script mouse.overlay
Texture: mouse.dds: Loading 1 faces(PF_DXT3,32x32x1) with 5 custom mipmaps from Image. Internal format is PF_DXT3,32x32x1.
Parsing script needlesmask.overlay
Texture: pitchmask.dds: Loading 1 faces(PF_DXT1,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x64x1.
Texture: rollmask.dds: Loading 1 faces(PF_DXT1,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x64x1.
Parsing script needles.overlay
Texture: blueneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture: pedal.dds: Loading 1 faces(PF_DXT3,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x64x1.
Texture: pbrake-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x64x1.
Texture: locked-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x64x1.
Texture: secured-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x64x1.
Texture: lopress-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x64x1.
Texture: clutch-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x64x1.
Texture: lights-off.dds: Loading 1 faces(PF_DXT5,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT5,64x64x1.
Texture: batt-off.dds: Loading 1 faces(PF_DXT5,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT5,64x64x1.
Texture: ign-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: TC_OFF.dds: Loading 1 faces(PF_A8R8G8B8,64x64x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,64x64x1.
Texture: ALB_OFF.dds: Loading 1 faces(PF_A8R8G8B8,64x64x1) with 5 generated mipmaps from Image. Internal format is PF_A8R8G8B8,64x64x1.
Parsing script truckhud.overlay
Parsing script various.overlay
Texture: pressure.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Finished parsing scripts for resource group General
Parsing scripts for resource group Internal
Finished parsing scripts for resource group Internal
Parsing scripts for resource group Scripts
Finished parsing scripts for resource group Scripts
Parsing scripts for resource group Wallpapers
Finished parsing scripts for resource group Wallpapers
Parsing scripts for resource group cache
Finished parsing scripts for resource group cache
Creating resource group Packs
Added resource location '/home/username/ror-trunk2/bin/packs' of type 'FileSystem' to resource group 'Packs' with recursive option
Added resource location '/home/username/.rigsofrods/packs' of type 'FileSystem' to resource group 'Packs' with recursive option
Added resource location '/home/username/.rigsofrods/mods' of type 'FileSystem' to resource group 'Packs' with recursive option
Creating resource group VehicleFolders
Added resource location '/home/username/.rigsofrods/vehicles' of type 'FileSystem' to resource group 'VehicleFolders'
Creating resource group TerrainFolders
Added resource location '/home/username/.rigsofrods/terrains' of type 'FileSystem' to resource group 'TerrainFolders'
initialiseResourceGroups: VehicleFolders
Initialising resource group VehicleFolders
Parsing scripts for resource group VehicleFolders
Finished parsing scripts for resource group VehicleFolders
initialiseResourceGroups: TerrainFolders
Initialising resource group TerrainFolders
Parsing scripts for resource group TerrainFolders
Finished parsing scripts for resource group TerrainFolders
initialiseAllResourceGroups() - Content
Initialising resource group Packs
Parsing scripts for resource group Packs
Finished parsing scripts for resource group Packs
Rigs of Rods main loop starting ...
Leaving DummyState...
Entering GameState...
TerrainSceneManager: Registered a new PageSource for type Heightmap
Creating camera
Adding Frame Listener
* Initialise: RenderManager
./RoR: symbol lookup error: ./RoR: undefined symbol: _ZN5MyGUI13RenderManager12onResizeViewERKNS_5types5TSizeIiEE
username@ubuntu01:~/ror-trunk2/bin$ 

```help.. not that error..:frown:```

./RoR: symbol lookup error: ./RoR: undefined symbol: _ZN5MyGUI13RenderManager12onResizeViewERKNS_5types5TSizeIiEE
```
i got that exact same error with stunt rally.. [URL="http://ubuntuforums.org/showthread.php?t=1986879"]http://ubuntuforums.org/showthread.php?t=1986879
[/URL] thanks very much if you can solve this

---

### Post by fallenshadow on 2012-07-17
Congrats on getting so far with this! :KS 

I don't know what that error means exactly but make sure you have all the required libs to run it.

---

### Post by gandalf3 on 2012-07-17
is there a list somewhere of all the required libs? (in know theres kinda one on the compilation instructions wiki, but you said that was incomplete and i think i have all those anyway)
i didn't see any errors asking for more libs in the output either..:confused:

---

### Post by fallenshadow on 2012-07-18
If you have all of those you should be good to go. Remember Lua is not required for new versions of Rigs of Rods so you don't need that.

If you have that issue with other games then it must be a deeper issue and not a problem with the game.

Did you custom (compile+) install libOgre or install from the software center?

Also if you are using Ubuntu 11.10 you may not be able to run it since I compiled on Ubuntu 12.04 with possibly newer libs than the ones you have.

---

### Post by gandalf3 on 2012-07-18
i compiled libogremain, (i think. if it's on that list in the wiki with instructions i definitely did) though i  followed these[ instructions]("http://www.rigsofrods.com/threads/91025-How-to-Build-RoR-on-Ubuntu-11-10") first, waited a while for it to update, then i found the wiki page, continued where i left off, fail on the cmake command, deleted everything i could find related to my attempts, tried again and failed again, though i didn't delete it all this time so i still have it.
the just recently found out i compiled the wrong version, and installed the right version via a .deb file.
i think i may have compiled Lua anyway, would that cause problems?
i think it is a problem that gas something to do with ogre, partly because the error message say so :P,
but also the other game i get the same error on (stunt rally) also uses ogre, how ever this game used to work, maybe i did some thing that knocked something else out of whack? possibly when i was trying to compile RoR and RoR deps?

EDIT:

also all my previous attempts were to compile RoR 0.38 not 0.4, does make a difference?

---

### Post by fallenshadow on 2012-07-18
Ah I think thats where the problem is... the trick is to custom compile as little as possible. I installed most required libraries from the Ubuntu Software Center. (including ogre lib)

Newer versions of Rigs of Rods don't use Lua so you don't need it. Although if you did install it I don't think it would cause problems.

I followed this guide:
[http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries](http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries)

However the **only** libs I custom compiled:
[b]
- MyGUI

- Paged Geometry 

- Caelum

- AngelScript
[/b]
Everything else I installed from the Ubuntu Software Center. :)

---

### Post by gandalf3 on 2012-07-19
okay.. so what should i do? delete all my RoR trunk, dep, etc. folders and start again?
will that get rid of whatever flawed libs i have compiled?
or do in need to hunt around in some other spot like usr/lib/ or something to get them all?
thanks

---

### Post by gandalf3 on 2012-08-12
well i fresh-installed 12.04, so that got rid of anything that i don't want.
so i'm going to try compiling fresh.
i did go to 64bit though, will that cause problems?
i found some older stuff, might help, probably won't,
[apt.**rigsofrods**.com/dists/lucid/main/binary-amd64/]("http://ubuntuforums.org/apt.rigsofrods.com/dists/lucid/main/binary-amd64/")
and
[http://www.rigsofrods.com/repository/view/401](http://www.rigsofrods.com/repository/view/401)

---

### Post by gandalf3 on 2012-09-05
all was going smoothly until i get to MyGui (the first one i have to compile)

```
 user@Ubuntu01:~/ror-deps/my-gui$ cmake -DCMAKE_BUILD_TYPE:STRING=Release -DMYGUI_BUILD_SAMPLES:BOOL=OFF -DMYGUI_INSTALL_SAMPLES:BOOL=OFF -DMYGUI_BUILD_TOOLS:BOOL=OFF -DMYGUI_BUILD_PLUGINS:BOOL=OFF .
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring MYGUI 3.2.0
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- Looking for FREETYPE...
-- checking for module 'freetype2'
--   package 'freetype2' not found
-- CMAKE_PREFIX_PATH: Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/usr/local
-- Could not locate FREETYPE
-- checking for one of the modules 'OGRE'
-- Looking for OIS...
-- OIS_PREFIX_PATH changed.
-- checking for module 'OIS'
--   package 'OIS' not found
-- Could not locate OIS
-- Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE) 
CMake Error at CMake/Utils/MacroLogFeature.cmake:91 (MESSAGE):
  

  
  -----------------------------------------------------------------------------


  -- The following REQUIRED packages could NOT be located on your system.

  -- Please install them before continuing this software installation.

  -- If you are in Windows, try passing -DMYGUI_DEPENDENCIES_DIR=<path to
  dependencies>

  -- Also check that you buildind with RenderSystem that you need or set
  another with -DMYGUI_RENDERSYSTEM=<1 2 or 3 for Direct3D_9 OGRE or OpenGL>

  
  -----------------------------------------------------------------------------


  + freetype: Portable font engine <http://www.freetype.org>

  + ogre: Support for the Ogre render system <>

  
  -----------------------------------------------------------------------------
Call Stack (most recent call first):
  CMake/Dependencies.cmake:108 (MACRO_DISPLAY_FEATURE_LOG)
  CMakeLists.txt:232 (include)


-- Configuring incomplete, errors occurred! 
```
the thing is, i did sudo apt-get install libogremain1.7-1.7.2 before doing this, so ogre should be there, and it says freetype is installed in the software center.. :confused:

---

### Post by fallenshadow on 2012-09-09
When compiling stuff you must install the "-dev" package of that thing you need.

So for freetype you would need:

> libfreetype6-dev

For OIS you would need:

> libois-dev

So install as much as possible from the Software Center. Then just custom compile the 4 required things I mentioned before. In order to custom compile those you may need these things from the Software Center. Just install them as required.

---

### Post by gandalf3 on 2012-09-10
thanks. installed the -dev packages, but now something seems to be wrong with cmake:

```
user@Ubuntu01:~/ror-deps/my-gui$ cmake -DCMAKE_BUILD_TYPE:STRING=Release -DMYGUI_BUILD_SAMPLES:BOOL=OFF -DMYGUI_INSTALL_SAMPLES:BOOL=OFF -DMYGUI_BUILD_TOOLS:BOOL=OFF -DMYGUI_BUILD_PLUGINS:BOOL=OFF .
-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring MYGUI 3.2.0
-- Looking for FREETYPE...
-- checking for module 'freetype2'
--   found freetype2, version 14.0.8
-- CMAKE_PREFIX_PATH: Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/usr/local
-- Found FREETYPE: /usr/lib/x86_64-linux-gnu/libfreetype.so
-- checking for one of the modules 'OGRE'
--   libraries : OgreMain;pthread from /usr/lib/x86_64-linux-gnu
--   includes  : /usr/include/OGRE
-- Looking for OIS...
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Found OIS: /usr/lib/libOIS.so
-- Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE) 
-- 
-----------------------------------------------------------------------------
-- The following external packages were located on your system.
-- This installation will have the extra features provided by these packages.
+ freetype
+ ogre
+ OIS
-----------------------------------------------------------------------------
-- The following OPTIONAL packages could NOT be located on your system.
-- Consider installing them to enable more features from this software.
+ Doxygen: Tool for building API documentation <http://doxygen.org>
-----------------------------------------------------------------------------

CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- /home/user/ror-deps/my-guiProjectRevision
-- Using svn revision 4344.
-- Configuring incomplete, errors occurred!
user@Ubuntu01:~/ror-deps/my-gui$ make -j2
make: *** No targets specified and no makefile found.  Stop.
user@Ubuntu01:~/ror-deps/my-gui$ sudo make install
[sudo] password for user: 
user@Ubuntu01:~/ror-deps/my-gui$ 

```

---

### Post by fallenshadow on 2012-09-11
Cmake is simply telling you that a CXX compiler was not found. CXX actually stands for C++ the programming language.

To fix this install: g++ and try to compile again! :)

---

### Post by gandalf3 on 2012-09-11
Thanks! now something else went wrong.. missing files?

```
user@Ubuntu01:~/ror-deps/my-gui$ cmake -DCMAKE_BUILD_TYPE:STRING=Release -DMYGUI_BUILD_SAMPLES:BOOL=OFF -DMYGUI_INSTALL_SAMPLES:BOOL=OFF -DMYGUI_BUILD_TOOLS:BOOL=OFF -DMYGUI_BUILD_PLUGINS:BOOL=OFF .
-- The CXX compiler identification is GNU
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Configuring MYGUI 3.2.0
-- Performing Test MYGUI_GCC_VISIBILITY
-- Performing Test MYGUI_GCC_VISIBILITY - Success
-- Detected g++ 4.6

-- Enabling GCC visibility flags
-- Looking for FREETYPE...
-- CMAKE_PREFIX_PATH: Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/home/user/ror-deps/my-gui/../Dependencies;/usr/local
-- Found FREETYPE: /usr/lib/x86_64-linux-gnu/libfreetype.so
-- Looking for OIS...
-- Found OIS: /usr/lib/libOIS.so
-- Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE) 
-- 
-----------------------------------------------------------------------------
-- The following external packages were located on your system.
-- This installation will have the extra features provided by these packages.
+ freetype
+ ogre
+ OIS
-----------------------------------------------------------------------------
-- The following OPTIONAL packages could NOT be located on your system.
-- Consider installing them to enable more features from this software.
+ Doxygen: Tool for building API documentation <http://doxygen.org>
-----------------------------------------------------------------------------

-- /home/user/ror-deps/my-guiProjectRevision
-- Using svn revision 4344.
-- Configuring done
-- Generating done
CMake Warning:
  Manually-specified variables were not used by the project:

    MYGUI_BUILD_SAMPLES


-- Build files have been written to: /home/user/ror-deps/my-gui
user@Ubuntu01:~/ror-deps/my-gui$ make -j2
Scanning dependencies of target MyGUIEngine
[  1%] [  1%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Button.cpp.o
Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Canvas.cpp.o
[  2%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ComboBox.cpp.o
[  3%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DDContainer.cpp.o
[  4%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_EditBox.cpp.o
[  4%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ImageBox.cpp.o
[  5%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ItemBox.cpp.o
[  6%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ListBox.cpp.o
[  6%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MenuBar.cpp.o
[  7%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MenuControl.cpp.o
[  8%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MenuItem.cpp.o
[  9%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MultiListBox.cpp.o
[  9%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_PopupMenu.cpp.o
[ 10%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ProgressBar.cpp.o
[ 11%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ScrollBar.cpp.o
[ 12%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ScrollView.cpp.o
[ 12%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TextBox.cpp.o
[ 13%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TabControl.cpp.o
[ 14%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TabItem.cpp.o
[ 14%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MultiListItem.cpp.o
[ 15%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Widget.cpp.o
[ 16%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Window.cpp.o
[ 17%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_EditText.cpp.o
[ 17%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MainSkin.cpp.o
[ 18%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_PolygonalSkin.cpp.o
[ 19%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_RotatingSkin.cpp.o
[ 20%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SimpleText.cpp.o
[ 20%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SubSkin.cpp.o
[ 21%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TileRect.cpp.o
[ 22%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LayerItem.cpp.o
[ 23%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LayerNode.cpp.o
[ 23%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_OverlappedLayer.cpp.o
[ 24%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_RenderItem.cpp.o
[ 25%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SharedLayer.cpp.o
[ 25%] [ 26%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SharedLayerNode.cpp.o
Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SkinItem.cpp.o
[ 27%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ActionController.cpp.o
[ 28%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ControllerEdgeHide.cpp.o
[ 28%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ControllerFadeAlpha.cpp.o
[ 29%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ControllerPosition.cpp.o
[ 30%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_BackwardCompatibility.cpp.o
[ 31%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Exception.cpp.o
[ 31%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Precompiled.cpp.o
[ 32%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_BiIndexBase.cpp.o
[ 33%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ScrollViewBase.cpp.o
[ 33%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_WidgetInput.cpp.o
[ 34%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_WidgetUserData.cpp.o
[ 35%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceImageSet.cpp.o
[ 36%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceImageSetPointer.cpp.o
[ 36%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceLayout.cpp.o
[ 37%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceManualFont.cpp.o
[ 38%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceManualPointer.cpp.o
[ 39%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceSkin.cpp.o
[ 39%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceTrueTypeFont.cpp.o
[ 40%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ChildSkinInfo.cpp.o
[ 41%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_MaskPickInfo.cpp.o
[ 41%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SubWidgetBinding.cpp.o
[ 42%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Any.cpp.o
[ 43%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Colour.cpp.o
[ 44%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ClipboardManager.cpp.o
[ 44%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ControllerManager.cpp.o
[ 45%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DataManager.cpp.o
[ 46%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DynLibManager.cpp.o
[ 47%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_FactoryManager.cpp.o
[ 47%] [ 48%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_FontManager.cpp.o
Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Gui.cpp.o
[ 49%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_InputManager.cpp.o
[ 50%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LanguageManager.cpp.o
[ 50%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LayerManager.cpp.o
[ 51%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LayoutManager.cpp.o
[ 52%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_PluginManager.cpp.o
[ 52%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_PointerManager.cpp.o
[ 53%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_RenderManager.cpp.o
[ 54%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ResourceManager.cpp.o
[ 55%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SkinManager.cpp.o
[ 55%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_SubWidgetManager.cpp.o
[ 56%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ToolTipManager.cpp.o
[ 57%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_WidgetManager.cpp.o
[ 58%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Constants.cpp.o
[ 58%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DataFileStream.cpp.o
[ 59%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DataStream.cpp.o
[ 60%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_DynLib.cpp.o
[ 60%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_GeometryUtility.cpp.o
[ 61%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TextIterator.cpp.o
[ 62%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TextureUtility.cpp.o
[ 63%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_TextView.cpp.o
[ 63%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_Timer.cpp.o
[ 64%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_UString.cpp.o
[ 65%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_XmlDocument.cpp.o
[ 66%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_ConsoleLogListener.cpp.o
[ 66%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_FileLogListener.cpp.o
[ 67%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LevelLogFilter.cpp.o
[ 68%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LogManager.cpp.o
[ 69%] Building CXX object MyGUIEngine/CMakeFiles/MyGUIEngine.dir/src/MyGUI_LogSource.cpp.o
Linking CXX shared library ../lib/libMyGUIEngine.so
[ 69%] Built target MyGUIEngine
Scanning dependencies of target MyGUI.OgrePlatform
[ 69%] [ 70%] Building CXX object Platforms/Ogre/OgrePlatform/CMakeFiles/MyGUI.OgrePlatform.dir/src/MyGUI_OgreDataManager.cpp.o
Building CXX object Platforms/Ogre/OgrePlatform/CMakeFiles/MyGUI.OgrePlatform.dir/src/MyGUI_OgreDataStream.cpp.o
In file included from /home/user/ror-deps/my-gui/Platforms/Ogre/OgrePlatform/src/MyGUI_OgreDataManager.cpp:9:0:
/home/user/ror-deps/my-gui/Platforms/Ogre/OgrePlatform/include/MyGUI_OgreDataStream.h:13:28: fatal error: OgreDataStream.h: No such file or directory
compilation terminated.
In file included from /home/user/ror-deps/my-gui/Platforms/Ogre/OgrePlatform/src/MyGUI_OgreDataStream.cpp:7:0:
/home/user/ror-deps/my-gui/Platforms/Ogre/OgrePlatform/include/MyGUI_OgreDataStream.h:13:28: fatal error: OgreDataStream.h: No such file or directory
compilation terminated.
make[2]: *** [Platforms/Ogre/OgrePlatform/CMakeFiles/MyGUI.OgrePlatform.dir/src/MyGUI_OgreDataManager.cpp.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [Platforms/Ogre/OgrePlatform/CMakeFiles/MyGUI.OgrePlatform.dir/src/MyGUI_OgreDataStream.cpp.o] Error 1
make[1]: *** [Platforms/Ogre/OgrePlatform/CMakeFiles/MyGUI.OgrePlatform.dir/all] Error 2
make: *** [all] Error 2

```

---

### Post by fallenshadow on 2012-09-12
Well it failed when it got to the ogre stuff.

Do you have "libogre-dev" installed?

---

### Post by gandalf3 on 2012-09-12
Yes, it say it's installed in the software center.
i think there was some error while i was installing it though.. (i don't think it was related, something about Java not installing because it couldn't connect, but I'll try reinstalling anyway just in case that messed something up with ogre)

EDIT:
yes, it worked, (i also deleted the "my-gui" directory and re-fetched it)
onto the next thing! :D

EDIT 2:
successfully compiled paged geometry! :D there were a few warnings about "set but unused variables" though.. what does that mean?

EDIT 3:
successfully compiled Caelum! :D some more warnings though "set but unused variables" also the instructions on the wiki say to copy /usr/local/lib/libCaelum.so to /usr/local/lib/OGRE/, but there is no "OGRE" directory there, probably because i installed with "sudo apt-get install libogre-dev" is there some other place i have to copy it?

EDIT 4: 
how did you install MysocketW? i can't find it in the software center :confused:

---

### Post by fallenshadow on 2012-09-12
Thats some nice progress! :) An unused variable is just a variable not being used in the code anywhere. Think of it like an apple in your lunchbox that you didn't eat! :D (it doesn't matter)

For mysocketW you need to install:

> libssl-dev

Its in the software center! :)

---

### Post by gandalf3 on 2012-09-12
installed libssl-dev, do i still have to do
> wget [http://www.digitalfanatics.org/cal/socketw/files/SocketW031026.tar.gz](http://www.digitalfanatics.org/cal/socketw/files/SocketW031026.tar.gz) -O SocketW031026.tar.gz tar xzf SocketW031026.tar.gz cd SocketW031026/ wget [http://wiki.rigsofrods.com/images/c/c0/Socketw.patch](http://wiki.rigsofrods.com/images/c/c0/Socketw.patch) -O Socketw.patch patch -p0 -d src < Socketw.patch rm Socketw.patch make -j2 --silent shared sudo make install cd ..?
or am i done with mysocketw (i searched for "socketw" in the software center, it's not there)

---

### Post by fallenshadow on 2012-09-13
libssl gives you mysocketw support.

I found it on this page:

[http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries](http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries)

So that bit is done! :)

---

### Post by gandalf3 on 2012-09-13
:) successfully compiled angelscript
and installed openall
but i wasn&#8217;t sure what version/thing i wanted for wxwidgets. (there's a lot of things that come up when you search in the software centre)
and nothing comes up for hydrax.. :confused: where do you get that?

---

### Post by fallenshadow on 2012-09-14
The wxwidgets you should install is:

> libwxgtk2.8-dev

2.8 is the latest stable version.

I think for Hydrax I did the instructions here:

[http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries](http://www.rigsofrods.com/wiki/pages/Compiling_3rd_party_libraries)

---

### Post by gandalf3 on 2012-09-14
i successfully installed wxwidgets2.8-dev,

and i think i successfully compiled hydrax. (no errors, and no "successfully compiled" messages)

and since i just did the "compiling dependencies" page, do i still have to do all this

```

sudo apt-get install automake subversion cmake build-essential libfreetype6-dev libzzip-dev nvidia-cg-toolkit \  libwxgtk2.8-dev libfreeimage-dev libgl1-mesa-dev libxrandr-dev libx11-dev libxt-dev libxaw7-dev \  libglu1-mesa-dev libxxf86vm-dev libboost-dev pkg-config uuid-dev libuuid1 libgtk2.0-dev liblua5.1-0-dev \  libopenal-dev scons cmake-qt-gui libboost-all-dev libcurl4-openssl-dev doxygen mercurial 
```
? (from here)
[http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux](http://www.rigsofrods.com/wiki/pages/Compiling_Sources_under_Linux)

---

### Post by fallenshadow on 2012-09-14
Try it and see if you are missing anything. If you are missing anything from this,  just install them.

Then proceed to compiling Rigs of Rods.

---

### Post by gandalf3 on 2012-09-14
it was missing 850 MB of stuff...
i assume that using the CLI cmake as recommended and running this
```

cmake -DROR_USE_MYGUI="TRUE" \ -DROR_USE_OPENAL="TRUE" \ -DROR_USE_LUA="TRUE" \ -DROR_USE_SOCKETW="TRUE" \ -DROR_USE_MOFILEREADER="TRUE" \ -DROR_USE_PAGED="TRUE" \ -DROR_USE_CAELUM="TRUE" \ -DROR_USE_ANGELSCRIPT="TRUE" . 
```will do it?

EDIT:

i did it, but it didn&#8217;t do it..
i checked out the trunk
and ran:

```
user@Ubuntu01:~$ cd ~/ror-codehg/
user@Ubuntu01:~/ror-codehg$ cmake -DROR_USE_MYGUI="TRUE" \
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.10
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.26.1
-- checking for module 'OGRE'
--   found OGRE, version 1.7.4
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.7.4
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.7.4
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.7.4
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Found CURL: /usr/lib/x86_64-linux-gnu/libcurl.so 
-- Found OpenAL: /usr/lib/x86_64-linux-gnu/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:          YES
-- MYGUI_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS:     /usr/local/lib
-- MYGUI_LIBRARIES:        MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:          YES
-- OPENAL_INCLUDE_DIRS:     /usr/include/AL
-- OPENAL_LIBRARY_DIRS:     
-- OPENAL_LIBRARIES:        /usr/lib/x86_64-linux-gnu/libopenal.so
-- CURL Enabled:          YES
-- CURL_INCLUDE_DIRS:     /usr/include
-- CURL_LIBRARY_DIRS:     
-- CURL_LIBRARIES:        /usr/lib/x86_64-linux-gnu/libcurl.so
-- SOCKETW Enabled:          NO
-- PAGED Enabled:          YES
-- PAGED_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/PagedGeometry
-- PAGED_LIBRARY_DIRS:     
-- PAGED_LIBRARIES:        /usr/local/lib/libPagedGeometry.a
-- CAELUM Enabled:          YES
-- CAELUM_INCLUDE_DIRS:     /usr/local/include/Caelum
-- CAELUM_LIBRARY_DIRS:     
-- CAELUM_LIBRARIES:        /usr/local/lib/libCaelum.so
-- ANGELSCRIPT Enabled:          YES
-- ANGELSCRIPT_INCLUDE_DIRS:     /usr/local/include;/home/user/ror-codehg/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS:     
-- ANGELSCRIPT_LIBRARIES:        /usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
-- Configuring done
-- Generating done
CMake Warning:
  Manually-specified variables were not used by the project:

    ROR_USE_LUA
    ROR_USE_MOFILEREADER


-- Build files have been written to: /home/user/ror-codehg
user@Ubuntu01:~/ror-codehg$ make -j2
Scanning dependencies of target RoRConfig
Scanning dependencies of target angelscript_addons
[  0%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptfile/scriptfile.cpp.o
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/contextmgr/contextmgr.cpp.o
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/serializer/serializer.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmath.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmathcomplex.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath3d/scriptmath3d.cpp.o
[  3%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/Configurator.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/autowrapper/generator/generateheader.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptdictionary/scriptdictionary.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthelper/scripthelper.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/debugger/debugger.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthandle/scripthandle.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptany/scriptany.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring_utils.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptbuilder/scriptbuilder.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring.cpp.o
[  9%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring_utils.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptarray/scriptarray.cpp.o
Linking CXX static library ../../bin/libangelscript_addons.a
[ 10%] Built target angelscript_addons
Scanning dependencies of target RoR
[ 10%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundScriptManager.cpp.o
[ 11%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/statpict.cpp.o
[ 11%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/Settings.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/Sound.cpp.o
[ 13%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/SHA1.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundManager.cpp.o
[ 13%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/ErrorUtils.cpp.o
[ 14%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/Utils.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/AutoPilot.cpp.o
Linking CXX executable ../../bin/RoRConfig
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/BeamEngine.cpp.o
[ 15%] Built target RoRConfig
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PlayerColours.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Skin.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/MaterialReplacer.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/SkinManager.cpp.o
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp: In member function &#8216;virtual void ChatSystem::receiveStreamData(unsigned int&, int&, unsigned int&, char*, unsigned int&)&#8217;:
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp:176:42: error: invalid use of incomplete type &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/GlobalEnvironment.h:28:7: error: forward declaration of &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp:179:33: error: invalid use of incomplete type &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/GlobalEnvironment.h:28:7: error: forward declaration of &#8216;struct Network&#8217;
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Replay.cpp.o
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2
user@Ubuntu01:~/ror-codehg$ 

``` :confused:

---

### Post by gandalf3 on 2012-10-05
i tried the whole thing over again in case forgot sudo somewhere or something.. but this time it failed here:

```
user@Ubuntu01:~/ror-codehg$ cmake -DROR_USE_MYGUI="TRUE" \
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.10
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.26.1
-- checking for module 'OGRE'
--   found OGRE, version 1.7.4
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.7.4
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.7.4
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.7.4
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Could NOT find CURL (missing:  CURL_LIBRARY CURL_INCLUDE_DIR) 
-- Found OpenAL: /usr/lib/x86_64-linux-gnu/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:          YES
-- MYGUI_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS:     /usr/local/lib
-- MYGUI_LIBRARIES:        MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:          YES
-- OPENAL_INCLUDE_DIRS:     /usr/include/AL
-- OPENAL_LIBRARY_DIRS:     
-- OPENAL_LIBRARIES:        /usr/lib/x86_64-linux-gnu/libopenal.so
-- CURL Enabled:          NO
-- SOCKETW Enabled:          NO
-- PAGED Enabled:          YES
-- PAGED_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/PagedGeometry
-- PAGED_LIBRARY_DIRS:     
-- PAGED_LIBRARIES:        /usr/local/lib/libPagedGeometry.a
-- CAELUM Enabled:          YES
-- CAELUM_INCLUDE_DIRS:     /usr/local/include/Caelum
-- CAELUM_LIBRARY_DIRS:     
-- CAELUM_LIBRARIES:        /usr/local/lib/libCaelum.so
-- ANGELSCRIPT Enabled:          YES
-- ANGELSCRIPT_INCLUDE_DIRS:     /usr/local/include;/home/user/ror-codehg/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS:     
-- ANGELSCRIPT_LIBRARIES:        /usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
-- Configuring done
-- Generating done
CMake Warning:
  Manually-specified variables were not used by the project:

    ROR_USE_LUA
    ROR_USE_MOFILEREADER


-- Build files have been written to: /home/user/ror-codehg
user@Ubuntu01:~/ror-codehg$ 
user@Ubuntu01:~/ror-codehg$ make
Scanning dependencies of target angelscript_addons
[  0%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptfile/scriptfile.cpp.o
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/contextmgr/contextmgr.cpp.o
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/serializer/serializer.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmath.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmathcomplex.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath3d/scriptmath3d.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/autowrapper/generator/generateheader.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptdictionary/scriptdictionary.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthelper/scripthelper.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/debugger/debugger.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthandle/scripthandle.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptany/scriptany.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring_utils.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptbuilder/scriptbuilder.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring.cpp.o
[  9%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring_utils.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptarray/scriptarray.cpp.o
Linking CXX static library ../../bin/libangelscript_addons.a
[ 10%] Built target angelscript_addons
Scanning dependencies of target RoR
[ 10%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundScriptManager.cpp.o
[ 11%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/Sound.cpp.o
[ 11%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundManager.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/AutoPilot.cpp.o
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/BeamEngine.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PlayerColours.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Skin.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/MaterialReplacer.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp: In member function &#8216;virtual void ChatSystem::receiveStreamData(unsigned int&, int&, unsigned int&, char*, unsigned int&)&#8217;:
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp:176:42: error: invalid use of incomplete type &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/GlobalEnvironment.h:28:7: error: forward declaration of &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/gameplay/ChatSystem.cpp:179:33: error: invalid use of incomplete type &#8216;struct Network&#8217;
/home/user/ror-codehg/source/main/GlobalEnvironment.h:28:7: error: forward declaration of &#8216;struct Network&#8217;
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o] Error 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Error 2
make: *** [all] Error 2

```:( what is failing??

EDIT:

are you sure libssl-dev gives you my socketw support?

```
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.10
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.26.1
-- checking for module 'OGRE'
--   found OGRE, version 1.7.4
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.7.4
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.7.4
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.7.4
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Could NOT find CURL (missing:  CURL_LIBRARY CURL_INCLUDE_DIR) 
-- Found OpenAL: /usr/lib/x86_64-linux-gnu/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:          YES
-- MYGUI_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS:     /usr/local/lib
-- MYGUI_LIBRARIES:        MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:          YES
-- OPENAL_INCLUDE_DIRS:     /usr/include/AL
-- OPENAL_LIBRARY_DIRS:     
-- OPENAL_LIBRARIES:        /usr/lib/x86_64-linux-gnu/libopenal.so
-- CURL Enabled:          NO
-- SOCKETW Enabled:          NO
-- PAGED Enabled:          YES
-- PAGED_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/PagedGeometry
-- PAGED_LIBRARY_DIRS:     
-- PAGED_LIBRARIES:        /usr/local/lib/libPagedGeometry.a
-- CAELUM Enabled:          YES
-- CAELUM_INCLUDE_DIRS:     /usr/local/include/Caelum
-- CAELUM_LIBRARY_DIRS:     
-- CAELUM_LIBRARIES:        /usr/local/lib/libCaelum.so
-- ANGELSCRIPT Enabled:          YES
-- ANGELSCRIPT_INCLUDE_DIRS:     /usr/local/include;/home/user/ror-codehg/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS:     
-- ANGELSCRIPT_LIBRARIES:        /usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
```> -- SOCKETW Enabled:          NOlibssl-dev installed..

> **  MySocketW **

 NOTE: You have to install the OpenSSL development package before you compile. In Ubuntu and Debian run sudo apt-get install libssl-dev
, in CentOS run yum install libssl-dev
. This needs another patch [Media:Socketw.patch]("http://www.rigsofrods.com/wiki/images/c/c0/Socketw.patch") to fix socketw for newer compilers 
 wget [http://www.digitalfanatics.org/cal/socketw/files/SocketW031026.tar.gz](http://www.digitalfanatics.org/cal/socketw/files/SocketW031026.tar.gz) -O SocketW031026.tar.gz tar xzf SocketW031026.tar.gz cd SocketW031026/ wget [http://wiki.rigsofrods.com/images/c/c0/Socketw.patch](http://wiki.rigsofrods.com/images/c/c0/Socketw.patch) -O Socketw.patch patch -p0 -d src < Socketw.patch rm Socketw.patch make -j2 --silent shared sudo make install cd ..
 since there is no uninstall script run this to remove SocketW 
 sudo rm /usr/local/lib/libSocketW* sudo rm /usr/local/include/SocketW.h sudo rm /usr/local/include/sw_*.h
maybe they mean you have to install openssl AND compile mysocketw?

hmm..

going to try that..

EDIT 2:

> [100%] Built target RoRConfig
[ 97%] Built target RoRbut when i run rorconfig, i get a dialogue box saying:

Unable to load the render systems. Please check if all required files are there and the plugins.cfg file is correct.
This is a fatal error and the game will not start.

in plugins.cfg, it says:
> # Defines plugins to load

# Define plugin folder
PluginFolder=/usr/local/lib/OGRE/

# Define plugins
Plugin=RenderSystem_Direct3D9
Plugin=RenderSystem_GL
Plugin=Plugin_ParticleFX
Plugin=Plugin_OctreeSceneManager
Plugin=Plugin_CgProgramManager
Plugin=libCaelum.so


however, there IS no OGRE directory in /usr/share/local/
should i create it?
:confused:

---

### Post by gandalf3 on 2012-10-08
i found the OGRE folder lurking in /usr/include
pasted into /usr/local/
still missing a few *.so files.. (including opengl)
found the rest in /usr/lib/x86_64-linux-gnu/OGRE-1.7.4
it starts! ..then crashes :(

im attaching my ror.log,
but all i found was some streaming error called error7
:confused:

---

### Post by emgiezet on 2012-10-10
> **gandalf3 said:**
> i found the OGRE folder lurking in /usr/include
pasted into /usr/local/
still missing a few *.so files.. (including opengl)
found the rest in /usr/lib/x86_64-linux-gnu/OGRE-1.7.4
it starts! ..then crashes :(

im attaching my ror.log,
but all i found was some streaming error called error7
:confused:

I got same situation like yours.
Mine RoR compilation don't runs but crashes when trying to connect the server.

Look at mine thread on RoR forum:
[http://www.rigsofrods.com/threads/97476-Ubuntu-12-04-64bit-crash-on-game-start?p=1086915](http://www.rigsofrods.com/threads/97476-Ubuntu-12-04-64bit-crash-on-game-start?p=1086915)

---

### Post by gandalf3 on 2012-10-10
mine works fine until i try to load the "simple test terrain" (only option)
then it crashes.. :(
the terminal out puts this:

```
user@Ubuntu01:~$ cd ~/ror-codehg/
user@Ubuntu01:~/ror-codehg$ cd ./bin/
user@Ubuntu01:~/ror-codehg/bin$ ./RoR
 * log path:         /home/user/.rigsofrods/logs/
 * config path:      /home/user/.rigsofrods/config/
 * user path:        /home/user/.rigsofrods/
 * program path:     /home/user/ror-codehg/bin/
 * used plugins.cfg: /home/user/ror-codehg/bin/plugins.cfg
 * used ogre.cfg:    /home/user/.rigsofrods/config/ogre.cfg
 * used ogre.log:    /home/user/.rigsofrods/logs/RoR.log
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
DDS codec registering
FreeImage version: 3.15.1
This  program uses FreeImage, a free, open source image library supporting  all common bitmap formats. See http://freeimage.sourceforge.net for  details
Supported formats:  bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi,exr,j2k,j2c,jp2,pfm,pct,pict,pic,3fr,arw,bay,bmq,cap,cine,cr2,crw,cs1,dc2,dcr,drf,dsc,dng,erf,fff,ia,iiq,k25,kc2,kdc,mdc,mef,mos,mrw,nef,nrw,orf,pef,ptx,pxn,qtk,raf,raw,rdc,rw2,rwl,rwz,sr2,srf,sti
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
*-*-* OGRE Initialising
*-*-* Version 1.7.4 (Cthugha)
Loading library /usr/local/lib/OGRE/RenderSystem_Direct3D9
failed  to load plugin: /usr/local/lib/OGRE/RenderSystem_Direct3D9: OGRE  EXCEPTION(7:InternalErrorException): Could not load dynamic library  /usr/local/lib/OGRE/RenderSystem_Direct3D9.  System Error:  /usr/local/lib/OGRE/RenderSystem_Direct3D9.so: cannot open shared object  file: No such file or directory in DynLib::load at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDynLib.cpp (line 91)
Loading library /usr/local/lib/OGRE/RenderSystem_GL
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_ParticleFX
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_OctreeSceneManager
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager
failed  to load plugin: /usr/local/lib/OGRE/Plugin_CgProgramManager: OGRE  EXCEPTION(7:InternalErrorException): Could not load dynamic library  /usr/local/lib/OGRE/Plugin_CgProgramManager.  System Error:  libOgreMain-1.6.4.so: cannot open shared object file: No such file or  directory in DynLib::load at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDynLib.cpp (line 91)
Loading library /usr/local/lib/OGRE/libCaelum.so
Installing plugin: Caelum
Caelum plugin version 0.6.1 installed
Registering ResourceManager for type PropertyScript
Plugin successfully installed
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Pentium(R) 4 CPU 3.20GHz
 *      SSE: yes
 *     SSE2: yes
 *     SSE3: yes
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: no
 * 3DNOWEXT: no
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: yes
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::_createRenderWindow  "Rigs of Rods version 0.4.0.5", 800x600 windowed  miscParams: FSAA=0  displayFrequency=50 MHz gamma=No vsync=No 
GLXWindow::create used FBConfigID = 153
GL_VERSION = 2.1.2 NVIDIA 295.40
GL_VENDOR = NVIDIA Corporation
GL_RENDERER = GeForce 7900 GT/GTO/PCIe/SSE2
GL_EXTENSIONS  = GL_ARB_color_buffer_float GL_ARB_compressed_texture_pixel_storage  GL_ARB_conservative_depth GL_ARB_copy_buffer GL_ARB_depth_clamp  GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_ES2_compatibility  GL_ARB_explicit_attrib_location GL_ARB_fragment_program  GL_ARB_fragment_program_shadow GL_ARB_fragment_shader  GL_ARB_framebuffer_object GL_ARB_get_program_binary  GL_ARB_half_float_pixel GL_ARB_half_float_vertex GL_ARB_imaging  GL_ARB_internalformat_query GL_ARB_map_buffer_alignment  GL_ARB_map_buffer_range GL_ARB_multisample GL_ARB_multitexture  GL_ARB_occlusion_query GL_ARB_occlusion_query2  GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite  GL_ARB_provoking_vertex GL_ARB_robustness GL_ARB_sampler_objects  GL_ARB_separate_shader_objects GL_ARB_shader_objects  GL_ARB_shading_language_100 GL_ARB_shading_language_420pack  GL_ARB_shading_language_include GL_ARB_shadow GL_ARB_sync  GL_ARB_texture_border_clamp GL_ARB_texture_compression  GL_ARB_texture_cube_map GL_ARB_texture_env_add  GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar  GL_ARB_texture_env_dot3 GL_ARB_texture_float  GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two  GL_ARB_texture_rectangle GL_ARB_texture_rg GL_ARB_texture_storage  GL_ARB_texture_swizzle GL_ARB_timer_query GL_ARB_transpose_matrix  GL_ARB_vertex_array_bgra GL_ARB_vertex_array_object  GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader  GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float  GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr  GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate  GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract  GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test  GL_EXT_direct_state_access GL_EXT_draw_range_elements GL_EXT_fog_coord  GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample  GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters  GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil  GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters  GL_EXT_provoking_vertex GL_EXT_rescale_normal GL_EXT_secondary_color  GL_EXT_separate_shader_objects GL_EXT_separate_specular_color  GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap  GL_EXT_texture3D GL_EXT_texture_compression_dxt1  GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map  GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine  GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic  GL_EXT_texture_format_BGRA8888 GL_EXT_texture_lod  GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp  GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_texture_sRGB_decode  GL_EXT_texture_storage GL_EXT_texture_swizzle GL_EXT_timer_query  GL_EXT_vertex_array GL_EXT_vertex_array_bgra GL_EXT_x11_sync_object  GL_EXT_import_sync_object GL_IBM_rasterpos_clip  GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_alpha_test  GL_NV_blend_minmax GL_NV_blend_square GL_NV_complex_primitives  GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fbo_color_attachments  GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragdepth  GL_NV_fragment_program GL_NV_fragment_program_option  GL_NV_fragment_program2 GL_NV_framebuffer_multisample_coverage  GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint  GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range  GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners  GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_barrier  GL_NV_texture_compression_vtc GL_NV_texture_env_combine4  GL_NV_texture_expand_normal GL_NV_texture_lod_clamp  GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2  GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2  GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2  GL_NV_vertex_program2_option GL_NV_vertex_program3  GL_NVX_conditional_render GL_OES_depth24 GL_OES_depth32  GL_OES_depth_texture GL_OES_element_index_uint GL_OES_fbo_render_mipmap  GL_OES_get_program_binary GL_OES_mapbuffer GL_OES_packed_depth_stencil  GL_OES_rgb8_rgba8 GL_OES_standard_derivatives GL_OES_texture_3D  GL_OES_texture_float GL_OES_texture_float_linear  GL_OES_texture_half_float GL_OES_texture_half_float_linear  GL_OES_texture_npot GL_OES_vertex_array_object GL_OES_vertex_half_float  GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture  GL_SGIX_shadow GL_SUN_slice_accum 
Supported GLX extensions:  GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig  GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control  GLX_EXT_swap_control GLX_EXT_texture_from_pixmap GLX_ARB_create_context  GLX_ARB_create_context_profile GLX_EXT_create_context_es2_profile  GLX_ARB_create_context_robustness GLX_ARB_multisample  GLX_NV_float_buffer GLX_ARB_fbconfig_float GLX_ARB_get_proc_address 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GLSL support detected
GL: Using GL_EXT_framebuffer_object for rendering to textures (best)
FBO PF_UNKNOWN depth/stencil support: D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R5G6B5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B5G6R5 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_B8G8R8A8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2R10G10B10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_A2B10G10R10 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_FLOAT16_RGBA depth/stencil support: D0S0 D16S0 
FBO PF_FLOAT32_RGB depth/stencil support: D0S0 D16S0 
FBO PF_FLOAT32_RGBA depth/stencil support: D0S0 D16S0 
FBO PF_X8R8G8B8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_X8B8G8R8 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGBA depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_R3G3B2 depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
FBO PF_SHORT_RGB depth/stencil support: D0S0 D16S0 D24S0 D32S0 Packed-D24S8 
[GL]  : Valid FBO targets PF_UNKNOWN PF_R5G6B5 PF_B5G6R5 PF_R8G8B8 PF_B8G8R8  PF_A8R8G8B8 PF_B8G8R8A8 PF_A2R10G10B10 PF_A2B10G10R10 PF_FLOAT16_RGB  PF_FLOAT16_RGBA PF_FLOAT32_RGB PF_FLOAT32_RGBA PF_X8R8G8B8 PF_X8B8G8R8  PF_SHORT_RGBA PF_R3G3B2 PF_SHORT_RGB 
RenderSystem capabilities
-------------------------
RenderSystem Name: OpenGL Rendering Subsystem
GPU Vendor: nvidia
Device Name: GeForce 7900 GT/GTO/PCIe/SSE2
Driver Version: 2.1.2.0
 * Fixed function pipeline: yes
 * Hardware generation of mipmaps: yes
 * Texture blending: yes
 * Anisotropic texture filtering: yes
 * Dot product texture operation: yes
 * Cube mapping: yes
 * Hardware stencil buffer: yes
   - Stencil depth: 8
   - Two sided stencil support: yes
   - Wrap stencil values: yes
 * Hardware vertex / index buffers: yes
 * Vertex programs: yes
 * Number of floating-point constants for vertex programs: 256
 * Number of integer constants for vertex programs: 0
 * Number of boolean constants for vertex programs: 0
 * Fragment programs: yes
 * Number of floating-point constants for fragment programs: 512
 * Number of integer constants for fragment programs: 0
 * Number of boolean constants for fragment programs: 0
 * Geometry programs: no
 * Number of floating-point constants for geometry programs: 0
 * Number of integer constants for geometry programs: 0
 * Number of boolean constants for geometry programs: 0
 * Supported Shader Profiles: arbfp1 arbvp1 fp20 fp30 fp40 glsl vp30 vp40
 * Texture Compression: yes
   - DXT: yes
   - VTC: yes
   - PVRTC: no
 * Scissor Rectangle: yes
 * Hardware Occlusion Query: yes
 * User clip planes: yes
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: yes
 * Floating point textures: yes
 * Non-power-of-two textures: yes
 * Volume textures: yes
 * Multiple Render Targets: 4
   - With different bit depths: yes
 * Point Sprites: yes
 * Extended point parameters: yes
 * Max Point Size: 63.375
 * Vertex texture fetch: yes
 * Number of world matrices: 0
 * Number of texture units: 16
 * Stencil buffer depth: 8
 * Number of vertex blend matrices: 0
   - Max vertex textures: 4
   - Vertex textures shared: yes
 * Render to Vertex Buffer : no
 * GL 1.5 without VBO workaround: no
 * Frame Buffer objects: yes
 * Frame Buffer objects (ARB extension): no
 * Frame Buffer objects (ATI extension): no
 * PBuffer support: yes
 * GL 1.5 without HW-occlusion workaround: no
Registering ResourceManager for type Texture
DefaultWorkQueue('Root') initialising on thread 0x29c23e0.
DefaultWorkQueue('Root')::WorkerFunc - thread 0x2c0d000 starting.
Particle Renderer Type 'billboard' registered
SceneManagerFactory for type 'OctreeSceneManager' registered.
DefaultWorkQueue('Root')::WorkerFunc - thread 0x2a29300 starting.
SceneManagerFactory for type 'TerrainSceneManager' registered.
Entering DummyState...
TerrainSceneManager: Registered a new PageSource for type Heightmap
system locale is: C
setting new locale to en_US
error setting new locale
* Language successfully loaded
Loading Bootstrap
resource  zip '/home/user/ror-codehg/bin/resources/OgreCore.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/OgreCore
Creating resource group Bootstrap
Added resource location '/home/user/ror-codehg/bin/resources/OgreCore' of type 'FileSystem' to resource group 'Bootstrap'
Loading Wallpapers
resource  zip '/home/user/ror-codehg/bin/resources/wallpapers.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/wallpapers
Creating resource group Wallpapers
Added resource location '/home/user/ror-codehg/bin/resources/wallpapers' of type 'FileSystem' to resource group 'Wallpapers'
creating loading bar
Initialising resource group Bootstrap
Parsing scripts for resource group Bootstrap
Parsing script OgreCore.material
Parsing script OgreProfiler.material
Parsing script micross.fontdef
Parsing script cyberbit.fontdef
Parsing script cent.fontdef
Parsing script Vera.fontdef
Parsing script Ogre.fontdef
Parsing script highcontrast.fontdef
Parsing script OgreDebugPanel.overlay
Texture:  New_Ogre_Border_Center.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with  5 generated mipmaps from Image. Internal format is  PF_A8R8G8B8,256x128x1.
Texture: New_Ogre_Border.png: Loading 1  faces(PF_A8R8G8B8,256x256x1) with 5 generated mipmaps from Image.  Internal format is PF_A8R8G8B8,256x256x1.
Texture:  New_Ogre_Border_Break.png: Loading 1 faces(PF_A8R8G8B8,32x32x1) with 5  generated mipmaps from Image. Internal format is PF_A8R8G8B8,32x32x1.
Texture:  ogretext.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Parsing script OgreLoadingPanel.overlay
Texture:  ror-promo-02b.jpg: Loading 1 faces(PF_R8G8B8,800x392x1) with 5  generated mipmaps from Image. Internal format is PF_X8R8G8B8,800x392x1.
Finished parsing scripts for resource group Bootstrap
OverlayElementFactory for type ColoredTextArea registered.
Loading main resources
resource  zip '/home/user/ror-codehg/bin/resources/airfoils.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/airfoils
Added resource location '/home/user/ror-codehg/bin/resources/airfoils' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/materials.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/materials
Added resource location '/home/user/ror-codehg/bin/resources/materials' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/meshes.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/meshes
Added resource location '/home/user/ror-codehg/bin/resources/meshes' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/overlays.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/overlays
Added resource location '/home/user/ror-codehg/bin/resources/overlays' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/particles.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/particles
Added resource location '/home/user/ror-codehg/bin/resources/particles' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/mygui.zip' not existing, using  directory instead: /home/user/ror-codehg/bin/resources/mygui
Added resource location '/home/user/ror-codehg/bin/resources/mygui' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/dashboards.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/dashboards
Added resource location '/home/user/ror-codehg/bin/resources/dashboards' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/scripts.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/scripts
Added resource location '/home/user/ror-codehg/bin/resources/scripts' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/textures.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/textures
Added resource location '/home/user/ror-codehg/bin/resources/textures' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/flags.zip' not existing, using  directory instead: /home/user/ror-codehg/bin/resources/flags
Added resource location '/home/user/ror-codehg/bin/resources/flags' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/icons.zip' not existing, using  directory instead: /home/user/ror-codehg/bin/resources/icons
Added resource location '/home/user/ror-codehg/bin/resources/icons' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/famicons.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/famicons
Added resource location '/home/user/ror-codehg/bin/resources/famicons' of type 'FileSystem' to resource group 'General'
Particle Affector Type 'FireExtinguisher' registered
Particle Affector Type 'ExtinguishableFire' registered
Creating Sound Manager
AL lib: pulseaudio.c:331: PulseAudio returned minreq > tlength/2; expect break up
SoundManager: OpenAL vendor is: OpenAL Community
SoundManager: OpenAL version is: 1.1 ALSOFT 1.13
SoundManager: OpenAL renderer is: OpenAL Soft
SoundManager:  OpenAL extensions are: AL_EXT_DOUBLE AL_EXT_EXPONENT_DISTANCE  AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS  AL_EXT_MULAW AL_EXT_MULAW_MCFORMATS AL_EXT_OFFSET  AL_EXT_source_distance_model AL_LOKI_quadriphonic  AL_SOFT_buffer_sub_data AL_SOFT_loop_points
SoundManager: OpenAL device is: SB Live! EMU10k1 Analog Stereo via PulseAudio
SoundManager:  OpenAL ALC extensions are: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT  ALC_EXT_CAPTURE ALC_EXT_disconnect ALC_EXT_EFX  ALC_EXT_thread_local_context
SoundScriptManager: Sound Manager started with 32 sources
resource  zip '/home/user/ror-codehg/bin/resources/sounds.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/sounds
Added resource location '/home/user/ror-codehg/bin/resources/sounds' of type 'FileSystem' to resource group 'General'
resource  zip '/home/user/ror-codehg/bin/resources/hydrax.zip' not existing,  using directory instead: /home/user/ror-codehg/bin/resources/hydrax
Added resource location '/home/user/ror-codehg/bin/resources/hydrax' of type 'FileSystem' to resource group 'General'
Loading filesystems
Creating resource group cache
Added resource location '/home/user/.rigsofrods/cache' of type 'FileSystem' to resource group 'cache'
Added resource location '/home/user/.rigsofrods/config' of type 'FileSystem' to resource group 'General'
Added resource location '/home/user/.rigsofrods/alwaysload' of type 'FileSystem' to resource group 'General'
Creating resource group Scripts
Added resource location '/home/user/.rigsofrods/scripts' of type 'FileSystem' to resource group 'Scripts'
registering Skin Manager
Registering ResourceManager for type RoRVehicleSkins
registering colored text overlay factory
OverlayElementFactory for type ColoredTextArea registered.
initialiseAllResourceGroups()
Parsing scripts for resource group Autodetect
Font CyberbitEnglishusing texture size 1024x512
Info: Freetype returned null for character 127 in font CyberbitEnglish
Info: Freetype returned null for character 128 in font CyberbitEnglish
Info: Freetype returned null for character 129 in font CyberbitEnglish
Info: Freetype returned null for character 130 in font CyberbitEnglish
Info: Freetype returned null for character 131 in font CyberbitEnglish
Info: Freetype returned null for character 132 in font CyberbitEnglish
Info: Freetype returned null for character 133 in font CyberbitEnglish
Info: Freetype returned null for character 134 in font CyberbitEnglish
Info: Freetype returned null for character 135 in font CyberbitEnglish
Info: Freetype returned null for character 136 in font CyberbitEnglish
Info: Freetype returned null for character 137 in font CyberbitEnglish
Info: Freetype returned null for character 138 in font CyberbitEnglish
Info: Freetype returned null for character 139 in font CyberbitEnglish
Info: Freetype returned null for character 140 in font CyberbitEnglish
Info: Freetype returned null for character 141 in font CyberbitEnglish
Info: Freetype returned null for character 142 in font CyberbitEnglish
Info: Freetype returned null for character 143 in font CyberbitEnglish
Info: Freetype returned null for character 144 in font CyberbitEnglish
Info: Freetype returned null for character 145 in font CyberbitEnglish
Info: Freetype returned null for character 146 in font CyberbitEnglish
Info: Freetype returned null for character 147 in font CyberbitEnglish
Info: Freetype returned null for character 148 in font CyberbitEnglish
Info: Freetype returned null for character 149 in font CyberbitEnglish
Info: Freetype returned null for character 150 in font CyberbitEnglish
Info: Freetype returned null for character 151 in font CyberbitEnglish
Info: Freetype returned null for character 152 in font CyberbitEnglish
Info: Freetype returned null for character 153 in font CyberbitEnglish
Info: Freetype returned null for character 154 in font CyberbitEnglish
Info: Freetype returned null for character 155 in font CyberbitEnglish
Info: Freetype returned null for character 156 in font CyberbitEnglish
Info: Freetype returned null for character 157 in font CyberbitEnglish
Info: Freetype returned null for character 158 in font CyberbitEnglish
Info: Freetype returned null for character 159 in font CyberbitEnglish
Info: Freetype returned null for character 160 in font CyberbitEnglish
Texture:  CyberbitEnglishTexture: Loading 1 faces(PF_BYTE_LA,1024x512x1) with 0  generated mipmaps from Image. Internal format is PF_BYTE_LA,1024x512x1.
Finished parsing scripts for resource group Autodetect
Parsing scripts for resource group General
Parsing script general.program
Parsing script nicemetal.program
Parsing script fresnel.material
Compiler error: object unsupported by render system in fresnel.material(20)
Parsing script eurosigns.material
Parsing script largedocks.material
Parsing script ror.material
Parsing script trafficlights.material
Parsing script truckshop.material
Parsing script runway.material
Parsing script managed.material
Parsing script floatingdocks.material
Parsing script marina.material
Parsing script general.material
Parsing script grass.material
Parsing script hangar.material
Parsing script pssm.material
Parsing script ferryslip.material
Parsing script character.material
Parsing script particles.material
Parsing script smoke.particle
Parsing script dust.particle
Parsing script mud.particle
Parsing script snow.particle
Parsing script water.particle
Parsing script defaults.soundscript
SoundScriptManager: Parsing script defaults.soundscript
SoundScriptManager: creating template tracks/default_diesel
SoundScriptManager: creating template tracks/default_force
SoundScriptManager: creating template tracks/default_car
SoundScriptManager: creating template tracks/default_starter
SoundScriptManager: creating template tracks/default_turbo
SoundScriptManager: creating template tracks/default_air_purge
SoundScriptManager: creating template tracks/default_horn
SoundScriptManager: creating template tracks/default_pump
SoundScriptManager: creating template tracks/default_police
SoundScriptManager: creating template tracks/default_screetch
SoundScriptManager: creating template tracks/default_brakes
SoundScriptManager: creating template tracks/default_parkbrakes
SoundScriptManager: creating template tracks/default_air
SoundScriptManager: creating template tracks/default_shift
SoundScriptManager: creating template tracks/default_break
SoundScriptManager: creating template tracks/default_creak
Bad SoundScript attribute line: 'trigger_source    creak' in defaults.soundscript
SoundScriptManager: creating template tracks/default_gear_slide
SoundScriptManager: creating template tracks/default_marine_large
SoundScriptManager: creating template tracks/default_marine_small
SoundScriptManager: creating template tracks/default_turboprop_start1
SoundScriptManager: creating template tracks/default_turboprop_lopower1
SoundScriptManager: creating template tracks/default_turboprop_hipower1
SoundScriptManager: creating template tracks/default_turboprop_start2
SoundScriptManager: creating template tracks/default_turboprop_lopower2
SoundScriptManager: creating template tracks/default_turboprop_hipower2
SoundScriptManager: creating template tracks/default_turboprop_start3
SoundScriptManager: creating template tracks/default_turboprop_lopower3
SoundScriptManager: creating template tracks/default_turboprop_hipower3
SoundScriptManager: creating template tracks/default_turboprop_start4
SoundScriptManager: creating template tracks/default_turboprop_lopower4
SoundScriptManager: creating template tracks/default_turboprop_hipower4
SoundScriptManager: creating template tracks/default_turboprop_start5
SoundScriptManager: creating template tracks/default_turboprop_lopower5
SoundScriptManager: creating template tracks/default_turboprop_hipower5
SoundScriptManager: creating template tracks/default_turboprop_start6
SoundScriptManager: creating template tracks/default_turboprop_lopower6
SoundScriptManager: creating template tracks/default_turboprop_hipower6
SoundScriptManager: creating template tracks/default_turboprop_start7
SoundScriptManager: creating template tracks/default_turboprop_lopower7
SoundScriptManager: creating template tracks/default_turboprop_hipower7
SoundScriptManager: creating template tracks/default_turboprop_start8
SoundScriptManager: creating template tracks/default_turboprop_lopower8
SoundScriptManager: creating template tracks/default_turboprop_hipower8
SoundScriptManager: creating template tracks/default_pistonprop_start1
SoundScriptManager: creating template tracks/default_pistonprop_lopower1
SoundScriptManager: creating template tracks/default_pistonprop_hipower1
SoundScriptManager: creating template tracks/default_pistonprop_start2
SoundScriptManager: creating template tracks/default_pistonprop_lopower2
SoundScriptManager: creating template tracks/default_pistonprop_hipower2
SoundScriptManager: creating template tracks/default_pistonprop_start3
SoundScriptManager: creating template tracks/default_pistonprop_lopower3
SoundScriptManager: creating template tracks/default_pistonprop_hipower3
SoundScriptManager: creating template tracks/default_pistonprop_start4
SoundScriptManager: creating template tracks/default_pistonprop_lopower4
SoundScriptManager: creating template tracks/default_pistonprop_hipower4
SoundScriptManager: creating template tracks/default_pistonprop_lopower5
SoundScriptManager: creating template tracks/default_pistonprop_hipower5
SoundScriptManager: creating template tracks/default_pistonprop_lopower6
SoundScriptManager: creating template tracks/default_pistonprop_hipower6
SoundScriptManager: creating template tracks/default_pistonprop_lopower7
SoundScriptManager: creating template tracks/default_pistonprop_hipower7
SoundScriptManager: creating template tracks/default_pistonprop_lopower8
SoundScriptManager: creating template tracks/default_pistonprop_hipower8
SoundScriptManager: creating template tracks/default_turbojet_start1
SoundScriptManager: creating template tracks/default_turbojet_lopower1
SoundScriptManager: creating template tracks/default_turbojet_hipower1
SoundScriptManager: creating template tracks/default_turbojet_afterburner1
SoundScriptManager: creating template tracks/default_turbojet_start2
SoundScriptManager: creating template tracks/default_turbojet_lopower2
SoundScriptManager: creating template tracks/default_turbojet_hipower2
SoundScriptManager: creating template tracks/default_turbojet_afterburner2
SoundScriptManager: creating template tracks/default_turbojet_start3
SoundScriptManager: creating template tracks/default_turbojet_lopower3
SoundScriptManager: creating template tracks/default_turbojet_hipower3
SoundScriptManager: creating template tracks/default_turbojet_afterburner3
SoundScriptManager: creating template tracks/default_turbojet_start4
SoundScriptManager: creating template tracks/default_turbojet_lopower4
SoundScriptManager: creating template tracks/default_turbojet_hipower4
SoundScriptManager: creating template tracks/default_turbojet_afterburner4
SoundScriptManager: creating template tracks/default_turbojet_start5
SoundScriptManager: creating template tracks/default_turbojet_lopower5
SoundScriptManager: creating template tracks/default_turbojet_hipower5
SoundScriptManager: creating template tracks/default_turbojet_afterburner5
SoundScriptManager: creating template tracks/default_turbojet_start6
SoundScriptManager: creating template tracks/default_turbojet_lopower6
SoundScriptManager: creating template tracks/default_turbojet_hipower6
SoundScriptManager: creating template tracks/default_turbojet_afterburner6
SoundScriptManager: creating template tracks/default_turbojet_start7
SoundScriptManager: creating template tracks/default_turbojet_lopower7
SoundScriptManager: creating template tracks/default_turbojet_hipower7
SoundScriptManager: creating template tracks/default_turbojet_afterburner7
SoundScriptManager: creating template tracks/default_turbojet_start8
SoundScriptManager: creating template tracks/default_turbojet_lopower8
SoundScriptManager: creating template tracks/default_turbojet_hipower8
SoundScriptManager: creating template tracks/default_turbojet_afterburner8
SoundScriptManager: creating template tracks/default_reverse_beep
SoundScriptManager: creating template tracks/default_turn_signal
SoundScriptManager: creating template tracks/default_antilock
SoundScriptManager: creating template tracks/default_tractioncontrol
SoundScriptManager: creating template tracks/default_gpws_10
SoundScriptManager: creating template tracks/default_gpws_20
SoundScriptManager: creating template tracks/default_gpws_30
SoundScriptManager: creating template tracks/default_gpws_40
SoundScriptManager: creating template tracks/default_gpws_50
SoundScriptManager: creating template tracks/default_gpws_100
SoundScriptManager: creating template tracks/default_gpws_pullup
SoundScriptManager: creating template tracks/default_gpws_minimums
SoundScriptManager: creating template tracks/default_gpws_apdisconnect
SoundScriptManager: creating template tracks/default_aoa_warning
SoundScriptManager: creating template tracks/default_aivionic_chat01
SoundScriptManager: creating template tracks/default_aivionic_chat02
SoundScriptManager: creating template tracks/default_aivionic_chat03
SoundScriptManager: creating template tracks/default_aivionic_chat04
SoundScriptManager: creating template tracks/default_aivionic_chat05
SoundScriptManager: creating template tracks/default_aivionic_chat06
SoundScriptManager: creating template tracks/default_aivionic_chat07
SoundScriptManager: creating template tracks/default_aivionic_chat08
SoundScriptManager: creating template tracks/default_aivionic_chat09
SoundScriptManager: creating template tracks/default_aivionic_chat10
SoundScriptManager: creating template tracks/default_aivionic_chat11
SoundScriptManager: creating template tracks/default_aivionic_chat12
SoundScriptManager: creating template tracks/default_aivionic_chat13
Parsing script beamtiming.overlay
Parsing script chat.overlay
Parsing script needles.overlay
Texture:  redneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT3,256x256x1.
Texture:  whiteneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom  mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture:  blueneedle.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT3,256x256x1.
Texture: pedal.dds: Loading 1 faces(PF_DXT3,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x64x1.
Texture:  pbrake-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x64x1.
Texture:  locked-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x64x1.
Texture:  secured-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x64x1.
Texture:  lopress-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x64x1.
Texture:  clutch-off.dds: Loading 1 faces(PF_DXT1,256x64x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x64x1.
Texture: lights-off.dds: Loading 1 faces(PF_DXT5,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT5,64x64x1.
Texture: batt-off.dds: Loading 1 faces(PF_DXT5,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT5,64x64x1.
Texture: ign-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture:  TC_OFF.dds: Loading 1 faces(PF_A8R8G8B8,64x64x1) with 5 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,64x64x1.
Texture:  ALB_OFF.dds: Loading 1 faces(PF_A8R8G8B8,64x64x1) with 5 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,64x64x1.
Parsing script loader.overlay
Texture: unknown.dds: Loading 1 faces(PF_DXT5,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT5,256x256x1.
Parsing script directionarrow.overlay
Parsing script 3d_dashblend.overlay
Texture: dashblend.dds: Loading 1 faces(PF_DXT5,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT5,128x64x1.
Parsing script 3d_dashboard.overlay
Texture:  dashboard.dds: Loading 1 faces(PF_DXT1,1024x256x1) with 10 custom  mipmaps from Image. Internal format is PF_DXT1,1024x256x1.
Texture: tacho.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture: speedo.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script airdashboard.overlay
Texture: dashbar.dds: Loading 1 faces(PF_DXT1,512x16x1) with 9 custom mipmaps from Image. Internal format is PF_DXT1,512x16x1.
Texture: airhelp.dds: Loading 1 faces(PF_DXT1,512x32x1) with 9 custom mipmaps from Image. Internal format is PF_DXT1,512x32x1.
Texture:  airspeed.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps  from Image. Internal format is PF_DXT1,128x128x1.
Texture:  altimeter.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x256x1.
Texture: vvi.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture:  adi-tape.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x256x1.
Texture: adi.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT3,256x256x1.
Texture:  adi-bugs.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT3,256x256x1.
Texture: aoa.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture: hsi.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture:  hsi-rose.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT3,256x256x1.
Texture: hsi-bug.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture: hsi-v.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture: hsi-h.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT3,128x128x1.
Texture:  thrusttrack.dds: Loading 1 faces(PF_DXT1,32x128x1) with 7 custom  mipmaps from Image. Internal format is PF_DXT1,32x128x1.
Texture: engfire-off.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture:  engstart-off.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom  mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: airrpm.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x128x1.
Texture:  airpitch.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps  from Image. Internal format is PF_DXT1,128x128x1.
Texture:  airtorque.dds: Loading 1 faces(PF_DXT1,128x128x1) with 7 custom mipmaps  from Image. Internal format is PF_DXT1,128x128x1.
Texture: val-bg.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: ap-up.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: ap-dn.dds: Loading 1 faces(PF_DXT1,64x32x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x32x1.
Texture: hdg-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: wlv-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: nav-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: hold-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: vs-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: athr-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: gpws-on.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Texture: brks-off.dds: Loading 1 faces(PF_DXT1,64x64x1) with 6 custom mipmaps from Image. Internal format is PF_DXT1,64x64x1.
Parsing script 3d_dashboard_needles.overlay
Parsing script boatdashboard.overlay
Texture:  boatspeed.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT1,256x256x1.
Texture:  shipsteer_bg.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom  mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Texture:  boatdepthmeter.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom  mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script needlesmask.overlay
Texture: pitchmask.dds: Loading 1 faces(PF_DXT1,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x64x1.
Texture: rollmask.dds: Loading 1 faces(PF_DXT1,128x64x1) with 7 custom mipmaps from Image. Internal format is PF_DXT1,128x64x1.
Parsing script dashboard.overlay
Texture: anglo.dds: Loading 1 faces(PF_DXT1,128x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT1,128x256x1.
Texture:  instructions.dds: Loading 1 faces(PF_DXT1,256x256x1) with 8 custom  mipmaps from Image. Internal format is PF_DXT1,256x256x1.
Parsing script truckhud.overlay
Parsing script boatneedles.overlay
Texture:  thrusthandle.dds: Loading 1 faces(PF_DXT1,32x32x1) with 5 custom  mipmaps from Image. Internal format is PF_DXT1,32x32x1.
Texture:  shipsteer.dds: Loading 1 faces(PF_DXT3,256x256x1) with 8 custom mipmaps  from Image. Internal format is PF_DXT3,256x256x1.
Parsing script machinedashboard.overlay
Parsing script editor.overlay
Parsing script engine.overlay
Parsing script airneedles.overlay
Parsing script various.overlay
Texture:  pressure.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom mipmaps  from Image. Internal format is PF_DXT3,128x128x1.
Parsing script mouse.overlay
Texture: mouse.dds: Loading 1 faces(PF_DXT3,32x32x1) with 5 custom mipmaps from Image. Internal format is PF_DXT3,32x32x1.
Parsing script credits.overlay
Texture:  credits.dds: Loading 1 faces(PF_DXT1,1024x512x1) with 10 custom mipmaps  from Image. Internal format is PF_DXT1,1024x512x1.
Finished parsing scripts for resource group General
Parsing scripts for resource group Internal
Finished parsing scripts for resource group Internal
Parsing scripts for resource group Scripts
Finished parsing scripts for resource group Scripts
Parsing scripts for resource group Wallpapers
Finished parsing scripts for resource group Wallpapers
Parsing scripts for resource group cache
Finished parsing scripts for resource group cache
Creating resource group Packs
Added resource location '/home/user/ror-codehg/bin/packs' of type 'FileSystem' to resource group 'Packs' with recursive option
Added resource location '/home/user/.rigsofrods/packs' of type 'FileSystem' to resource group 'Packs' with recursive option
Added resource location '/home/user/.rigsofrods/mods' of type 'FileSystem' to resource group 'Packs' with recursive option
Creating resource group VehicleFolders
Added resource location '/home/user/.rigsofrods/vehicles' of type 'FileSystem' to resource group 'VehicleFolders'
Creating resource group TerrainFolders
Added resource location '/home/user/.rigsofrods/terrains' of type 'FileSystem' to resource group 'TerrainFolders'
initialiseResourceGroups: VehicleFolders
Initialising resource group VehicleFolders
Parsing scripts for resource group VehicleFolders
Finished parsing scripts for resource group VehicleFolders
initialiseResourceGroups: TerrainFolders
Initialising resource group TerrainFolders
Parsing scripts for resource group TerrainFolders
Finished parsing scripts for resource group TerrainFolders
initialiseAllResourceGroups() - Content
Initialising resource group Packs
Parsing scripts for resource group Packs
Finished parsing scripts for resource group Packs
Rigs of Rods main loop starting ...
Leaving DummyState...
Entering GameState...
TerrainSceneManager: Registered a new PageSource for type Heightmap
Creating camera
Adding Frame Listener
* Initialise: RenderManager
RenderManager successfully initialized
* Initialise: DataManager
DataManager successfully initialized
* Initialise: Gui
* MyGUI version 3.2.0.4344
* Initialise: ResourceManager
ResourceManager successfully initialized
* Initialise: LayerManager
LayerManager successfully initialized
* Initialise: WidgetManager
WidgetManager successfully initialized
* Initialise: InputManager
InputManager successfully initialized
* Initialise: SubWidgetManager
SubWidgetManager successfully initialized
* Initialise: SkinManager
SkinManager successfully initialized
* Initialise: FontManager
FontManager successfully initialized
* Initialise: ControllerManager
ControllerManager successfully initialized
* Initialise: PointerManager
PointerManager successfully initialized
* Initialise: ClipboardManager
ClipboardManager successfully initialized
* Initialise: LayoutManager
LayoutManager successfully initialized
* Initialise: DynLibManager
DynLibManager successfully initialized
* Initialise: PluginManager
PluginManager successfully initialized
* Initialise: LanguageManager
LanguageManager successfully initialized
* Initialise: FactoryManager
FactoryManager successfully initialized
* Initialise: ToolTipManager
ToolTipManager successfully initialized
Gui successfully initialized
Load ini file 'MyGUI_Images.xml'
Load ini file 'MyGUI_CommonSkins.xml'
Load ini file 'MyGUI_BlueWhiteTheme.xml'
Load ini file 'MyGUI_BlueWhiteImages.xml'
Load ini file 'MyGUI_BlueWhiteSkins.xml'
Texture:  MyGUI_BlueWhiteSkins.png: Loading 1 faces(PF_A8R8G8B8,512x256x1) with 0  generated mipmaps from Image. Internal format is PF_A8R8G8B8,512x256x1.
Load ini file 'MyGUI_BlueWhiteTemplates.xml'
Load ini file 'MyGUI_Pointers.xml'
Load ini file 'MyGUI_Layers.xml'
Load ini file 'MyGUI_Settings.xml'
Texture:  RoR_Pointers.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 0  generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
ResourceTrueTypeFont 'Default' using texture size 256 x 256
ResourceTrueTypeFont 'Default' using real height 13 pixels
ResourceTrueTypeFont 'DefaultBig' using texture size 512 x 256
ResourceTrueTypeFont 'DefaultBig' using real height 17 pixels
Skin 'default' not found. Replaced with default skin. []
Texture:  arrow_up.png: Loading 1 faces(PF_A8R8G8B8,16x16x1) with 0 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,16x16x1.
Texture:  arrow_down.png: Loading 1 faces(PF_A8R8G8B8,16x16x1) with 0 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,16x16x1.
Widget property 'MoveToClick' not found [LoadingWindow.layout]
Texture:  wallpaper.jpg: Loading 1 faces(PF_R8G8B8,495x371x1) with 0 generated  mipmaps from Image. Internal format is PF_X8R8G8B8,495x371x1.
Texture 'loading_04.jpg' not found
ScriptEngine initialized
ScriptEngine (SE) initializing ...
Type registrations done. If you see no error above everything should be working
ScriptEngine running
Mesh: Loading arrow2.mesh.
WARNING:  arrow2.mesh is an older format ([MeshSerializer_v1.40]); you should  upgrade it as soon as possible using the OgreMeshUpgrade tool.
Texture:  targetarrowtex.dds: Loading 1 faces(PF_DXT3,128x128x1) with 7 custom  mipmaps from Image. Internal format is PF_DXT3,128x128x1.
*** Loading OIS ***
*** Initializing OIS ***
*** OIS WINDOW: 71303170
OIS Version: 1.3.0
+ Release Name: 1.3.0
+ Manager: X11InputManager
+ Total Keyboards: 1
+ Total Mice: 1
+ Total JoySticks: 1
* Device: Keyboard Vendor: X11InputManager
* Device: Mouse Vendor: X11InputManager
* Device: JoyStick Vendor: WiseGroup Gameport to USB Box
Creating Joystick 1 (WiseGroup Gameport to USB Box)
* Axes: 8
* Sliders: 0
* POV/HATs: 4
* Buttons: 16
* Vector3: 0
 * Loading input mapping input.map
 * Input map successfully loaded: 195 entries
 * Loading input mapping WiseGroup_Gameport_to_USB_Box.map
Loading category titles from /home/user/.rigsofrods/config/categories.cfg
* mod cache is valid, using it.
loading cache...
CacheSystem::loadCache
cache loaded!
*** windowResized
Texture:  arrow_left.png: Loading 1 faces(PF_A8R8G8B8,16x16x1) with 0 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,16x16x1.
Mesh: Loading character.mesh.
Skeleton: Loading character.skeleton
Error  loading texture male_char01_tex.jpg. Texture layer will be blank.  Loading the texture failed with the following exception: OGRE  EXCEPTION(6:FileNotFoundException): Cannot locate resource  male_char01_tex.jpg in resource group General or any other group. in  ResourceGroupManager::openResource at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreResourceGroupManager.cpp (line  753)
Texture: character.dds: Loading 1  faces(PF_X8R8G8B8,1024x1024x1) with 10 custom mipmaps from Image.  Internal format is PF_X8R8G8B8,1024x1024x1.
Texture:  character-alpha.png: Loading 1 faces(PF_A8R8G8B8,1024x1024x1) with 5  generated mipmaps from Image. Internal format is  PF_A8R8G8B8,1024x1024x1.
Texture 'simple2-terrain.zip_simple2.terrn2.mini.png' not found
Texture:  simple2-terrain.zip_simple2.terrn2.mini.png: Loading 1  faces(PF_R8G8B8,128x128x1) with 5 generated mipmaps from Image. Internal  format is PF_X8R8G8B8,128x128x1.
*** windowMoved
*** windowFocusChange
*** windowFocusChange
*** windowFocusChange
*** windowFocusChange
*** windowFocusChange
Texture: dust.dds: Loading 1 faces(PF_DXT5,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT5,128x128x1.
Texture:  flaretrail.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 5 generated  mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Texture: splash.dds: Loading 1 faces(PF_DXT5,256x256x1) with 8 custom mipmaps from Image. Internal format is PF_DXT5,256x256x1.
Texture: ripple.dds: Loading 1 faces(PF_DXT5,128x128x1) with 7 custom mipmaps from Image. Internal format is PF_DXT5,128x128x1.
Creating resource group General-Reloaded-1
Added resource location '/home/user/.rigsofrods/packs/simple2-terrain.zip' of type 'Zip' to resource group 'General-Reloaded-1'
Initialising resource group General-Reloaded-1
Parsing scripts for resource group General-Reloaded-1
Parsing script simple2.os
Finished parsing scripts for resource group General-Reloaded-1
Registering ResourceManager for type RoRVehicleSkins
Loading new terrain format: simple2.terrn2
  ## Loading Terrain Configuration
 ===== LOADING TERRAIN simple2.terrn2
  ## Initializing Geometry Subsystem
  ## Initializing Object Subsystem
  ## Initializing Collision Subsystem
  ## Initializing Script Subsystem
 (0, 0): Info = radian radian::opAdd() const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opAdd(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opAdd(const degree&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub() const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub(const degree&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opMul(float) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opMul(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opDiv(float) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd() const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd(const radian&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub() const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub(const radian&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opMul(float) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opMul(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opDiv(float) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opAdd(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opSub(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opMul(float) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opMul(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opDiv(float) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opDiv(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opAdd() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opSub() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::midPoint(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::perpendicular() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::randomDeviant(const radian&in, const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian vector3::angleBetween(const vector3&in)
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion vector3::getRotationTo(const vector3&in, const vector3&in) const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::normalisedCopy() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::reflect(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opAdd(const quaternion&in) const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opSub(const quaternion&in) const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opMul(const quaternion&in) const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opMul(float) const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opSub() const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = vector3 quaternion::opMul(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Inverse() const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::UnitInverse() const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Exp() const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Log() const
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getRoll(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getPitch(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getYaw(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion Slerp(float, const quaternion&in, const quaternion&in, bool&in)
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = quaternion SlerpExtraSpins(float, const quaternion&in, const quaternion&in, int&in)
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0):  Info = quaternion Squad(float, const quaternion&in, const  quaternion&in, const quaternion&in, const quaternion&in,  bool&in)
 (0, 0): Error = Don't support returning type  'quaternion' by value from application in native calling convention on  this platform
 (0, 0): Info = quaternion nlerp(float, const quaternion&in, const quaternion&in, bool&in)
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = vector3 LocalStorage::getVector3(string&in)
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian LocalStorage::getRadian(string&in)
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = degree LocalStorage::getDegree(string&in)
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion LocalStorage::getQuaternion(string&in)
 (0,  0): Error = Don't support returning type 'quaternion' by value from  application in native calling convention on this platform
 (0, 0): Info = vector3 BeamClass::getGForces()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getPersonPosition()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian GameScriptClass::getPersonRotation()
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraPosition()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraDirection()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraOrientation()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Error = Invalid configuration. Verify the registered application interface.
Failed to build the module
  ## Initializing Shadow Subsystem
  ## Initializing Camera Subsystem
  ## Initializing Sky Subsystem
Error  loading texture cloudy_noon_fr.dds. Texture layer will be blank.  Loading the texture failed with the following exception: OGRE  EXCEPTION(6:FileNotFoundException): Cannot locate resource  cloudy_noon_fr.dds in resource group General or any other group. in  ResourceGroupManager::openResource at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreResourceGroupManager.cpp (line  753)
  ## Initializing Light Subsystem
  ## Initializing Fog Subsystem
  ## Initializing Vegetation Subsystem
  ## Initializing Environment Map Subsystem
  ## Initializing Dashboards Subsystem
 ===== LOADING TERRAIN GEOMETRY simple2.terrn2
  ## Loading Terrain Geometry
loading page config for page [0,0] : 


An  exception has occured!: OGRE EXCEPTION(7:InternalErrorException):  Streaming error occurred in FileStreamDataStream::readLine at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDataStream.cpp (line 612) /  url:  http://wiki.rigsofrods.com/index.php?title=Error_7#FileStreamDataStream::readLine



An  exception has occured!: OGRE EXCEPTION(7:InternalErrorException):  Streaming error occurred in FileStreamDataStream::readLine at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDataStream.cpp (line 612) /  url:  http://wiki.rigsofrods.com/index.php?title=Error_7#FileStreamDataStream::readLine

Leaving GameState...
Shutdown OGRE...
*** glibc detected *** ./RoR: double free or corruption (!prev): 0x0000000002a244f0 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7ec96)[0x7f395a0b0c96]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSsD1Ev+0x23)[0x7f395a99fc13]
/lib/x86_64-linux-gnu/libc.so.6(__cxa_finalize+0x9d)[0x7f395a06dd3d]
/usr/local/lib/libCaelum.so(+0x81666)[0x7f395b018666]
======= Memory map: ========
00400000-00be4000 r-xp 00000000 08:16 3282782                            /home/user/ror-codehg/bin/RoR
00de3000-00de5000 r--p 007e3000 08:16 3282782                            /home/user/ror-codehg/bin/RoR
00de5000-00dec000 rw-p 007e5000 08:16 3282782                            /home/user/ror-codehg/bin/RoR
00dec000-00dfd000 rw-p 00000000 00:00 0 
02999000-0546f000 rw-p 00000000 00:00 0                                  [heap]
400ce000-40149000 rw-p 00000000 00:00 0 
40cc2000-40cc4000 r-xs 00000000 08:16 3552960                            /tmp/glGoun7I (deleted)
7f392c000000-7f392c021000 rw-p 00000000 00:00 0 
7f392c021000-7f3930000000 ---p 00000000 00:00 0 
7f3934000000-7f3934021000 rw-p 00000000 00:00 0 
7f3934021000-7f3938000000 ---p 00000000 00:00 0 
7f393a296000-7f393bfff000 rw-p 00000000 00:00 0 
7f3940000000-7f3940021000 rw-p 00000000 00:00 0 
7f3940021000-7f3944000000 ---p 00000000 00:00 0 
7f39449b4000-7f3944bb4000 rw-s d913d000 00:05 9784                       /dev/nvidia0
7f3944bb4000-7f3944db4000 rw-s d933d000 00:05 9784                       /dev/nvidia0
7f3944db4000-7f3944f34000 rw-s d953d000 00:05 9784                       /dev/nvidia0
7f3944f34000-7f394508f000 rw-s 45449000 00:05 9784                       /dev/nvidia0
7f394508f000-7f39451ea000 rw-s 4746c000 00:05 9784                       /dev/nvidia0
7f39451ea000-7f39452ea000 rw-s 47483000 00:05 9784                       /dev/nvidia0
7f39452ea000-7f39454ea000 rw-p 00000000 00:00 0 
7f39454ea000-7f39454ef000 r-xp 00000000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f39454ef000-7f39456ee000 ---p 00005000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f39456ee000-7f39456ef000 r--p 00004000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f39456ef000-7f39456f0000 rw-p 00005000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f39457a5000-7f39459a5000 rw-s 47704000 00:05 9784                       /dev/nvidia0
7f39459a5000-7f39459ae000 r-xp 00000000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f39459ae000-7f3945bad000 ---p 00009000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f3945bad000-7f3945bae000 r--p 00008000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f3945bae000-7f3945baf000 rw-p 00009000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f3945baf000-7f3945faf000 rw-s d9e13000 00:05 9784                       /dev/nvidia0
7f3945faf000-7f39463af000 rw-s da213000 00:05 9784                       /dev/nvidia0
7f39463af000-7f39466af000 rw-p 00000000 00:00 0 
7f39467af000-7f39469af000 rw-s 56f13000 00:05 9784                       /dev/nvidia0
7f39469af000-7f39469b0000 ---p 00000000 00:00 0 
7f39469b0000-7f39471b0000 rw-p 00000000 00:00 0 
7f39471b0000-7f39471b1000 ---p 00000000 00:00 0 
7f39471b1000-7f39479b1000 rw-p 00000000 00:00 0 
7f39479b1000-7f39479c9000 r-xp 00000000 08:16 3298911                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f39479c9000-7f3947bc9000 ---p 00018000 08:16 3298911                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f3947bc9000-7f3947bca000 r--p 00018000 08:16 3298911                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f3947bca000-7f3947bcb000 rw-p 00019000 08:16 3298911                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f3947bcb000-7f3947bcd000 rw-p 00000000 00:00 0 
7f3947bcd000-7f3947bd3000 r-xp 00000000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f3947bd3000-7f3947dd2000 ---p 00006000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f3947dd2000-7f3947dd3000 r--p 00005000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f3947dd3000-7f3947dd4000 rw-p 00006000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f3947dd4000-7f3947dff000 r-xp 00000000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f3947dff000-7f3947ffe000 ---p 0002b000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f3947ffe000-7f3947fff000 r--p 0002a000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f3947fff000-7f3948000000 rw-p 0002b000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f3948000000-7f3948021000 rw-p 00000000 00:00 0 
7f3948021000-7f394c000000 ---p 00000000 00:00 0 
7f394c06b000-7f394c31e000 r-xp 00000000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f394c31e000-7f394c51d000 ---p 002b3000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f394c51d000-7f394c539000 r--p 002b2000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f394c539000-7f394c53a000 rw-p 002ce000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f394c53a000-7f394c582000 r-xp 00000000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f394c582000-7f394c782000 ---p 00048000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f394c782000-7f394c783000 r--p 00048000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f394c783000-7f394c784000 rw-p 00049000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f394c784000-7f394c79b000 r-xp 00000000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f394c79b000-7f394c99a000 ---p 00017000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f394c99a000-7f394c99b000 r--p 00016000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f394c99b000-7f394c99c000 rw-p 00017000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f394c99c000-7f394c99e000 rw-p 00000000 00:00 0 
7f394c99e000-7f394c9a3000 r-xp 00000000 08:16 400773                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f394c9a3000-7f394cba2000  ---p 00005000 08:16 400773                      /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1Aborted (core dumped)
user@Ubuntu01:~/ror-codehg/bin$ 

```the only errors i saw were these:

```
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager
failed  to load plugin: /usr/local/lib/OGRE/Plugin_CgProgramManager: OGRE  EXCEPTION(7:InternalErrorException): Could not load dynamic library  /usr/local/lib/OGRE/Plugin_CgProgramManager.  System Error:  libOgreMain-1.6.4.so: cannot open shared object file: No such file or  directory in DynLib::load at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDynLib.cpp (line 91)
```a bunch of errors about radians right after it loads the terrain, and a few "file not found"s

then the biggie:

```
An  exception has occured!: OGRE EXCEPTION(7:InternalErrorException):  Streaming error occurred in FileStreamDataStream::readLine at  /build/buildd/ogre-1.7.4/OgreMain/src/OgreDataStream.cpp (line 612) /  url:  http://wiki.rigsofrods.com/index.php?title=Error_7#FileStreamDataStream::readLine
```i'm not trying to connect to a server (at least to my knowledge.. im not on multiplayer or anything)
does your compile attempt work on single player?

EDIT:

i searched my ror.log for "conn" and found this: (don't think it helps :P)

```
14:04:52: SoundManager: OpenAL device is: SB Live! EMU10k1 Analog Stereo via PulseAudio
14:04:52: SoundManager: OpenAL ALC extensions are: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_disconnect ALC_EXT_EFX ALC_EXT_thread_local_context
14:04:52: SoundScriptManager: Sound Manager started with 32 sources
```
and later 
```
14:04:52: SoundScriptManager: creating template tracks/default_gpws_apdisconnect
```

---

### Post by lego11 on 2012-10-13
Mine halts here, on the compiling step. I have all the required dependencies installed. I am using Ubuntu 11.04 with ATI FGLRX drivers and gnome.
The reason why caelum is set to false is because I thought first that the compiling problem would be caelum-related.
```
jacopo@ubuntu:~$ cd ./Scrivania/rigsofrods-source-0.4.0.4/
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ cmake -DROR_USE_MYGUI="TRUE" \
> -DROR_USE_OPENAL="TRUE" \
> -DROR_USE_LUA="TRUE" \
> -DROR_USE_SOCKETW="TRUE" \
> -DROR_USE_MOFILEREADER="TRUE" \
> -DROR_USE_PAGED="TRUE" \
> -DROR_USE_CAELUM="TRUE" \
> -DROR_USE_ANGELSCRIPT="TRUE" .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- checking for module 'gtk+-2.0'
--   found gtk+-2.0, version 2.24.4
-- checking for module 'gdk-pixbuf-2.0'
--   found gdk-pixbuf-2.0, version 2.23.3
-- checking for module 'OGRE'
--   found OGRE, version 1.8.0
-- checking for module 'OGRE-Terrain'
--   found OGRE-Terrain, version 1.8.0
-- checking for module 'OGRE-Paging'
--   found OGRE-Paging, version 1.8.0
-- checking for module 'OGRE-RTShaderSystem'
--   found OGRE-RTShaderSystem, version 1.8.0
-- checking for module 'OIS'
--   found OIS, version 1.3.0
-- Found CURL: /usr/lib/libcurl.so 
-- Found OpenAL: /usr/lib/libopenal.so 
-- checking for module 'MYGUI'
--   found MYGUI, version 3.2.0
-- MYGUI Enabled:          YES
-- MYGUI_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS:     /usr/local/lib
-- MYGUI_LIBRARIES:        MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:          YES
-- OPENAL_INCLUDE_DIRS:     /usr/include/AL
-- OPENAL_LIBRARY_DIRS:     
-- OPENAL_LIBRARIES:        /usr/lib/libopenal.so
-- CURL Enabled:          YES
-- CURL_INCLUDE_DIRS:     /usr/include
-- CURL_LIBRARY_DIRS:     
-- CURL_LIBRARIES:        /usr/lib/libcurl.so
-- SOCKETW Enabled:          YES
-- SOCKETW_INCLUDE_DIRS:     /usr/local/include
-- SOCKETW_LIBRARY_DIRS:     
-- SOCKETW_LIBRARIES:        /usr/local/lib/libSocketW.so
-- PAGED Enabled:          NO
-- CAELUM Enabled:          NO
-- ANGELSCRIPT Enabled:          YES
-- ANGELSCRIPT_INCLUDE_DIRS:     /usr/local/include;/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS:     
-- ANGELSCRIPT_LIBRARIES:        /usr/local/lib/libangelscript.so
-- Found wxWidgets: TRUE 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jacopo/Scrivania/rigsofrods-source-0.4.0.4
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ make 
Scanning dependencies of target angelscript_addons
[  1%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthelper/scripthelper.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scripthandle/scripthandle.cpp.o
[  2%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring.cpp.o
[  3%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstdstring/scriptstdstring_utils.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptdictionary/scriptdictionary.cpp.o
[  4%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/serializer/serializer.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptany/scriptany.cpp.o
[  5%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/autowrapper/generator/generateheader.cpp.o
[  6%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptarray/scriptarray.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptbuilder/scriptbuilder.cpp.o
[  7%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath3d/scriptmath3d.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/contextmgr/contextmgr.cpp.o
[  8%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/debugger/debugger.cpp.o
[  9%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptfile/scriptfile.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmathcomplex.cpp.o
[ 10%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptmath/scriptmath.cpp.o
[ 11%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring_utils.cpp.o
[ 12%] Building CXX object source/angelscript_addons/CMakeFiles/angelscript_addons.dir/scriptstring/scriptstring.cpp.o
Linking CXX static library ../../bin/libangelscript_addons.a
[ 12%] Built target angelscript_addons
Scanning dependencies of target RoR
[ 12%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundScriptManager.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/Sound.cpp.o
[ 13%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/audio/SoundManager.cpp.o
[ 14%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CacheSystem.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/SceneMouse.cpp.o
[ 15%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Character.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/AutoPilot.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Replay.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Savegame.cpp.o
^Cmake[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Savegame.cpp.o] Interruzione
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Interruzione
make: *** [all] Interruzione

jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ make -j5
Scanning dependencies of target RoRConfig
[ 12%] Built target angelscript_addons
[ 13%] [ 14%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/statpict.cpp.o
[ 14%] [ 14%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/Settings.cpp.o
Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/SHA1.cpp.o
Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/Configurator.cpp.o
[ 15%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/ErrorUtils.cpp.o
[ 16%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Savegame.cpp.o
[ 16%] Building CXX object source/configurator/CMakeFiles/RoRConfig.dir/__/main/utils/Utils.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/SkinManager.cpp.o
[ 17%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PositionStorage.cpp.o
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TorqueCurve.cpp.o
[ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/OutProtocol.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ProceduralManager.cpp.o
Linking CXX executable ../../bin/RoRConfig
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/MaterialReplacer.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Skin.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RigsOfRods.cpp.o
[ 21%] Built target RoRConfig
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Road.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/ChatSystem.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/PlayerColours.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o
[ 24%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/BeamEngine.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/CharacterFactory.cpp.o
[ 25%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Road2.cpp.o
[ 26%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/TwoDReplay.cpp.o
[ 26%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/Landusemap.cpp.o
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp: In member function &#8216;virtual bool RoRFrameListener::frameStarted(const Ogre::FrameEvent&)&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp:3204:14: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
[ 27%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainGeometryManager.cpp.o
[ 28%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o] Errore 1
make[2]: *** Attesa per i processi non terminati....
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp: In member function &#8216;void TerrainManager::initLight()&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp:293:27: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o] Errore 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Errore 2
make: *** [all] Errore 2
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ cmake -DROR_USE_MYGUI="TRUE" -DROR_USE_OPENAL="TRUE" -DROR_USE_LUA="FALSE" -DROR_USE_SOCKETW="TRUE" -DROR_USE_MOFILEREADER="TRUE" -DROR_USE_PAGED="TRUE" -DROR_USE_CAELUM="FALSE" -DROR_USE_ANGELSCRIPT="TRUE" .
-- MYGUI Enabled:          YES
-- MYGUI_INCLUDE_DIRS:     /usr/local/include;/usr/local/include/MYGUI
-- MYGUI_LIBRARY_DIRS:     /usr/local/lib
-- MYGUI_LIBRARIES:        MyGUIEngine;/usr/local/lib/libMyGUI.OgrePlatform.a
-- OPENAL Enabled:          YES
-- OPENAL_INCLUDE_DIRS:     /usr/include/AL
-- OPENAL_LIBRARY_DIRS:     
-- OPENAL_LIBRARIES:        /usr/lib/libopenal.so
-- CURL Enabled:          YES
-- CURL_INCLUDE_DIRS:     /usr/include
-- CURL_LIBRARY_DIRS:     
-- CURL_LIBRARIES:        /usr/lib/libcurl.so
-- SOCKETW Enabled:          YES
-- SOCKETW_INCLUDE_DIRS:     /usr/local/include
-- SOCKETW_LIBRARY_DIRS:     
-- SOCKETW_LIBRARIES:        /usr/local/lib/libSocketW.so
-- PAGED Enabled:          NO
-- CAELUM Enabled:          NO
-- ANGELSCRIPT Enabled:          YES
-- ANGELSCRIPT_INCLUDE_DIRS:     /usr/local/include;/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/angelscript_addons
-- ANGELSCRIPT_LIBRARY_DIRS:     
-- ANGELSCRIPT_LIBRARIES:        /usr/local/lib/libangelscript.so
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jacopo/Scrivania/rigsofrods-source-0.4.0.4
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ make -j8
[ 12%] Built target angelscript_addons
[ 15%] Built target RoRConfig
[ 16%] [ 16%] [ 16%] [ 17%] [ 18%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/map/SurveyMapManager.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/map/SurveyMapEntity.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainObjectManager.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o
[ 18%] [ 19%] [ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/DepthOfFieldEffect.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/dof/Lens.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/SkyManager.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ColoredTextAreaOverlayElement.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/PreviewRenderer.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Skidmark.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/HDRListener.cpp.o
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp: In member function &#8216;void TerrainManager::initLight()&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp:293:27: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp: In member function &#8216;virtual bool RoRFrameListener::frameStarted(const Ogre::FrameEvent&)&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp:3204:14: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o] Errore 1
make[2]: *** Attesa per i processi non terminati....
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o] Errore 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Errore 2
make: *** [all] Errore 2
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ make -j8
[ 12%] Built target angelscript_addons
[ 15%] Built target RoRConfig
[ 15%] [ 16%] [ 16%] [ 17%] [ 18%] [ 18%] [ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o
[ 19%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreAreaEmitter.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/MovableText.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Water.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/ExtinguishableFireAffector.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreShaderParticleRenderer.cpp.o
Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/OgreBoxEmitter.cpp.o
[ 20%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/particle/FireExtinguisherAffector.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/DustManager.cpp.o
[ 21%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/ShadowManager.cpp.o
[ 22%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/Heathaze.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorVehicle.cpp.o
[ 23%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorFree.cpp.o
[ 24%] Building CXX object source/main/main_sim/CMakeFiles/RoR.dir/__/gfx/camera/CameraBehaviorOrbit.cpp.o
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp: In member function &#8216;void TerrainManager::initLight()&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/terrain/TerrainManager.cpp:293:27: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/terrain/TerrainManager.cpp.o] Errore 1
make[2]: *** Attesa per i processi non terminati....
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp: In member function &#8216;virtual bool RoRFrameListener::frameStarted(const Ogre::FrameEvent&)&#8217;:
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/gameplay/RoRFrameListener.cpp:3204:14: error: invalid use of incomplete type &#8216;struct SkyManager&#8217;
/home/jacopo/Scrivania/rigsofrods-source-0.4.0.4/source/main/GlobalEnvironment.h:30:7: error: forward declaration of &#8216;struct SkyManager&#8217;
make[2]: *** [source/main/main_sim/CMakeFiles/RoR.dir/__/gameplay/RoRFrameListener.cpp.o] Errore 1
make[1]: *** [source/main/main_sim/CMakeFiles/RoR.dir/all] Errore 2
make: *** [all] Errore 2
jacopo@ubuntu:~/Scrivania/rigsofrods-source-0.4.0.4$ 

```](*,):evil:
Please help, I don't want to reboot every time I want to play RoR...

---

### Post by gandalf3 on 2012-10-14
are you sure you have paged geometry? and caelum?
> 
```

-- PAGED Enabled:          NO
 -- CAELUM Enabled:          NO

```


also Rigs of Rods is supposed to run under [wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=26074") with [playonlinux]("http://www.playonlinux.com/en/") if you want to try that out.. 
good luck!

---

### Post by gandalf3 on 2012-10-18
i have tried recompiling it about three times now, using different versions of ogre and other things,
they all returned something like this.. (starting when i click "OK" after selecting map.)
```

Creating resource group General-Reloaded-1
Added resource location '/home/user/.rigsofrods/packs/simple2-terrain.zip' of type 'Zip' to resource group 'General-Reloaded-1'
Initialising resource group General-Reloaded-1
Parsing scripts for resource group General-Reloaded-1
Parsing script simple2.os
Compiler error: unknown error in simple2.os(1): token class, caelum_sky_system, unrecognized.
Compiler error: unknown error in simple2.os(7): token class, sun, unrecognized.
Compiler error: unknown error in simple2.os(25): token class, moon, unrecognized.
Compiler error: unknown error in simple2.os(43): token class, sky_dome, unrecognized.
Finished parsing scripts for resource group General-Reloaded-1
Creating resources for group General-Reloaded-1
All done
Registering ResourceManager for type RoRVehicleSkins
Loading new terrain format: simple2.terrn2
  ## Loading Terrain Configuration
 ===== LOADING TERRAIN simple2.terrn2
  ## Initializing Geometry Subsystem
  ## Initializing Object Subsystem
  ## Initializing Collision Subsystem
  ## Initializing Script Subsystem
 (0, 0): Info = radian radian::opAdd() const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opAdd(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opAdd(const degree&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub() const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opSub(const degree&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opMul(float) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opMul(const radian&in) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian radian::opDiv(float) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd() const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opAdd(const radian&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub() const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opSub(const radian&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opMul(float) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opMul(const degree&in) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = degree degree::opDiv(float) const
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opAdd(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opSub(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opMul(float) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opMul(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opDiv(float) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opDiv(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opAdd() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::opSub() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::midPoint(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::perpendicular() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::randomDeviant(const radian&in, const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian vector3::angleBetween(const vector3&in)
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion vector3::getRotationTo(const vector3&in, const vector3&in) const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::normalisedCopy() const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 vector3::reflect(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opAdd(const quaternion&in) const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opSub(const quaternion&in) const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opMul(const quaternion&in) const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opMul(float) const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::opSub() const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 quaternion::opMul(const vector3&in) const
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Inverse() const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::UnitInverse() const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Exp() const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion quaternion::Log() const
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getRoll(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getPitch(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = radian quaternion::getYaw(bool) const
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion Slerp(float, const quaternion&in, const quaternion&in, bool&in)
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion SlerpExtraSpins(float, const quaternion&in, const quaternion&in, int&in)
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion Squad(float, const quaternion&in, const quaternion&in, const quaternion&in, const quaternion&in, bool&in)
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion nlerp(float, const quaternion&in, const quaternion&in, bool&in)
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 LocalStorage::getVector3(string&in)
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian LocalStorage::getRadian(string&in)
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = degree LocalStorage::getDegree(string&in)
 (0, 0): Error = Don't support returning type 'degree' by value from application in native calling convention on this platform
 (0, 0): Info = quaternion LocalStorage::getQuaternion(string&in)
 (0, 0): Error = Don't support returning type 'quaternion' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 BeamClass::getGForces()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getPersonPosition()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = radian GameScriptClass::getPersonRotation()
 (0, 0): Error = Don't support returning type 'radian' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraPosition()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraDirection()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Info = vector3 GameScriptClass::getCameraOrientation()
 (0, 0): Error = Don't support returning type 'vector3' by value from application in native calling convention on this platform
 (0, 0): Error = Invalid configuration. Verify the registered application interface.
Failed to build the module
  ## Initializing Shadow Subsystem
  ## Initializing Camera Subsystem
  ## Initializing Sky Subsystem
Error loading texture cloudy_noon_fr.dds. Texture layer will be blank. Loading the texture failed with the following exception: OGRE EXCEPTION(6:FileNotFoundException): Cannot locate resource cloudy_noon_fr.dds in resource group General or any other group. in ResourceGroupManager::openResource at /home/user/ror-deps/ogre_src_v1-8-0/OgreMain/src/OgreResourceGroupManager.cpp (line 756)
  ## Initializing Light Subsystem
  ## Initializing Fog Subsystem
  ## Initializing Vegetation Subsystem
  ## Initializing Environment Map Subsystem
  ## Initializing Dashboards Subsystem
 ===== LOADING TERRAIN GEOMETRY simple2.terrn2
  ## Loading Terrain Geometry
loading page config for page [0,0] : 


An exception has occured!: OGRE EXCEPTION(7:InternalErrorException): Streaming error occurred in FileStreamDataStream::readLine at /home/user/ror-deps/ogre_src_v1-8-0/OgreMain/src/OgreDataStream.cpp (line 613) / url: http://wiki.rigsofrods.com/index.php?title=Error_7#FileStreamDataStream::readLine



An exception has occured!: OGRE EXCEPTION(7:InternalErrorException): Streaming error occurred in FileStreamDataStream::readLine at /home/user/ror-deps/ogre_src_v1-8-0/OgreMain/src/OgreDataStream.cpp (line 613) / url: http://wiki.rigsofrods.com/index.php?title=Error_7#FileStreamDataStream::readLine

Leaving GameState...
Shutdown OGRE...
*** glibc detected *** : double free or corruption (!prev): 0x000000000259cf50 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7ec96)[0x7fcd6ba30c96]
/usr/lib/x86_64-linux-gnu/libstdc++.so.6(_ZNSsD1Ev+0x23)[0x7fcd6c31fc13]
/lib/x86_64-linux-gnu/libc.so.6(__cxa_finalize+0x9d)[0x7fcd6b9edd3d]
/usr/local/lib/libCaelum.so(+0x816e6)[0x7fcd6c9986e6]
======= Memory map: ========
00400000-00be8000 r-xp 00000000 08:16 3180606                            /home/user/ror-codehg/bin/RoR
00de7000-00de9000 r--p 007e7000 08:16 3180606                            /home/user/ror-codehg/bin/RoR
00de9000-00df0000 rw-p 007e9000 08:16 3180606                            /home/user/ror-codehg/bin/RoR
00df0000-00e01000 rw-p 00000000 00:00 0 
02533000-04cdf000 rw-p 00000000 00:00 0                                  [heap]
40a72000-40a74000 r-xs 00000000 08:16 3559303                            /tmp/glRFX8Ra (deleted)
41438000-414b3000 rw-p 00000000 00:00 0 
7fcd38000000-7fcd38021000 rw-p 00000000 00:00 0 
7fcd38021000-7fcd3c000000 ---p 00000000 00:00 0 
7fcd40000000-7fcd40021000 rw-p 00000000 00:00 0 
7fcd40021000-7fcd44000000 ---p 00000000 00:00 0 
7fcd46f49000-7fcd47049000 rw-p 00000000 00:00 0 
7fcd47049000-7fcd47249000 rw-s d74d0000 00:05 10275                      /dev/nvidia0
7fcd47249000-7fcd473c9000 rw-s d7e6a000 00:05 10275                      /dev/nvidia0
7fcd473c9000-7fcd47fff000 rw-p 00000000 00:00 0 
7fcd4c000000-7fcd4c021000 rw-p 00000000 00:00 0 
7fcd4c021000-7fcd50000000 ---p 00000000 00:00 0 
7fcd50452000-7fcd51585000 rw-p 00000000 00:00 0 
7fcd51585000-7fcd51785000 rw-s a7382000 00:05 10275                      /dev/nvidia0
7fcd51785000-7fcd518e0000 rw-s 7416d000 00:05 10275                      /dev/nvidia0
7fcd518e0000-7fcd51ce0000 rw-s d7fea000 00:05 10275                      /dev/nvidia0
7fcd51de0000-7fcd51f3b000 rw-s b74ae000 00:05 10275                      /dev/nvidia0
7fcd51f3b000-7fcd5203b000 rw-p 00000000 00:00 0 
7fcd5203b000-7fcd52040000 r-xp 00000000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fcd52040000-7fcd5223f000 ---p 00005000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fcd5223f000-7fcd52240000 r--p 00004000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fcd52240000-7fcd52241000 rw-p 00005000 08:16 400731                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7fcd523f3000-7fcd523fc000 r-xp 00000000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fcd523fc000-7fcd525fb000 ---p 00009000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fcd525fb000-7fcd525fc000 r--p 00008000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fcd525fc000-7fcd525fd000 rw-p 00009000 08:16 400723                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7fcd525fd000-7fcd529fd000 rw-s d9e6a000 00:05 10275                      /dev/nvidia0
7fcd529fe000-7fcd52dfe000 rw-s d8940000 00:05 10275                      /dev/nvidia0
7fcd52dfe000-7fcd52ffe000 rw-p 00000000 00:00 0 
7fcd52ffe000-7fcd52fff000 ---p 00000000 00:00 0 
7fcd52fff000-7fcd537ff000 rw-p 00000000 00:00 0 
7fcd537ff000-7fcd53800000 ---p 00000000 00:00 0 
7fcd53800000-7fcd54000000 rw-p 00000000 00:00 0 
7fcd54000000-7fcd54021000 rw-p 00000000 00:00 0 
7fcd54021000-7fcd58000000 ---p 00000000 00:00 0 
7fcd5800b000-7fcd5810b000 rw-s 32700000 00:05 10275                      /dev/nvidia0
7fcd5810c000-7fcd5820c000 rw-p 00000000 00:00 0 
7fcd5820c000-7fcd5840c000 rw-s 36d87000 00:05 10275                      /dev/nvidia0
7fcd5840c000-7fcd58412000 r-xp 00000000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fcd58412000-7fcd58611000 ---p 00006000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fcd58611000-7fcd58612000 r--p 00005000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fcd58612000-7fcd58613000 rw-p 00006000 08:16 401126                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7fcd58613000-7fcd5863e000 r-xp 00000000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fcd5863e000-7fcd5883d000 ---p 0002b000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fcd5883d000-7fcd5883e000 r--p 0002a000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fcd5883e000-7fcd5883f000 rw-p 0002b000 08:16 401284                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7fcd5883f000-7fcd58af2000 r-xp 00000000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fcd58af2000-7fcd58cf1000 ---p 002b3000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fcd58cf1000-7fcd58d0d000 r--p 002b2000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fcd58d0d000-7fcd58d0e000 rw-p 002ce000 08:16 401286                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7fcd58d0e000-7fcd58d56000 r-xp 00000000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fcd58d56000-7fcd58f56000 ---p 00048000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fcd58f56000-7fcd58f57000 r--p 00048000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fcd58f57000-7fcd58f58000 rw-p 00049000 08:16 400659                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7fcd58f58000-7fcd58f6f000 r-xp 00000000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7fcd58f6f000-7fcd5916e000 ---p 00017000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7fcd5916e000-7fcd5916f000 r--p 00016000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7fcd5916f000-7fcd59170000 rw-p 00017000 08:16 3298925                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7fcd59170000-7fcd59172000 rw-p 00000000 00:00 0 
7fcd59172000-7fcd59177000 r-xp 00000000 08:16 400773                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fcd59177000-7fcd59376000 ---p 00005000 08:16 400773                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fcd59376000-7fcd59377000 r--p 00004000 08:16 400773                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fcd59377000-7fcd59378000 rw-p 00005000 08:16 400773                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7fcd59378000-7fcd593d8000 r-xp 00000000 08:16 401221                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7fcd593d8000-7fcd595d8000 ---p 00060000 08:16 401221                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
7fcd595d8000-7fcd595da000 r--p 00060000 08:16 401221                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25Aborted (core dumped)

```also i can't install new maps.. :(

maybe everything needs to be 32bit?
just a random guess..

EDIT:

how do i checkout the source for the latest stable just in case this an error with that actual program, and not my compiling?
or at least a version that's known to work under 12.04 64bit?

Thanks.

---

### Post by gandalf3 on 2012-10-22
sorry for double posting, but i found that the repo that i started this thread does seem to be still up,
you can view it's contents in a browser:
```

[http://apt.rigsofrods.com/](http://apt.rigsofrods.com/)
```
 but i guess you can only install this if your running lucid?

does anyone know if this works in lucid, or how to try to force it in 12.04? (and hope that it just might work ;))

---

### Post by Hari5g900 on 2012-10-23
Uhhhh, Just to know, can I get a .deb file for Rigs Of Rods for Ubuntu 10.04?

---

### Post by gandalf3 on 2012-10-24
well, there seems to be a 10.04 (i assume by the "lucid" directory..) repository here:

[http://apt.rigsofrods.com/](http://apt.rigsofrods.com/)

try adding this line to your apt sources

```

deb http://apt.rigsofrods.com/ /

```
you can do this either by adding a new line
to your /etc/apt/sources.list file,

or using synaptic or the software center.

Good Luck! ;)

---

### Post by Hari5g900 on 2012-10-25
I got this error message when trying to add the repository and reloading in synaptic
```

Failed to fetch http://apt.rigsofrods.com/Packages.gz  404  File not found
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by gandalf3 on 2012-10-25
hmm.. that's what i got too..
(strange though.. there is a "Packages.gz" file at [http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/](http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/)..)

i tried manually downloading each .deb file and installing by right clicking it and selecting "software center", and it seems to work, except for "ror-unstable.deb"
which gives an error "unsatisfied  dependency: libios-1.2.0"

however, libois-1.3.0 is in the 12.04 repository, maybe it's the right version in 10.04?

---

### Post by Hari5g900 on 2012-10-26
Well then, any ideas how to install it?
May I know which browser you are using? Because I cannot right-click and do it like you did
I'm using chromium

---

### Post by Hari5g900 on 2012-10-26
okay now i get it
I left-clicked and it downloaded and after that selected software center
and i just downloaded this [file]("http://apt.rigsofrods.com/dists/lucid/main/binary-amd64/rigsofrods-unstable-amd64.deb")

---

### Post by gandalf3 on 2012-10-26
did it work?

---

### Post by Hari5g900 on 2012-10-27
well, hmmmmmmmm.... It did not! Sorry:(

---

### Post by Hari5g900 on 2012-10-27
Let me try installing Rigs Of Rods on my new PC after I get it. The one I'm using is pretty old.
I have a question: Installing anything on windows is very very easy compared to linux. Why??

---

### Post by gandalf3 on 2012-10-27
that is a very good question..
there are probably a lot of technical answers that have to do with file systems and stuff..

there is the fact that windows just has more support in general, 
but i would still like to know an explanation of at least one of the reasons that more programs work "out of the box" (downloading a zip instead of a installer and just extracting and running) in windows than Ubuntu. (the only program that i have had work "out of the box" on Ubuntu is Blender3d)

---

### Post by Hari5g900 on 2012-10-30
Well I got Maniadrive and Dakar2010 to work besides blender

---

### Post by fallenshadow on 2012-10-30
The problem here is that the Rigs of Rods guys do not have anyone to compile and build an Ubuntu installer.

Installing stuff in Ubuntu is easy if there is a .deb installer. Unfortunately rigs of rods does not have one.

---

### Post by gandalf3 on 2012-11-01
how hard is it to make one?

---

### Post by Hari5g900 on 2012-11-02
> **gandalf3 said:**
> how hard is it to make one?

Yeah, how hard is it?

---

### Post by zzarko on 2012-11-16
Someone has packaged RoR for Ubuntu:
[https://launchpad.net/~aapo-rantalainen/+archive/rigsofrods](https://launchpad.net/~aapo-rantalainen/+archive/rigsofrods)

---

### Post by gandalf3 on 2012-11-19
wow! don't know how that escaped all my googleing.. (is that a word?)
trying it now!!
THANKS!!!! :D

---

### Post by Mr_Leo on 2012-12-01
I tried installing RoR on Ubuntu 12.04 with the previously mentioned ppa from "Aapo Rantalainen". When I try to launch the game from a terminal, I get this error:

undefined symbol: _ZN5MyGUI13RenderManager12onResizeViewERKNS_5types5TSizeIiEE

---

### Post by gandalf3 on 2012-12-01
hmm.. that looks like the error i got when i tried to compile it..

the PPA didn&#8217;t really work for me either, i loaded the map "simple terrain" and everything worked, but it had random white planes and other artifacts.. (like no ground :P) other than that it worked (the vehicle loaded, looked fine, same with the character.)

> I tried installing RoR on Ubuntu 12.04 with the previously mentioned ppa  from "Aapo Rantalainen". When I try to launch the game from a terminal,  I get this error:

undefined symbol: _ZN5MyGUI13RenderManager12onResizeViewERKNS_5types  5TSizeIiEE

if you have better system specs than me, you might want to try running ror in wine with playonlinux.
it's supposed to work flawlessly
(it worked for me, but crashes often.. i suspect i need more RAM.. i might be totally off though.)

---

