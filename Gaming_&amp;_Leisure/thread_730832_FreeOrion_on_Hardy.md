---
title: "FreeOrion on Hardy?"
date: 2008-03-21
forum: Gaming &amp; Leisure
---

### Post by Achetar on 2008-03-21
Okay. I have downloaded the latest version of freeorion from CVS and attempted to compile it. GiGi compiles fine. But freeorion fails to compile with the following errors:
```
Empire/Empire.o: In function `Empire':
/home/fixer/Projects/freeorion/FreeOrion/Empire/Empire.cpp:620: undefined reference to `GG::Clr::Clr()'
/home/fixer/Projects/freeorion/FreeOrion/Empire/Empire.cpp:620: undefined reference to `GG::Clr::Clr()'
network/Message.o: In function `construct<boost::archive::xml_iarchive, GG::Clr>':
/usr/include/boost/serialization/access.hpp:123: undefined reference to `GG::Clr::Clr()'
network/Message.o: In function `NebulaData':
/home/fixer/Projects/freeorion/FreeOrion/network/../util/MultiplayerCommon.h:92: undefined reference to `GG::Pt::Pt()'
universe/ParserUtil.o: In function `operator()<unsigned int, unsigned int, unsigned int, unsigned int>':
/usr/include/boost/spirit/phoenix/casts.hpp:498: undefined reference to `GG::Clr::Clr(unsigned char, unsigned char, unsigned char, unsigned char)'
universe/Tech.o: In function `TechCategory':
/home/fixer/Projects/freeorion/FreeOrion/universe/Tech.cpp:300: undefined reference to `GG::CLR_WHITE'
/home/fixer/Projects/freeorion/FreeOrion/universe/Tech.cpp:300: undefined reference to `GG::CLR_WHITE'
universe/Tech.o: In function `tuple':
/usr/include/boost/spirit/phoenix/tuples.hpp:703: undefined reference to `GG::Clr::Clr()'
universe/TopLevelParsers.o: In function `tuple':
/usr/include/boost/spirit/phoenix/tuples.hpp:746: undefined reference to `GG::Clr::Clr()'
util/MultiplayerCommon.o: In function `PlayerSetupData':
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:215: undefined reference to `GG::CLR_GRAY'
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:215: undefined reference to `GG::CLR_GRAY'
util/MultiplayerCommon.o: In function `SaveGameEmpireData':
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:204: undefined reference to `GG::Clr::Clr()'
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:204: undefined reference to `GG::Clr::Clr()'
util/MultiplayerCommon.o: In function `SinglePlayerSetupData':
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:196: undefined reference to `GG::Clr::Clr()'
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:196: undefined reference to `GG::Clr::Clr()'
util/MultiplayerCommon.o: In function `XMLToClr(XMLElement const&)':
/home/fixer/Projects/freeorion/FreeOrion/util/MultiplayerCommon.cpp:90: undefined reference to `GG::Clr::Clr()'
server/SaveLoad-server.o: In function `SaveGameUIData':
/home/fixer/Projects/freeorion/FreeOrion/server/../universe/../util/MultiplayerCommon.h:90: undefined reference to `GG::Pt::Pt()'
server/ServerFSM-server.o: In function `SaveGameUIData':
/home/fixer/Projects/freeorion/FreeOrion/server/../universe/../util/MultiplayerCommon.h:90: undefined reference to `GG::Pt::Pt()'
universe/Universe-server.o: In function `Universe::GenerateEmpires(int, std::vector<int, std::allocator<int> >&, std::map<int, PlayerSetupData, std::less<int>, std::allocator<std::pair<int const, PlayerSetupData> > > const&)':
/home/fixer/Projects/freeorion/FreeOrion/universe/Universe.cpp:2775: undefined reference to `GG::Clr::Clr()'
/home/fixer/Projects/freeorion/FreeOrion/universe/Universe.cpp:2788: undefined reference to `GG::FloatClr(float, float, float, float)'
universe/Universe-server.o: In function `__gnu_cxx::__normal_iterator<GG::Clr*, std::vector<GG::Clr, std::allocator<GG::Clr> > > std::__find<__gnu_cxx::__normal_iterator<GG::Clr*, std::vector<GG::Clr, std::allocator<GG::Clr> > >, GG::Clr>(__gnu_cxx::__normal_iterator<GG::Clr*, std::vector<GG::Clr, std::allocator<GG::Clr> > >, __gnu_cxx::__normal_iterator<GG::Clr*, std::vector<GG::Clr, std::allocator<GG::Clr> > >, GG::Clr const&, std::random_access_iterator_tag)':
/usr/include/c++/4.2/bits/stl_algo.h:212: undefined reference to `GG::operator==(GG::Clr const&, GG::Clr const&)'
/usr/include/c++/4.2/bits/stl_algo.h:216: undefined reference to `GG::operator==(GG::Clr const&, GG::Clr const&)'
/usr/include/c++/4.2/bits/stl_algo.h:220: undefined reference to `GG::operator==(GG::Clr const&, GG::Clr const&)'
/usr/include/c++/4.2/bits/stl_algo.h:208: undefined reference to `GG::operator==(GG::Clr const&, GG::Clr const&)'
/usr/include/c++/4.2/bits/stl_algo.h:228: undefined reference to `GG::operator==(GG::Clr const&, GG::Clr const&)'
universe/Universe-server.o:/usr/include/c++/4.2/bits/stl_algo.h:232: more undefined references to `GG::operator==(GG::Clr const&, GG::Clr const&)' follow
collect2: ld returned 1 exit status
scons: *** [freeoriond] Error 1
scons: building terminated because of errors.
```
Any ideas? Do I need to add the GiGI libraries to scons or g++?

---

### Post by Perfect Storm on 2008-03-21
Can you attach all the terminal output from compiling the needed libs to freeOrion.

---

### Post by Achetar on 2008-03-22
You mean GiGi? I would, except that some updates yesterday broke my WiFi card (again). Everything compiled fine. GiGi was installed to /usr/lib /usr/local/lib /usr/lib/pkg-config/*.pc and ~/Projects/freeorion/FreeOrion/GG

When I get my wifi card working again I will post the output for compilation (there were no errors for GiGi)

I was able to install all the other dependencies through apt-get.

---

### Post by Achetar on 2008-03-23
> **Artificial Intelligence said:**
> Can you attach all the terminal output from compiling the needed libs to freeOrion.
Okay, configurationof GiGi outputted this:
```

