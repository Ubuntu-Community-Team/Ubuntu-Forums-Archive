---
title: "Rigs of rods complie help"
date: 2010-04-24
forum: Gaming &amp; Leisure
---

### Post by retro89 on 2010-04-24
I follow the ubuntu instructions from here:[http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux](http://wiki.rigsofrods.com/pages/Compiling_Sources_under_Ubuntu_Linux)
 I get to build ror and when I try "make -j2 && make install" I get this output:


  1%] Building CXX object source/configurator/CMakeFiles/rorconfig.dir/configurator.cpp.o
[  2%] [  3%] Building CXX object source/main/CMakeFiles/RoR.dir/LoadingWindow.cpp.o
Building CXX object source/main/CMakeFiles/RoR.dir/MapTextureCreator.cpp.o
[  4%] Building CXX object source/main/CMakeFiles/RoR.dir/Console.cpp.o
[  5%] Building CXX object source/main/CMakeFiles/RoR.dir/memoryWrapper.cpp.o
[  6%] Building CXX object source/main/CMakeFiles/RoR.dir/nedmalloc.cpp.o
[  7%] Building CXX object source/main/CMakeFiles/RoR.dir/ColoredTextAreaOverlayElement.cpp.o
In file included from /home/brad/ror-trunk/source/main/Beam.h:54,
                 from /home/brad/ror-trunk/source/main/ExampleFrameListener.h:50,
                 from /home/brad/ror-trunk/source/main/MapTextureCreator.cpp:24:
/home/brad/ror-trunk/source/main/CmdKeyInertia.h:50: error: &#8216;Ogre::vector&#8217; has not been declared
/home/brad/ror-trunk/source/main/CmdKeyInertia.h:50: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;<&#8217; token
In file included from /home/brad/ror-trunk/source/main/ExampleFrameListener.h:50,
                 from /home/brad/ror-trunk/source/main/MapTextureCreator.cpp:24:
/home/brad/ror-trunk/source/main/Beam.h:1337: error: expected unqualified-id before &#8216;<&#8217; token
/home/brad/ror-trunk/source/main/Beam.h:1337: error: expected &#8216;)&#8217; before &#8216;<&#8217; token
/home/brad/ror-trunk/source/main/Beam.h:1337: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
make[2]: *** [source/main/CMakeFiles/RoR.dir/MapTextureCreator.cpp.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [source/main/CMakeFiles/RoR.dir/all] Error 2
make[1]: *** Waiting for unfinished jobs....
/home/brad/ror-trunk/source/configurator/configurator.cpp: In member function &#8216;void MyDialog::updateRendersystems(Ogre::RenderSystem*)&#8217;:
/home/brad/ror-trunk/source/configurator/configurator.cpp:2315: error: conversion from &#8216;Ogre::RenderSystemList*&#8217; to non-scalar type &#8216;const Ogre::RenderSystemList&#8217; requested
make[2]: *** [source/configurator/CMakeFiles/rorconfig.dir/configurator.cpp.o] Error 1
make[1]: *** [source/configurator/CMakeFiles/rorconfig.dir/all] Error 2
make: *** [all] Error 2



What is causing this issue?

---

### Post by garyedwardjohnston on 2010-04-24
Better to ask them...they are the experts on this program

---

