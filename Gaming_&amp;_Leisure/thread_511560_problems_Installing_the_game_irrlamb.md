---
title: "problems Installing the game irrlamb"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by PsyWolf on 2007-07-27
I used this [official howto]("http://code.google.com/p/irrlamb/wiki/LinuxInstall")

when i try to compile with the scons command i get this

wolf@Tim:~/irrlamb$ sudo scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/menu.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/menu.cpp
g++ -o src/main.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/main.cpp
g++ -o src/viewreplay.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/viewreplay.cpp
g++ -o src/play.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/play.cpp
g++ -o src/tinyxml/tinystr.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/tinyxml/tinystr.cpp
g++ -o src/tinyxml/tinyxmlparser.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/tinyxml/tinyxmlparser.cpp
g++ -o src/tinyxml/tinyxml.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/tinyxml/tinyxml.cpp
g++ -o src/tinyxml/tinyxmlerror.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/tinyxml/tinyxmlerror.cpp
g++ -o src/objects/terrain.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/terrain.cpp
g++ -o src/objects/box.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/box.cpp
g++ -o src/objects/sphere.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/sphere.cpp
g++ -o src/objects/water.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/water.cpp
g++ -o src/objects/orb.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/orb.cpp
g++ -o src/objects/mesh.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/mesh.cpp
g++ -o src/objects/default.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/default.cpp
g++ -o src/objects/object.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/object.cpp
g++ -o src/objects/basicjoint.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/basicjoint.cpp
g++ -o src/objects/zone.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/zone.cpp
g++ -o src/objects/player.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/player.cpp
g++ -o src/objects/rigidbody.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/rigidbody.cpp
g++ -o src/objects/scene.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/objects/scene.cpp
g++ -o src/engine/audio.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/audio.cpp
g++ -o src/engine/interface.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/interface.cpp
g++ -o src/engine/campaign.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/campaign.cpp
g++ -o src/engine/replay.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/replay.cpp
g++ -o src/engine/physics.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/physics.cpp
g++ -o src/engine/camera.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/camera.cpp
g++ -o src/engine/game.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/game.cpp
g++ -o src/engine/config.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/config.cpp
g++ -o src/engine/globals.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/globals.cpp
g++ -o src/engine/objectmanager.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/objectmanager.cpp
g++ -o src/engine/save.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/save.cpp
g++ -o src/engine/graphics.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/graphics.cpp
g++ -o src/engine/level.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/level.cpp
g++ -o src/engine/input.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/input.cpp
g++ -o src/engine/scripting.o -c -O3 -DNDEBUG -Ilibraries/include -Ilibraries/include/bullet -I/usr/include/lua5.1 src/engine/scripting.cpp
g++ -o irrlamb src/menu.o src/main.o src/viewreplay.o src/play.o src/tinyxml/tinystr.o src/tinyxml/tinyxmlparser.o src/tinyxml/tinyxml.o src/tinyxml/tinyxmlerror.o src/objects/terrain.o src/objects/box.o src/objects/sphere.o src/objects/water.o src/objects/orb.o src/objects/mesh.o src/objects/default.o src/objects/object.o src/objects/basicjoint.o src/objects/zone.o src/objects/player.o src/objects/rigidbody.o src/objects/scene.o src/engine/audio.o src/engine/interface.o src/engine/campaign.o src/engine/replay.o src/engine/physics.o src/engine/camera.o src/engine/game.o src/engine/config.o src/engine/globals.o src/engine/objectmanager.o src/engine/save.o src/engine/graphics.o src/engine/level.o src/engine/input.o src/engine/scripting.o -Llibraries/lib -lGL -lGLU -lIrrlicht -lXxf86vm -lXext -lX11 -lbulletdynamics -lbulletcollision -lbulletmath -laudiere -lboost_filesystem -llua5.1
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
scons: *** [irrlamb] Error 1
scons: building terminated because of errors.

---

### Post by DoktorSeven on 2007-07-28
Do you have direct rendering/GL installed? 

(**glxinfo | grep direct** returns "direct rendering: Yes")

If so, what does 

**ls -al /usr/lib/libGL***

return?  I've seen it where there was no /usr/lib/libGL.so but there was a libGL.so.1, so if nothing else you could try

**sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so**

---

### Post by hikaricore on 2007-07-28
If you're running Feisty or above, GetDeb.net has a package install for it: [http://www.getdeb.net/app.php?name=Irrlamb](http://www.getdeb.net/app.php?name=Irrlamb)

---

### Post by PsyWolf on 2007-07-28
the packages worked.  I don't know how I missed that.

---