scons: Reading SConscript files ...
Checking for pkg-config... yes
Configuring for POSIX system...
Checking for C++ header file boost/shared_ptr.hpp... yes
Checking Boost version >= 1.34... (cached) yes
Looking for boost lib boost_signals...
Checking for boost::signals::connection() in C++ library boost_signals... yes
Looking for boost lib boost_filesystem...
Checking for boost::filesystem::initial_path() in C++ library boost_filesystem... yes
Looking for boost lib boost_thread...
Checking for boost::thread::yield() in C++ library boost_thread... yes
Boost configuration... (cached) ok
Checking for C header file pthread.h... yes
Checking for pthread_create() in C library pthread... yes
Checking for C header file GL/gl.h... yes
Checking for C header file GL/glu.h... yes
Checking for glBegin() in C library GL... yes
Checking for gluLookAt() in C library GLU... yes
Checking for freetype2 >= 9.0.0... yes
Checking for C header file ft2build.h... yes
Checking for FT_Init_FreeType() in C library freetype... yes
Checking DevIL version >= 1.6.1... (cached) yes
Checking for C header file IL/il.h... yes
Checking for C header file IL/ilu.h... yes
Checking for ilInit() in C library IL... yes
Checking for iluInit() in C library ILU... yes
Generating libltdl/config.h using libltdl/configure... (cached) ok
Configuration successful... (cached) yes
Copy("GG/ltdl.h", "libltdl/ltdl.h")
Copy("GG/ltdl_config.h", "libltdl/config.h")
Configuring GiGiSDL driver...
Checking for sdl-config... (cached) yes
Checking SDL version >= 1.2.7... (cached) yes
Linking SDL/OpenGL test app... yes
SDL configuration... (cached) yes
Configuration successful... (cached) yes
Configuring GiGiOgre driver...
Checking for pkg-config... yes
Checking for OGRE >= 1.4.5... yes
Checking for C++ header file Ogre.h... yes
Checking for Ogre::Root() in C++ library OgreMain... yes
Configuration successful... (cached) yes
Configuring GiGiOgre's OIS plugin...
Checking for pkg-config... yes
Checking for OIS >= 1.0.0... yes
Checking for C++ header file OIS.h... yes
Configuration successful... (cached) yes

