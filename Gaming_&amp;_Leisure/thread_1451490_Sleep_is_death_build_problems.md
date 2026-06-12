---
title: "Sleep is death build problems"
date: 2010-04-10
forum: Gaming &amp; Leisure
---

### Post by ubunchu on 2010-04-10
This new game just came out called sleep is death and I downloaded a copy. It said that it could be built from source on GNU/Linux, and in the runtobuild file you can even choose GNU/Linux, but I get some errors when I do and it doesn't create the executable game file afterwards. I think I have installed all of the dependencies, which are given here: [http://sleepisdeath.net/compileNotes.php](http://sleepisdeath.net/compileNotes.php)


Here is the output of the runToBuild program:

```
./runToBuild 
select platform:
  1 --  GNU/Linux
  2 --  MacOSX
  3 --  Win32 using MinGW
  q --  quit

> 1
Building miniUPNP...
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o minixmlvalid.o minixmlvalid.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o minixml.o minixml.c
cc   minixmlvalid.o minixml.o   -o minixmlvalid
minixml validation test
./minixmlvalid
14 events
touch validateminixml
/bin/sh updateminiupnpcstrings.sh
Detected OS [Ubuntu] version [9.10]
setting OS_STRING macro value to Ubuntu/9.10 in miniupnpcstrings.h.
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o miniwget.o miniwget.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o igd_desc_parse.o igd_desc_parse.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o minisoap.o minisoap.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o miniupnpc.o miniupnpc.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o upnpreplyparse.o upnpreplyparse.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o upnpcommands.o upnpcommands.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o minissdpc.o minissdpc.c
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o upnperrors.o upnperrors.c
ar crs libminiupnpc.a miniwget.o minixml.o igd_desc_parse.o minisoap.o miniupnpc.o upnpreplyparse.o upnpcommands.o minissdpc.o upnperrors.o
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o upnpc.o upnpc.c
cc -o upnpc-static upnpc.o libminiupnpc.a
cc -shared -Wl,-soname,libminiupnpc.so.4 -o libminiupnpc.so miniwget.o minixml.o igd_desc_parse.o minisoap.o miniupnpc.o upnpreplyparse.o upnpcommands.o minissdpc.o upnperrors.o
cc -o upnpc-shared upnpc.o libminiupnpc.so
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o testminixml.o testminixml.c
cc   testminixml.o minixml.o igd_desc_parse.o   -o testminixml
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o testupnpreplyparse.o testupnpreplyparse.c
cc   testupnpreplyparse.o minixml.o upnpreplyparse.o   -o testupnpreplyparse
cc -fPIC -O -Wall -DNDEBUG -DMINIUPNPC_SET_SOCKET_TIMEOUT   -c -o testigddescparse.o testigddescparse.c
testigddescparse.c: In function ‘main’:
testigddescparse.c:51: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
cc   testigddescparse.o igd_desc_parse.o minixml.o   -o testigddescparse
Building SleepIsDeath...
Makefile:587: Makefile.dependencies: No such file or directory
Makefile:810: Makefile.minorGems_dependencies: No such file or directory
rm -f Makefile.minorGems_dependencies
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -I../.. -MM ../../minorGems/graphics/openGL/ScreenGL_SDL.cpp ../../minorGems/graphics/openGL/SingleTextureGL.cpp ../../minorGems/io/linux/TypeIOLinux.cpp ../../minorGems/util/stringUtils.cpp ../../minorGems/util/StringBufferOutputStream.cpp ../../minorGems/io/file/linux/PathLinux.cpp ../../minorGems/system/unix/TimeUnix.cpp ../../minorGems/system/linux/ThreadLinux.cpp ../../minorGems/system/linux/MutexLockLinux.cpp ../../minorGems/graphics/converters/PNGImageConverter.cpp ../../minorGems/util/TranslationManager.cpp ../../minorGems/network/linux/SocketLinux.cpp ../../minorGems/network/linux/HostAddressLinux.cpp ../../minorGems/network/linux/SocketClientLinux.cpp ../../minorGems/network/linux/SocketServerLinux.cpp ../../minorGems/network/NetworkFunctionLocks.cpp ../../minorGems/network/LookupThread.cpp ../../minorGems/network/web/WebRequest.cpp ../../minorGems/util/SettingsManager.cpp ../../minorGems/system/FinishedSignalThread.cpp ../../minorGems/crypto/hashes/sha1.cpp ../../minorGems/formats/encodingUtils.cpp ../../minorGems/io/file/unix/DirectoryUnix.cpp ../../minorGems/network/upnp/portMapping.cpp ../../minorGems/util/log/Log.cpp ../../minorGems/util/log/AppLog.cpp ../../minorGems/util/log/FileLog.cpp ../../minorGems/util/log/PrintLog.cpp ../../minorGems/util/printUtils.cpp >> Makefile.minorGems_dependencies.temp
cat Makefile.minorGems_dependencies.temp | sed ' s/^HostAddress.*\.o/${HOST_ADDRESS_O}/; s/^SocketServer.*\.o/${SOCKET_SERVER_O}/; s/^SocketClient.*\.o/${SOCKET_CLIENT_O}/; s/^SocketUDP.*\.o/${SOCKET_UDP_O}/; s/^SocketManager.*\.o/${SOCKET_MANAGER_O}/; s/^Socket.*\.o/${SOCKET_O}/; s/^NetworkFunctionLocks.*\.o/${NETWORK_FUNCTION_LOCKS_O}/; s/^LookupThread.*\.o/${LOOKUP_THREAD_O}/; s/^Path.*\.o/${PATH_O}/; s/^Directory.*\.o/${DIRECTORY_O}/; s/^TypeIO.*\.o/${TYPE_IO_O}/; s/^Time.*\.o/${TIME_O}/; s/^MutexLock.*\.o/${MUTEX_LOCK_O}/; s/^BinarySemaphore.*\.o/${BINARY_SEMAPHORE_O}/; s/^AppLog.*\.o/${APP_LOG_O}/; s/^PrintLog.*\.o/${PRINT_LOG_O}/; s/^FileLog.*\.o/${FILE_LOG_O}/; s/^Log.*\.o/${LOG_O}/; s/^PrintUtils.*\.o/${PRINT_UTILS_O}/; s/^WebClient.*\.o/${WEB_CLIENT_O}/; s/^URLUtils.*\.o/${URL_UTILS_O}/; s/^MimeTyper.*\.o/${MIME_TYPER_O}/; s/^WebRequest.*\.o/${WEB_REQUEST_O}/; s/^StringBufferOutputStream.*\.o/${STRING_BUFFER_OUTPUT_STREAM_O}/; s/^XMLUtils.*\.o/${XML_UTILS_O}/; s/^HTMLUtils.*\.o/${HTML_UTILS_O}/; s/^SettingsManager.*\.o/${SETTINGS_MANAGER_O}/; s/^TranslationManager.*\.o/${TRANSLATION_MANAGER_O}/; s/^stringUtils.*\.o/${STRING_UTILS_O}/; s/^sha1.*\.o/${SHA1_O}/; ' | sed ' s/^MemoryTrack.*\.o/${MEMORY_TRACK_O}/; s/^DebugMemory.*\.o/${DEBUG_MEMORY_O}/; s/^HostCatcher.*\.o/${HOST_CATCHER_O}/; s/^OutboundChannel.*\.o/${OUTBOUND_CHANNEL_O}/; s/^DuplicateMessageDetector.*\.o/${DUPLICATE_MESSAGE_DETECTOR_O}/; s/^protocolUtils.*\.o/${PROTOCOL_UTILS_O}/; s/^MessagePerSecondLimiter.*\.o/${MESSAGE_PER_SECOND_LIMITER_O}/; s/^MultiSourceDownloader.*\.o/${MULTI_SOURCE_DOWNLOADER_O}/; s/^encodingUtils.*\.o/${ENCODING_UTILS_O}/; s/^WebServer.*\.o/${WEB_SERVER_O }/; s/^RequestHandlingThread.*\.o/${REQUEST_HANDLING_THREAD_O}/; s/^ThreadHandlingThread.*\.o/${THREAD_HANDLING_THREAD_O}/; s/^Thread.*\.o/${THREAD_O}/; s/^ConnectionPermissionHandler.*\.o/${CONNECTION_PERMISSION_HANDLER_O}/; s/^StopSignalThread.*\.o/${STOP_SIGNAL_THREAD_O}/; s/^FinishedSignalThreadManager.*\.o/${FINISHED_SIGNAL_THREAD_MANAGER_O}/; s/^FinishedSignalThread.*\.o/${FINISHED_SIGNAL_THREAD_O}/; s/^ScreenGL.*\.o/${SCREEN_GL_O}/; s/^ScreenGLSDL.*\.o/${SCREEN_GL_SDL_O}/; s/^SingleTextureGL.*\.o/${SINGLE_TEXTURE_GL_O}/; s/^PNGImageConverter.*\.o/${PNG_IMAGE_CONVERTER_O}/; s/^portMapping.*\.o/${PORT_MAPPING_O}/; ' >> Makefile.minorGems_dependencies
rm -f Makefile.minorGems_dependencies.temp
rm -f Makefile.dependencies
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -MM game.cpp common.cpp uniqueID.cpp resourceManager.cpp resourceDatabase.cpp StringTree.cpp buttons.cpp Connection.cpp GameHalf.cpp PlayerGame.cpp ControllerGame.cpp Tile.cpp Room.cpp Editor.cpp ColorEditor.cpp HueValuePicker.cpp ColorWells.cpp BorderPanel.cpp TileEditor.cpp Sprite.cpp DrawToolSet.cpp labels.cpp ResourcePicker.cpp TilePicker.cpp RoomPicker.cpp RoomEditor.cpp SpriteResource.cpp SpritePicker.cpp SpriteEditor.cpp GameState.cpp GameStateEditor.cpp GameStateDisplay.cpp StateToolSet.cpp TransformToolSet.cpp ToolTipManager.cpp ToolTipDisplay.cpp StateObject.cpp StateObjectPicker.cpp StateObjectDisplay.cpp StateObjectEditor.cpp PlayerMoveEditor.cpp MoveToolSet.cpp TimerDisplay.cpp FixedTipDisplay.cpp ToolTipComponentGL.cpp musicPlayer.cpp Envelope.cpp Timbre.cpp NoteGridDisplay.cpp MusicEditor.cpp imageCache.cpp ToolTipSliderGL.cpp DemoCodeChecker.cpp SelectionManager.cpp WarningDisplay.cpp DragAndDropManager.cpp Music.cpp MusicPicker.cpp Scene.cpp ScenePicker.cpp packSaver.cpp PressActionGUIPanelGL.cpp fixOldResources.cpp   >> Makefile.dependencies.temp
cat Makefile.dependencies.temp | sed ' ' >> Makefile.dependencies
rm -f Makefile.dependencies.temp
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o game.o game.cpp
In file included from game.cpp:38:
../../minorGems/graphics/openGL/gui/TextGL.h: In member function ‘void TextGL::drawCharacter(char, double, double, double, double, double*)’:
../../minorGems/graphics/openGL/gui/TextGL.h:482: warning: array subscript has type ‘char’
../../minorGems/graphics/openGL/gui/TextGL.h:483: warning: array subscript has type ‘char’
../../minorGems/graphics/openGL/gui/TextGL.h:489: warning: array subscript has type ‘char’
../../minorGems/graphics/openGL/gui/TextGL.h: In member function ‘double TextGL::measureTextWidth(char*)’:
../../minorGems/graphics/openGL/gui/TextGL.h:660: warning: array subscript has type ‘char’
../../minorGems/graphics/openGL/gui/TextGL.h:661: warning: array subscript has type ‘char’
In file included from game.cpp:48:
../../minorGems/io/file/File.h: In member function ‘File* File::getParentDirectory()’:
../../minorGems/io/file/File.h:675: warning: deprecated conversion from string constant to ‘char*’
../../minorGems/io/file/File.h:704: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In function ‘void cleanUpAtExit()’:
game.cpp:336: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In function ‘int mainFunction(int, char**)’:
game.cpp:470: warning: deprecated conversion from string constant to ‘char*’
game.cpp:473: warning: deprecated conversion from string constant to ‘char*’
game.cpp:487: warning: deprecated conversion from string constant to ‘char*’
game.cpp:490: warning: deprecated conversion from string constant to ‘char*’
game.cpp:506: warning: deprecated conversion from string constant to ‘char*’
game.cpp:517: warning: deprecated conversion from string constant to ‘char*’
game.cpp:554: warning: deprecated conversion from string constant to ‘char*’
game.cpp:565: warning: deprecated conversion from string constant to ‘char*’
game.cpp:574: warning: deprecated conversion from string constant to ‘char*’
game.cpp:584: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In member function ‘HighlightLabelGL* GameSceneHandler::createLabel(double, char*, TextGL*)’:
game.cpp:844: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In member function ‘void GameSceneHandler::initFromFiles()’:
game.cpp:859: warning: deprecated conversion from string constant to ‘char*’
game.cpp:883: warning: deprecated conversion from string constant to ‘char*’
game.cpp:897: warning: deprecated conversion from string constant to ‘char*’
game.cpp:935: warning: deprecated conversion from string constant to ‘char*’
game.cpp:938: warning: deprecated conversion from string constant to ‘char*’
game.cpp:945: warning: deprecated conversion from string constant to ‘char*’
game.cpp:959: warning: deprecated conversion from string constant to ‘char*’
game.cpp:961: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1010: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1026: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1029: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1035: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1038: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1043: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1046: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1073: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1076: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1079: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1089: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1093: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1111: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1120: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1125: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1139: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1141: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In member function ‘virtual void GameSceneHandler::fireRedraw()’:
game.cpp:1304: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1366: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1447: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1462: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1479: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1585: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1632: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1655: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1678: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1698: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1705: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1708: warning: deprecated conversion from string constant to ‘char*’
game.cpp: In member function ‘virtual void GameSceneHandler::keyPressed(unsigned char, int, int)’:
game.cpp:1832: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1833: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1850: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1851: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1861: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1870: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1910: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1914: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1942: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1995: warning: deprecated conversion from string constant to ‘char*’
game.cpp:1999: warning: deprecated conversion from string constant to ‘char*’
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o common.o common.cpp
In file included from common.cpp:5:
../../minorGems/io/file/File.h: In member function ‘File* File::getParentDirectory()’:
../../minorGems/io/file/File.h:675: warning: deprecated conversion from string constant to ‘char*’
../../minorGems/io/file/File.h:704: warning: deprecated conversion from string constant to ‘char*’
common.cpp: In function ‘Image* readTGA(char*)’:
common.cpp:18: warning: deprecated conversion from string constant to ‘char*’
common.cpp: In function ‘intPair readIntPair(unsigned char*, int, int*)’:
common.cpp:125: warning: deprecated conversion from string constant to ‘char*’
common.cpp: In function ‘int readInt(unsigned char*, int, int*)’:
common.cpp:161: warning: deprecated conversion from string constant to ‘char*’
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o uniqueID.o uniqueID.cpp
uniqueID.cpp: In function ‘uniqueID readUniqueID(unsigned char*, int, int*)’:
uniqueID.cpp:80: warning: deprecated conversion from string constant to ‘char*’
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o resourceManager.o resourceManager.cpp
In file included from resourceManager.cpp:10:
../../minorGems/io/file/File.h: In member function ‘File* File::getParentDirectory()’:
../../minorGems/io/file/File.h:675: warning: deprecated conversion from string constant to ‘char*’
../../minorGems/io/file/File.h:704: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘void initResourceManager()’:
resourceManager.cpp:27: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:30: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:39: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘File* getResourceDir(const char*)’:
resourceManager.cpp:64: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘File* getResourceFile(const char*, uniqueID)’:
resourceManager.cpp:82: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘unsigned char* loadResourceData(const char*, uniqueID, int*, char*)’:
resourceManager.cpp:196: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘unsigned char** loadResourceData(const char*, int, uniqueID*, int*, char*)’:
resourceManager.cpp:356: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp: In function ‘void saveResourceData(const char*, uniqueID, char*, unsigned char*, int)’:
resourceManager.cpp:446: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:456: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:467: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:473: warning: deprecated conversion from string constant to ‘char*’
resourceManager.cpp:477: warning: deprecated conversion from string constant to ‘char*’
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o resourceDatabase.o resourceDatabase.cpp
In file included from resourceDatabase.cpp:14:
../../minorGems/io/file/File.h: In member function ‘File* File::getParentDirectory()’:
../../minorGems/io/file/File.h:675: warning: deprecated conversion from string constant to ‘char*’
../../minorGems/io/file/File.h:704: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp: In function ‘File* getFullDBFile()’:
resourceDatabase.cpp:22: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp:26: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp: In function ‘char** getDataFileLines(int*)’:
resourceDatabase.cpp:103: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp:108: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp:116: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp: In function ‘int countSearchResults(const char*, char*)’:
resourceDatabase.cpp:472: warning: deprecated conversion from string constant to ‘char*’
resourceDatabase.cpp: In function ‘int getSearchResults(const char*, char*, int, int, uniqueID*)’:
resourceDatabase.cpp:540: warning: deprecated conversion from string constant to ‘char*’
g++  -Wall -g  -DLINUX  -O0 -I../.. -c -o StringTree.o StringTree.cpp
StringTree.cpp: In member function ‘void ValueHashTable::insert(valueHolder*)’:
StringTree.cpp:53: error: cast from ‘void*’ to ‘unsigned int’ loses precision
StringTree.cpp: In member function ‘void ValueHashTable::remove(valueHolder*)’:
StringTree.cpp:61: error: cast from ‘void*’ to ‘unsigned int’ loses precision
StringTree.cpp: In member function ‘valueHolder* ValueHashTable::lookup(void*)’:
StringTree.cpp:69: error: cast from ‘void*’ to ‘unsigned int’ loses precision
StringTree.cpp: In member function ‘void StringTreeNode::print()’:
StringTree.cpp:479: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:479: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:479: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:486: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:486: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:491: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:491: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:496: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
StringTree.cpp:496: error: cast from ‘StringTreeNode*’ to ‘int’ loses precision
make: *** [StringTree.o] Error 1
cp: cannot stat `SleepIsDeath/gameSource/SleepIsDeath': No such file or directory
Run SleepIsDeathApp to play.
```

But no SleepIsDeathApp is created. Could anyone help me with this?

---

### Post by netcrusher88 on 2010-04-10
Do you have the -dev packages for those libraries installed?

I've complied it fine under Karmic but SiD segfaults as soon as I launch it... works great under Wine though!

---

### Post by shygantic on 2010-04-10
I had the same error. Installing the dev version of the libraries fixed everything on 9.10.

---

### Post by quadomatic on 2010-04-10
Sorry I don't know how to help you...but thanks for pointing out Sleep is Death. Maybe I'll buy it come the 16th

---

### Post by ubunchu on 2010-04-10
> **shygantic said:**
> I had the same error. Installing the dev version of the libraries fixed everything on 9.10.

which libraries? Like what specific packages do I need to install? I installed every libsdl, libpng, and zlib dev package that I could find on synaptic, but it still isn't making the final file for me.

---

### Post by shygantic on 2010-04-10
I installed libsdl1.2-dev, libpng12-dev, and zlib1g-dev. Just to make sure, try rebooting, delete all of the files that you have already extracted, and re-extract the archive before running runToBuild.

---

### Post by ubunchu on 2010-04-10
> **shygantic said:**
> I installed libsdl1.2-dev, libpng12-dev, and zlib1g-dev. Just to make sure, try rebooting, delete all of the files that you have already extracted, and re-extract the archive before running runToBuild.

I installed all three of those packages, deleted the files I already extracted, restarted, and then ran runToBuild again, and the exact same error log was created (verified with Meld Diff Viewer), so something seems to be going on that doesn't have to do with the development packages.

---

### Post by shygantic on 2010-04-10
Interesting. I just had a closer look at your output and realized that it is different from what I had. It looks to me like you are using a 64 bit operating system and Sleep Is Death is expecting to be built on only 32 bit operating systems. I have a feeling that it will take more than tweaking the makefile to get this to work. I would love to help, but I only have a 32 bit system to work with. It looks like this would be a good time to contact the developer.

If you look at the system requirements it states that it was developed on a 900MHz PC, so it's possible that it was never a problem that came up during development.

---

### Post by shygantic on 2010-04-10
It looks like someone put together a patch. [http://pastebin.com/1cRCXxfk](http://pastebin.com/1cRCXxfk)

---

### Post by ubunchu on 2010-04-10
> **shygantic said:**
> It looks like someone put together a patch. [http://pastebin.com/1cRCXxfk](http://pastebin.com/1cRCXxfk)

How am I supposed to use this file? I know i'm supposed to know how to do patches, but I really have no idea at all.

---

### Post by DePingus on 2010-04-12
*bump*

I'm having probs building this too. And I have no sound in WINE so...any help would be great with this awesome game.

---

### Post by androbit on 2010-04-13
To build it on 64 Bit Ubuntu do this:
Download the patch, it includes changes to 2 files (got the changes from Jason Rohrer).

create the following folder structure:
```

