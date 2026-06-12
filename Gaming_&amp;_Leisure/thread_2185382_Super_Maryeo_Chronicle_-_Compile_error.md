---
title: "Super Maryeo Chronicle - Compile error"
date: 2013-11-02
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-11-02
Hi guys, I just found a clone to super mario brothers that I think would be a lot of fun but I can't seem to get it to compile. I am following the instructions here: [http://www.secretmaryo.org/wiki/index.php?title=Compiling_from_Tarball](http://www.secretmaryo.org/wiki/index.php?title=Compiling_from_Tarball)
and it fails during the make process. here's the last bit of code of the make command
```
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
overworld/world_layer.cpp: In member function ‘SMC::cLine_collision SMC::cLayer::Get_Nearest(float, float, SMC::ObjectDirection, unsigned int, int) const’:
overworld/world_layer.cpp:460:60: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  CXX    smc-world_manager.o
In file included from overworld/../overworld/../core/../video/../video/gl_surface.h:23:0,
                 from overworld/../overworld/../core/../video/img_settings.h:21,
                 from overworld/../overworld/../core/editor.h:22,
                 from overworld/../overworld/world_editor.h:19,
                 from overworld/world_manager.cpp:21:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-world_player.o
In file included from overworld/../video/../video/../video/gl_surface.h:23:0,
                 from overworld/../video/../video/img_manager.h:22,
                 from overworld/../video/font.h:20,
                 from overworld/world_player.cpp:21:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-world_sprite_manager.o
  CXX    smc-world_waypoint.o
In file included from overworld/../video/gl_surface.h:23:0,
                 from overworld/world_waypoint.cpp:25:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-preferences.o
  CXX    smc-savegame.o
  CXX    smc-animation.o
In file included from video/../video/gl_surface.h:23:0,
                 from video/animation.cpp:19:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-font.o
In file included from video/../video/../video/../video/gl_surface.h:23:0,
                 from video/../video/../video/img_manager.h:22,
                 from video/../video/font.h:20,
                 from video/font.cpp:16:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-gl_surface.o
  CXX    smc-img_manager.o
In file included from video/../video/../video/gl_surface.h:23:0,
                 from video/../video/img_manager.h:22,
                 from video/img_manager.cpp:16:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-img_settings.o
  CXX    smc-renderer.o
In file included from video/renderer.cpp:21:0:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
  CXX    smc-video.o
In file included from video/../video/../video/../video/gl_surface.h:23:0,
                 from video/../video/../video/img_manager.h:22,
                 from video/../video/font.h:20,
                 from video/video.cpp:20:
/usr/include/SDL/SDL_opengl.h:116:0: warning: "GL_GLEXT_VERSION" redefined [enabled by default]
/usr/include/GL/glext.h:34:0: note: this is the location of the previous definition
video/video.cpp: In member function ‘SDL_Surface* SMC::cVideo::Convert_To_Final_Software_Image(SDL_Surface*) const’:
video/video.cpp:1289:24: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
video/video.cpp:1289:48: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
video/video.cpp: In member function ‘SMC::cGL_Surface* SMC::cVideo::Create_Texture(SDL_Surface*, bool, unsigned int, unsigned int) const’:
video/video.cpp:1356:22: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
video/video.cpp:1356:47: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
  CXXLD  smc
/usr/bin/ld: smc-editor.o: undefined reference to symbol 'boost::system::system_category()'
/usr/bin/ld: note: 'boost::system::system_category()' is defined in DSO /usr/lib/libboost_system.so.1.46.1 so try adding it to the linker command line
/usr/lib/libboost_system.so.1.46.1: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [smc] Error 1
make[2]: Leaving directory `/home/ubu/smc-20120222.orig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubu/smc-20120222.orig'
make: *** [all] Error 2

```

I've tried linking libboost per this thread [http://ubuntuforums.org/showthread.php?t=1872012](http://ubuntuforums.org/showthread.php?t=1872012)
```
./configure LDFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so.1.46.1"  BOOST_LIBS="-L/usr/lib/libboost_system.so" CXXFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so.1.46.1" CFLAGS="-lboost_filesystem -lboost_thread -lboost_system -L/usr/lib/libboost_system.so.1.46.1"
```
 but it still errors out with this
```
make  all-recursive
make[1]: Entering directory `/home/ubu/smc-20120222.orig'
Making all in src
make[2]: Entering directory `/home/ubu/smc-20120222.orig/src'
  CXXLD  smc
/usr/bin/ld: smc-editor.o: undefined reference to symbol 'boost::system::system_category()'
/usr/bin/ld: note: 'boost::system::system_category()' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib/libboost_system.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../../lib/libboost_system.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [smc] Error 1
make[2]: Leaving directory `/home/ubu/smc-20120222.orig/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubu/smc-20120222.orig'
make: *** [all] Error 2

```
So I gave up trying to compile my own and I tried installing the amd64.deb files of the game, data, and music from [https://launchpad.net/ubuntu/+source/smc](https://launchpad.net/ubuntu/+source/smc)
BUT my screen flashes black and then returns to the desktop. I ran the smc command from the desktop to see the error and this is what it says
```
Initialization: Exception raised: boost::filesystem::directory_iterator::construct: No such file or directory: "/usr/share/games/smc/campaign"
```

Please help....

---

### Post by dannyboy79 on 2013-11-04
bump

---