```
And compilation outputted this:
```

scons: Reading SConscript files ...
Using previous successful configuration; if you want to re-run the configuration step, run "scons configure".
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/AlignmentFlags.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/AlignmentFlags.cpp
g++ -o src/Base.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Base.cpp
g++ -o src/BrowseInfoWnd.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/BrowseInfoWnd.cpp
g++ -o src/Button.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Button.cpp
g++ -o src/Clr.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Clr.cpp
g++ -o src/Control.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Control.cpp
g++ -o src/Cursor.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Cursor.cpp
g++ -o src/DrawUtil.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/DrawUtil.cpp
g++ -o src/DropDownList.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/DropDownList.cpp
g++ -o src/DynamicGraphic.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/DynamicGraphic.cpp
g++ -o src/Edit.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Edit.cpp
g++ -o src/EventPump.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/EventPump.cpp
g++ -o src/Font.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Font.cpp
g++ -o src/GUI.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/GUI.cpp
g++ -o src/Layout.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Layout.cpp
g++ -o src/ListBox.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/ListBox.cpp
g++ -o src/Menu.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Menu.cpp
g++ -o src/MultiEdit.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/MultiEdit.cpp
g++ -o src/PluginInterface.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/PluginInterface.cpp
g++ -o src/PtRect.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/PtRect.cpp
g++ -o src/Scroll.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Scroll.cpp
g++ -o src/Slider.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Slider.cpp
g++ -o src/StaticGraphic.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/StaticGraphic.cpp
g++ -o src/StyleFactory.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/StyleFactory.cpp
g++ -o src/TabWnd.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/TabWnd.cpp
g++ -o src/TextControl.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/TextControl.cpp
g++ -o src/Texture.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Texture.cpp
g++ -o src/Timer.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Timer.cpp
g++ -o src/Wnd.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/Wnd.cpp
g++ -o src/WndEditor.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/WndEditor.cpp
g++ -o src/WndEvent.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/WndEvent.cpp
g++ -o src/ZList.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/ZList.cpp
gcc -o src/_vsnprintf.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/_vsnprintf.c
g++ -o src/dialogs/ColorDlg.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/dialogs/ColorDlg.cpp
g++ -o src/dialogs/FileDlg.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/dialogs/FileDlg.cpp
g++ -o src/dialogs/ThreeButtonDlg.os -c -pthread -Wall -O2 -fPIC -I/usr/include/freetype2 -I. -Ilibltdl src/dialogs/ThreeButtonDlg.cpp
gcc -o libltdl/ltdl.os -c -pthread -Wall -O2 -fPIC -DHAVE_CONFIG_H -I/usr/include/freetype2 -I. -Ilibltdl libltdl/ltdl.c
libltdl/ltdl.c: In function 'try_dlopen':
libltdl/ltdl.c:3175: warning: the address of 'sys_search_path' will always evaluate as 'true'
libltdl/ltdl.c: In function 'lt_dlopenext':
libltdl/ltdl.c:3467: warning: the address of 'archive_ext' will always evaluate as 'true'
libltdl/ltdl.c:3488: warning: the address of 'shlib_ext' will always evaluate as 'true'
libltdl/ltdl.c:3488: warning: the address of 'archive_ext' will always evaluate as 'true'
libltdl/ltdl.c:3491: warning: the address of 'shlib_ext' will always evaluate as 'true'
g++ -o libGiGi.so -pthread -shared src/AlignmentFlags.os src/Base.os src/BrowseInfoWnd.os src/Button.os src/Clr.os src/Control.os src/Cursor.os src/DrawUtil.os src/DropDownList.os src/DynamicGraphic.os src/Edit.os src/EventPump.os src/Font.os src/GUI.os src/Layout.os src/ListBox.os src/Menu.os src/MultiEdit.os src/PluginInterface.os src/PtRect.os src/Scroll.os src/Slider.os src/StaticGraphic.os src/StyleFactory.os src/TabWnd.os src/TextControl.os src/Texture.os src/Timer.os src/Wnd.os src/WndEditor.os src/WndEvent.os src/ZList.os src/_vsnprintf.os src/dialogs/ColorDlg.os src/dialogs/FileDlg.os src/dialogs/ThreeButtonDlg.os libltdl/ltdl.os -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lfreetype -lz -lfreetype -lIL -lILU
g++ -o src/SDL/SDLGUI.os -c -pthread -Wall -O2 -fPIC -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/freetype2 -I. -Ilibltdl -I/usr/include/SDL src/SDL/SDLGUI.cpp
g++ -o libGiGiSDL.so -pthread -shared src/SDL/SDLGUI.os -L/usr/lib -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lz -lfreetype -lIL -lILU -lSDL
g++ -o src/Ogre/OgreGUI.os -c -pthread -Wall -O2 -fPIC -DOGRE_GUI_gtk -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/freetype2 -I. -Ilibltdl -I/usr/include/OGRE src/Ogre/OgreGUI.cpp
g++ -o libGiGiOgre.so -pthread -shared src/Ogre/OgreGUI.os -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lz -lfreetype -lIL -lILU -lOgreMain -lOgreMain
g++ -o src/Ogre/Plugins/OgreGUIInputPlugin.os -c -pthread -Wall -O2 -fPIC -DOGRE_GUI_gtk -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/freetype2 -I. -Ilibltdl -I/usr/include/OGRE -I/usr/include/OIS -I/usr/include src/Ogre/Plugins/OgreGUIInputPlugin.cpp
g++ -o src/Ogre/Plugins/OISInput.os -c -pthread -Wall -O2 -fPIC -DOGRE_GUI_gtk -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/freetype2 -I. -Ilibltdl -I/usr/include/OGRE -I/usr/include/OIS -I/usr/include src/Ogre/Plugins/OISInput.cpp
g++ -o libGiGiOgrePlugin_OIS.so -pthread -shared src/Ogre/Plugins/OgreGUIInputPlugin.os src/Ogre/Plugins/OISInput.os -L/usr/lib -lboost_signals -lboost_filesystem -lboost_thread -lGL -lGLU -lz -lfreetype -lIL -lILU -lOgreMain -lOIS
scons: done building targets.