<yourhome>/SleepIsDeath_v13_UnixSource (original sources from the sid page)
<yourhome>/SleepIsDeath_v13 (cp -r of the folder above)
<yourhome>/sidv13.patch (gunzip of the attached patch)

```in <yourhome> run :
```

patch -p0 < sidv13.patch

```after that run: SleepIsDeath_v13/runToBuild 
it should compile, finally run SleepIsDeath_v13/SleepIsDeathApp

---

### Post by ubunchu on 2010-04-13
It works now, thanks a lot everybody!

---

### Post by salimfadhley on 2010-04-23
That pastebin link is down. Can somebody re-publish the patch file for me?

Thanks

---

### Post by salimfadhley on 2010-04-23
Actually the app seems to be compiling now - but is there any way to stop it from going full-screen? It's annoying that it wants to take up all of my monitor. It captures the mouse, and thats doubly annoying because I cannot use my 2nd screen.

Sal

---

### Post by PhazzedOut on 2010-06-19
Patch worked great for 64-bit OS! Thank you. I want to spend some time creating a frozen binary for it (.deb).

---

### Post by androbit on 2010-06-19
Sleep Is Death V14 should build without patch on 64bit ubuntu systems, please redownload the game to get the latest version before creating the binary version.

---

### Post by wideyes on 2010-07-26
Hi there! Latecomer to this post. I've also been having trouble getting this software to build in 10.04. I installed the -dev libraries and am in 32-bit. The build script seems to be working properly, but then it takes a wrong turn and crashes (exits) the terminal I run it in. Since I'm a noob I'm not quite sure how to record the whole interaction, but here is the std. error dump:
```
testigddescparse.c: In function &#8216;main&#8217;:
testigddescparse.c:51: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
Makefile:588: game.dep: No such file or directory
Makefile:588: common.dep: No such file or directory
Makefile:588: uniqueID.dep: No such file or directory
Makefile:588: resourceManager.dep: No such file or directory
Makefile:588: resourceDatabase.dep: No such file or directory
Makefile:588: StringTree.dep: No such file or directory
Makefile:588: buttons.dep: No such file or directory
Makefile:588: Connection.dep: No such file or directory
Makefile:588: GameHalf.dep: No such file or directory
Makefile:588: PlayerGame.dep: No such file or directory
Makefile:588: ControllerGame.dep: No such file or directory
Makefile:588: Tile.dep: No such file or directory
Makefile:588: Room.dep: No such file or directory
Makefile:588: Editor.dep: No such file or directory
Makefile:588: ColorEditor.dep: No such file or directory
Makefile:588: HueValuePicker.dep: No such file or directory
Makefile:588: ColorWells.dep: No such file or directory
Makefile:588: BorderPanel.dep: No such file or directory
Makefile:588: TileEditor.dep: No such file or directory
Makefile:588: Sprite.dep: No such file or directory
Makefile:588: DrawToolSet.dep: No such file or directory
Makefile:588: labels.dep: No such file or directory
Makefile:588: ResourcePicker.dep: No such file or directory
Makefile:588: TilePicker.dep: No such file or directory
Makefile:588: RoomPicker.dep: No such file or directory
Makefile:588: RoomEditor.dep: No such file or directory
Makefile:588: SpriteResource.dep: No such file or directory
Makefile:588: SpritePicker.dep: No such file or directory
Makefile:588: SpriteEditor.dep: No such file or directory
Makefile:588: GameState.dep: No such file or directory
Makefile:588: GameStateEditor.dep: No such file or directory
Makefile:588: GameStateDisplay.dep: No such file or directory
Makefile:588: StateToolSet.dep: No such file or directory
Makefile:588: TransformToolSet.dep: No such file or directory
Makefile:588: ToolTipManager.dep: No such file or directory
Makefile:588: ToolTipDisplay.dep: No such file or directory
Makefile:588: StateObject.dep: No such file or directory
Makefile:588: StateObjectPicker.dep: No such file or directory
Makefile:588: StateObjectDisplay.dep: No such file or directory
Makefile:588: StateObjectEditor.dep: No such file or directory
Makefile:588: PlayerMoveEditor.dep: No such file or directory
Makefile:588: MoveToolSet.dep: No such file or directory
Makefile:588: TimerDisplay.dep: No such file or directory
Makefile:588: FixedTipDisplay.dep: No such file or directory
Makefile:588: ToolTipComponentGL.dep: No such file or directory
Makefile:588: musicPlayer.dep: No such file or directory
Makefile:588: Envelope.dep: No such file or directory
Makefile:588: Timbre.dep: No such file or directory
Makefile:588: NoteGridDisplay.dep: No such file or directory
Makefile:588: MusicEditor.dep: No such file or directory
Makefile:588: imageCache.dep: No such file or directory
Makefile:588: ToolTipSliderGL.dep: No such file or directory
Makefile:588: DemoCodeChecker.dep: No such file or directory
Makefile:588: SelectionManager.dep: No such file or directory
Makefile:588: WarningDisplay.dep: No such file or directory
Makefile:588: DragAndDropManager.dep: No such file or directory
Makefile:588: Music.dep: No such file or directory
Makefile:588: MusicPicker.dep: No such file or directory
Makefile:588: Scene.dep: No such file or directory
Makefile:588: ScenePicker.dep: No such file or directory
Makefile:588: packSaver.dep: No such file or directory
Makefile:588: PressActionGUIPanelGL.dep: No such file or directory
Makefile:588: fixOldResources.dep: No such file or directory
Makefile:588: TimbreResource.dep: No such file or directory
Makefile:588: TimbrePicker.dep: No such file or directory
Makefile:588: TimbreEditor.dep: No such file or directory
Makefile:588: Song.dep: No such file or directory
Makefile:588: SongPicker.dep: No such file or directory
Makefile:588: SongEditor.dep: No such file or directory
Makefile:588: Scale.dep: No such file or directory
Makefile:588: ScalePicker.dep: No such file or directory
Makefile:588: ScaleEditor.dep: No such file or directory
Makefile:588: resourceImporter.dep: No such file or directory
Makefile:588: usageDatabase.dep: No such file or directory
Makefile:588: Palette.dep: No such file or directory
Makefile:588: PalettePicker.dep: No such file or directory
Makefile:588: PaletteEditor.dep: No such file or directory
Makefile:588: GridOverlay.dep: No such file or directory
Makefile:588: speechHints.dep: No such file or directory
Makefile:812: Makefile.minorGems_dependencies: No such file or directory
/bin/sh: g++: not found
make: *** [Makefile.minorGems_dependencies] Error 127
```That 2nd line from the end caught my attention: "/bin/sh: g++: not found". Is there some toolkit I'm missing? I noticed on the SID homepage that he mentioned the openGL library is required, and when I type that into Synaptic, I get many packages suggested, some of which are installed. Any thoughts would be helpful!

EDIT: just occurred to me that this thread is marked 'SOLVED'. Should I post this in a new thread?

---

### Post by wideyes on 2010-07-26
Well whaddaya know. I installed the 'g++' package from Synaptic, and the compile worked! The first time I launched the app, it crashed my system terribly, but upon reboot, it seems to play fine! I'll report back if I find any errors.

---