```

---

### Post by Perfect Storm on 2008-03-24
Seems alright enough. 
The only diffrence between you and I when compiling is that I compiled OGRE and I use Gutsy, so maybe it's something there.

---

### Post by Achetar on 2008-03-24
Well, I tried compiling OGRE as well and that didn't fix it. Also I noticed a little two letter word in the freeorion config that I absolutely hate. The word 'no'. It was on the GiGiSDL >= 0.6.0 line. I checked in /usr/lib and /usr/local/lib and it is there. Although I was missing some SDL dev libraries when I originally compiled. I will keep trying to get it compiled. When I do a guide is going to be up here faster than you can blink!

---

### Post by Achetar on 2008-03-24
I got it figured out. The -lGiGi and -lGiGiSDL commands were missing from the compile options. Once I added those it worked like a charm. Expect a guide up soon!

---

### Post by Perfect Storm on 2008-03-24
Well, you can just notify the devs instead, as both froorion and gigi you downloaded and installed are upstream development release, then they can correct it in no-time.

---

### Post by Achetar on 2008-03-24
I have. I am actually helping dev the AI, this is why it was so important for me to be able to compile it from SVN.

---

### Post by Achetar on 2008-05-16
Alright, somebody on the FreeOrion forums is doing static linux builds every major release (3.8,3.9,4.0,etc) so ppl can go there to get it. I am now able to test my AI using the static.

---

### Post by Perfect Storm on 2008-05-16
Good as it isn't the easist game to compile and get working, so I'm sure alot of people will be happy :KS

---

