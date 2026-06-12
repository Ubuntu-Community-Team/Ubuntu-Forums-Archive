---
title: "Alien Arena 2008 released!"
date: 2008-03-06
forum: Gaming &amp; Leisure
---

### Post by Irritant on 2008-03-06
COR Entertainment, LLC announces the release of Alien Arena 2008, a freeware, opensourced FPS.

This game is the followup to the critically acclaimed( [http://www.linux.com/feature/119775](http://www.linux.com/feature/119775) ) Alien Arena 2007, and features nearly all new game media, gameplay improvements, and a client that has been signifigantly upgraded for improved visual effects as well as major optimizations that greatly improve the fluidity and performance.

Alien Arena 2008 also offers a change to it's overall theme, moving towards a slightler darker, more serious tone, while still retaining a good bit of it's retro style, creating an interesting marriage between classic and modern sci-fi. This resulted in completely new player models, many new weapon models and textures, and seventeen new levels.

There are major improvements in weapon effects, per-pixel lighting, texture resolution, and resource usage, as well as the addition of a cross platform server browser, FUSE. Weapons have been tweaked for better balance, and movement has been enhanced with the addition of dodging abilities. Alien Arena 2008 will run on Windows and Linux, and the OSX/Mac port will be released in one week. 

To download the game, see new screenshots and videos, please visit [http://red.planetarena.org](http://red.planetarena.org)

---

### Post by Irritant on 2008-03-07
Should also mention if you have problems or question regarding this release - please visit the forums or join #alienarena@efnet.org, we have a friendly community that is always willing to help(and frag) you :)

---

### Post by CaptainCabinet on 2008-03-07
This is actually news I've been waiting for! :)
Thanks for posting this.

---

### Post by irrdev on 2008-03-07
Great news! Thanks for the announcement!

---

### Post by GSZX1337 on 2008-03-07
Cool, I've been looking for a new game to play in Linux. :)
So, is this like going from UT99 to UT2K4, two different games, or is it like going from Nexuiz 2.3 to 2.4?

---

### Post by Irritant on 2008-03-07
I'd say more akin to going from UT2k3 to UT2k4.  It's a similar game, with similar, but tweaked gameplay, but alot of replaced/new content, and only keeping the best things from previous release.  The major gameplay changes were the addition of dodging, and weapon balance.  However visually, the game is pretty different than past releases.  All player models are new, most maps are new, weapons have new looks, and effects in most cases.  The renderer also got alot of optimizations as well as some improvements.  For example, bumpmapping in 6.10 was just static, but in 7.0 it's real-time.  

Also the maps have been designed with alot more gameplay ideas in mind.  For example, the first map in the list, dm-dismal was designed specifically for large FFA games, and for new players to have a map that was easy to get around in.  Maps like Dm-Aquous and Dm-turbo are specifically geared towards 1v1 play.  Overall there is alot of variety in the dm maps, visually as well as gameplay wise.

---

### Post by babwe on 2008-03-07
I am running Ubuntugamers
pls advice me howto install Alien Arena 2008 release 
thanks in advance

---

### Post by Irritant on 2008-03-07
There are a couple of ways - 

First you can simply download the .zip of the latest version and unzip in your games directory.

Or you can use SVN and grab it from svn://svn.icculus.org/alienarena/trunk

I'm not sure, but maybe ubuntu also has a way to use a apt-get or similar way to install some games.

---

### Post by Melcar on 2008-03-07
Looks awesome, but problem is, I can't run it.  Got the zip file, extracted the alienarena2008 folder, and tried to run the crx executable, but I keep getting this:


```
principe@magicbox:~/.alienarena2008$ ./crx
./crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

```

Edit:  Yes, I have that libxxf86 thing installed.

---

### Post by wingnux on 2008-03-07
Are you running the 64bit version of Ubuntu?

---

### Post by Crafty Kisses on 2008-03-07
Nice!

---

### Post by Melcar on 2008-03-07
> **wingnux said:**
> Are you running the 64bit version of Ubuntu?

Yes.  Don't tell me it doesn't work with 64bit :-s.  I was reading some of the threads from their forums, and it seems that it's a naming thing with the file in question.  The one I find with Synaptic is named slightly different than the one crx is looking for.

---

### Post by Brebs on 2008-03-07
alienarena2008 works fine on 64-bit. Take a look through my [Arch pkgbuild](http://aur.archlinux.org/packages/alienarena/alienarena/PKGBUILD) for hints. Note that I compile it using this pkgbuild "script". Note its mention of "lib64".

What does this show:
```
find /usr/lib* -name libXxf86dga.so.1
```

---

### Post by Melcar on 2008-03-07
> **Brebs said:**
> alienarena2008 works fine on 64-bit. Take a look through my [Arch pkgbuild](http://aur.archlinux.org/packages/alienarena/alienarena/PKGBUILD) for hints. Note that I compile it using this pkgbuild "script". Note its mention of "lib64".

What does this show:
```
find /usr/lib* -name libXxf86dga.so.1
```



```
principe@magicbox:~$ find /usr/lib* -name libXxf86dga.so.1
/usr/lib/libXxf86dga.so.1
principe@magicbox:~$ 

```

Maybe the game is looking for the lib in the wrong place?

---

### Post by Brebs on 2008-03-08
Aha, I can kinda replicate this problem with the executables that are in alienarena2008-linux20080227.zip
```
$ ./crx.sdl 
./crx.sdl: error while loading shared libraries: libXxf86dga.so.1: wrong ELF class: ELFCLASS64
```
The problem is, they're 32-bit executables, and 64-bit executables aren't included. I'm using 64-bit archlinux, which isn't multib.

I'm not sure whether you can run it by installing more 32-bit packages, or if you'll need to recompile the game (if so, see my pkgbuild).

---

### Post by emonkey on 2008-03-08
Please vote on brainstorm to get v7.0 (2008) into hard and gutsy-backports. :)
[http://brainstorm.ubuntu.com/idea/3876/](http://brainstorm.ubuntu.com/idea/3876/)

[[IMG]http://brainstorm.ubuntu.com/idea/3876/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3876/)

---

### Post by Perfect Storm on 2008-03-08
For those who are on Ubuntu 64-bit - [http://gaming.gwos.org/doku.php/guides:64bit:alien_arena](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena)

Irritant, when does Alien Arena support 64-bit (well without the 32-bit layer?)?

---

### Post by firedevilbg on 2008-03-08
It sounds like very good game to me... I will test it... 10x... :guitar:

---

### Post by Brebs on 2008-03-08
Recompiling for 64-bit is easy:
```
# Based on http://aur.archlinux.org/packages.php?ID=14398
mkdir -p $HOME/temp/alienarena
cd $HOME/temp/alienarena
wget http://icculus.org/alienarena/Files/alienarena2008-linux20080227.zip
unzip alienarena2008-linux20080227.zip
cd alienarena2008
mv "data1/scripts/maps/tca-titan2k8 .rscript" data1/scripts/maps/tca-titan2k8.rscript
rm -f {arena,data1}/game.so crx{,.sdl} crded
cd source
make
cd ..
cp -f source/release/game.so arena/game.so
cp -f source/release/cr* .
./crx
```

---

### Post by Melcar on 2008-03-08
I get errors when executing the make command.  A bunch of GL_ type errors, finishing off with an "Error 2" message.

Last few lines of output:
```

client/cl_fx.c:2426: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_LaserBlast’:
client/cl_fx.c:2481: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2482: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_RedBlasterBeam’:
client/cl_fx.c:2560: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2561: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BubbleTrail’:
client/cl_fx.c:2644: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:2645: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BFGExplosionParticles’:
client/cl_fx.c:2686: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:2687: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_TeleportParticles’:
client/cl_fx.c:2737: error: ‘GL_ONE’ undeclared (first use in this function)
make[1]: *** [release/client/cl_fx.o] Error 1
make[1]: Leaving directory `/home/principe/Games/alienarena2008/source'
make: *** [build-release] Error 2

```

---

### Post by Brebs on 2008-03-08
You need dependencies installed:
'curl' 'libgl' 'libjpeg' 'libxxf86dga' 'libxxf86vm' 'mesa' 'sdl' 'unzip'

Whatever they're called in your distro ;)

It's better to show the *first* error message, rather than the last.

Edit: Here's the list of dependency packages for Ubuntu:  mesa-common-dev libsdl1.2-dev curl libcurl4-openssl-dev libcurl3

---

### Post by forrestcupp on 2008-03-08
Does this game have bots for single player game play, or is it online only?

---

### Post by Perfect Storm on 2008-03-08
> **forrestcupp said:**
> Does this game have bots for single player game play, or is it online only?

Yes, there are bots for single player.

---

### Post by Irritant on 2008-03-08
Yeah there are also bots on servers, most servers have a "botkick" set so that if a few people join, it automatically kicks the bots out.

Also one somewhat important change for AA2k8 is the ability to dodge by quickly pressing your left or right keys in succession.  You cannot dodge while moving forward, though that might get changed in the next release.

---

### Post by Chame_Wizard on 2008-03-08
```
chrimbo@JMWF:~$ chmod +x ~/.Games/AlienArena-launch.sh
chmod: cannot access `/home/chrimbo/.Games/AlienArena-launch.sh': No such file or directory

```](*,):frown:

have also  extracted the zip on the Desktop,give me headache.

---

### Post by Melcar on 2008-03-08
> **Brebs said:**
> You need dependencies installed:
'curl' 'libgl' 'libjpeg' 'libxxf86dga' 'libxxf86vm' 'mesa' 'sdl' 'unzip'

Whatever they're called in your distro ;)

It's better to show the *first* error message, rather than the last.

Have all those things installed.  This is the entire output after the make command:
```

principe@magicbox:~/Games/alienarena2008/source$ make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8"
make[1]: Entering directory `/home/principe/Games/alienarena2008/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_ai.o -c game/acesrc/acebot_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_cmds.o -c game/acesrc/acebot_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_compress.o -c game/acesrc/acebot_compress.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_items.o -c game/acesrc/acebot_items.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_movement.o -c game/acesrc/acebot_movement.c
game/acesrc/acebot_movement.c: In function ‘ACEMV_Wander’:
game/acesrc/acebot_movement.c:673: warning: the address of ‘M_CheckBottom’, will always evaluate as ‘true’
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_nodes.o -c game/acesrc/acebot_nodes.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_spawn.o -c game/acesrc/acebot_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/c_cam.o -c game/c_cam.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/cow.o -c game/cow.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -fPIC -o release/game/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_ai.o -c game/g_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_chase.o -c game/g_chase.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_cmds.o -c game/g_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_combat.o -c game/g_combat.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_ctf.o -c game/g_ctf.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_deathball.o -c game/g_deathball.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_func.o -c game/g_func.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_items.o -c game/g_items.c
game/g_items.c:1097: warning: initialization from incompatible pointer type
game/g_items.c:1120: warning: initialization from incompatible pointer type
game/g_items.c:1143: warning: initialization from incompatible pointer type
game/g_items.c:1165: warning: initialization from incompatible pointer type
game/g_items.c:1188: warning: initialization from incompatible pointer type
game/g_items.c:1211: warning: initialization from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_main.o -c game/g_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_misc.o -c game/g_misc.c
game/g_misc.c:1494:2: warning: no newline at end of file
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_monster.o -c game/g_monster.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_phys.o -c game/g_phys.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_save.o -c game/g_save.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_spawn.o -c game/g_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_svcmds.o -c game/g_svcmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_target.o -c game/g_target.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_trigger.o -c game/g_trigger.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_utils.o -c game/g_utils.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_weapon.o -c game/g_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_vehicles.o -c game/g_vehicles.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/m_move.o -c game/m_move.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_client.o -c game/p_client.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_hud.o -c game/p_hud.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_light.o -c game/p_light.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_trail.o -c game/p_trail.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_view.o -c game/p_view.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_weapon.o -c game/p_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -shared -o release/game.so release/game/acebot_ai.o release/game/acebot_cmds.o release/game/acebot_compress.o release/game/acebot_items.o release/game/acebot_movement.o release/game/acebot_nodes.o release/game/acebot_spawn.o release/game/c_cam.o release/game/cow.o release/game/q_shared.o release/game/g_ai.o release/game/g_chase.o release/game/g_cmds.o release/game/g_combat.o release/game/g_ctf.o release/game/g_deathball.o release/game/g_func.o release/game/g_items.o release/game/g_main.o release/game/g_misc.o release/game/g_monster.o release/game/g_phys.o release/game/g_save.o release/game/g_spawn.o release/game/g_svcmds.o release/game/g_target.o release/game/g_trigger.o release/game/g_utils.o release/game/g_weapon.o release/game/g_vehicles.o release/game/m_move.o release/game/p_client.o release/game/p_hud.o release/game/p_light.o release/game/p_trail.o release/game/p_view.o release/game/p_weapon.o
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_ai.o -c game/acesrc/acebot_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_cmds.o -c game/acesrc/acebot_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_compress.o -c game/acesrc/acebot_compress.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_items.o -c game/acesrc/acebot_items.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_movement.o -c game/acesrc/acebot_movement.c
game/acesrc/acebot_movement.c: In function ‘ACEMV_Wander’:
game/acesrc/acebot_movement.c:673: warning: the address of ‘M_CheckBottom’, will always evaluate as ‘true’
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_nodes.o -c game/acesrc/acebot_nodes.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_spawn.o -c game/acesrc/acebot_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -fPIC -o release/arena/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/c_cam.o -c game/c_cam.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/cow.o -c game/cow.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_ai.o -c game/g_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_chase.o -c game/g_chase.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_cmds.o -c game/g_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_combat.o -c game/g_combat.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_ctf.o -c game/g_ctf.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_deathball.o -c game/g_deathball.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_func.o -c game/g_func.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_items.o -c game/g_items.c
game/g_items.c:1097: warning: initialization from incompatible pointer type
game/g_items.c:1120: warning: initialization from incompatible pointer type
game/g_items.c:1143: warning: initialization from incompatible pointer type
game/g_items.c:1165: warning: initialization from incompatible pointer type
game/g_items.c:1188: warning: initialization from incompatible pointer type
game/g_items.c:1211: warning: initialization from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_main.o -c game/g_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_misc.o -c game/g_misc.c
game/g_misc.c:1494:2: warning: no newline at end of file
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_monster.o -c game/g_monster.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_phys.o -c game/g_phys.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_save.o -c game/g_save.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_spawn.o -c game/g_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_svcmds.o -c game/g_svcmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_target.o -c game/g_target.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_trigger.o -c game/g_trigger.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_utils.o -c game/g_utils.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_vehicles.o -c game/g_vehicles.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_weapon.o -c game/g_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/m_move.o -c game/m_move.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_client.o -c game/p_client.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_hud.o -c game/p_hud.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_light.o -c game/p_light.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_trail.o -c game/p_trail.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_view.o -c game/p_view.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_weapon.o -c game/p_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -shared -o release/arena/game.so release/arena/acebot_ai.o release/arena/acebot_cmds.o release/arena/acebot_compress.o release/arena/acebot_items.o release/arena/acebot_movement.o release/arena/acebot_nodes.o release/arena/acebot_spawn.o release/arena/q_shared.o release/arena/c_cam.o release/arena/cow.o release/arena/g_ai.o release/arena/g_chase.o release/arena/g_cmds.o release/arena/g_combat.o release/arena/g_ctf.o release/arena/g_deathball.o release/arena/g_func.o release/arena/g_items.o release/arena/g_main.o release/arena/g_misc.o release/arena/g_monster.o release/arena/g_phys.o release/arena/g_save.o release/arena/g_spawn.o release/arena/g_svcmds.o release/arena/g_target.o release/arena/g_trigger.o release/arena/g_utils.o release/arena/g_vehicles.o release/arena/g_weapon.o release/arena/m_move.o release/arena/p_client.o release/arena/p_hud.o release/arena/p_light.o release/arena/p_trail.o release/arena/p_view.o release/arena/p_weapon.o
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cmd.o -c qcommon/cmd.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cmodel.o -c qcommon/cmodel.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/common.o -c qcommon/common.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/crc.o -c qcommon/crc.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cvar.o -c qcommon/cvar.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/files.o -c qcommon/files.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/mdfour.o -c qcommon/mdfour.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/net_chan.o -c qcommon/net_chan.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_ccmds.o -c server/sv_ccmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_ents.o -c server/sv_ents.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_game.o -c server/sv_game.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_init.o -c server/sv_init.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_main.o -c server/sv_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_send.o -c server/sv_send.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_user.o -c server/sv_user.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_world.o -c server/sv_world.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/q_shunix.o -c unix/q_shunix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sys_unix.o -c unix/sys_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/glob.o -c unix/glob.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/net_udp.o -c unix/net_udp.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -DDEDICATED_ONLY -o release/ded/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/pmove.o -c qcommon/pmove.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cl_null.o -c null/cl_null.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/crded release/ded/cmd.o release/ded/cmodel.o release/ded/common.o release/ded/crc.o release/ded/cvar.o release/ded/files.o release/ded/mdfour.o release/ded/net_chan.o release/ded/sv_ccmds.o release/ded/sv_ents.o release/ded/sv_game.o release/ded/sv_init.o release/ded/sv_main.o release/ded/sv_send.o release/ded/sv_user.o release/ded/sv_world.o release/ded/q_shunix.o release/ded/sys_unix.o release/ded/glob.o release/ded/net_udp.o release/ded/q_shared.o release/ded/pmove.o release/ded/cl_null.o -lm -ldl
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_cin.o -c client/cl_cin.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_ents.o -c client/cl_ents.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_fx.o -c client/cl_fx.c
In file included from client/cl_fx.c:24:
client/../ref_gl/qgl.h:31:19: error: GL/gl.h: No such file or directory
client/../ref_gl/qgl.h:35:20: error: GL/glx.h: No such file or directory
In file included from client/cl_fx.c:24:
client/../ref_gl/qgl.h:45: error: expected ‘)’ before ‘op’
client/../ref_gl/qgl.h:46: error: expected ‘)’ before ‘func’
client/../ref_gl/qgl.h:47: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:47: error: expected ‘)’ before ‘n’
client/../ref_gl/qgl.h:48: error: expected ‘)’ before ‘i’
client/../ref_gl/qgl.h:49: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:50: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:51: error: expected ‘)’ before ‘width’
client/../ref_gl/qgl.h:52: error: expected ‘)’ before ‘sfactor’
client/../ref_gl/qgl.h:53: error: expected ‘)’ before ‘list’
client/../ref_gl/qgl.h:54: error: expected ‘)’ before ‘n’
client/../ref_gl/qgl.h:55: error: expected ‘)’ before ‘mask’
client/../ref_gl/qgl.h:56: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:57: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:58: error: expected ‘)’ before ‘depth’
client/../ref_gl/qgl.h:59: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:60: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:61: error: expected ‘)’ before ‘plane’
client/../ref_gl/qgl.h:62: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:63: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:64: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:65: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:66: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:67: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:68: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:69: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:70: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:71: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:72: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:73: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:74: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:75: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:76: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:77: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:78: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:79: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:80: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:81: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:82: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:83: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:84: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:85: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:86: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:87: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:88: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:89: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:90: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:91: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:92: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:93: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:94: error: expected ‘)’ before ‘red’
client/../ref_gl/qgl.h:95: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:96: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:97: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:98: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:99: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:100: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:101: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:102: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:103: error: expected ‘)’ before ‘list’
client/../ref_gl/qgl.h:104: error: expected ‘)’ before ‘n’
client/../ref_gl/qgl.h:105: error: expected ‘)’ before ‘func’
client/../ref_gl/qgl.h:106: error: expected ‘)’ before ‘flag’
client/../ref_gl/qgl.h:107: error: expected ‘)’ before ‘zNear’
client/../ref_gl/qgl.h:108: error: expected ‘)’ before ‘cap’
client/../ref_gl/qgl.h:109: error: expected ‘)’ before ‘array’
client/../ref_gl/qgl.h:110: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:111: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:112: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:113: error: expected ‘)’ before ‘width’
client/../ref_gl/qgl.h:114: error: expected ‘)’ before ‘flag’
client/../ref_gl/qgl.h:115: error: expected ‘)’ before ‘stride’
client/../ref_gl/qgl.h:116: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:117: error: expected ‘)’ before ‘cap’
client/../ref_gl/qgl.h:118: error: expected ‘)’ before ‘array’
client/../ref_gl/qgl.h:121: error: expected ‘)’ before ‘u’
client/../ref_gl/qgl.h:122: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:123: error: expected ‘)’ before ‘u’
client/../ref_gl/qgl.h:124: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:125: error: expected ‘)’ before ‘u’
client/../ref_gl/qgl.h:126: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:127: error: expected ‘)’ before ‘u’
client/../ref_gl/qgl.h:128: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:129: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:130: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:131: error: expected ‘)’ before ‘i’
client/../ref_gl/qgl.h:132: error: expected ‘)’ before ‘i’
client/../ref_gl/qgl.h:133: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:136: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:137: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:138: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:139: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:140: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:141: error: expected ‘)’ before ‘left’
client/../ref_gl/qgl.h:142: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:142: error: expected ‘)’ before ‘range’
client/../ref_gl/qgl.h:143: error: expected ‘)’ before ‘n’
client/../ref_gl/qgl.h:144: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:145: error: expected ‘)’ before ‘plane’
client/../ref_gl/qgl.h:146: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:147: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:147: error: ‘GLenum’ declared as function returning a function
client/../ref_gl/qgl.h:148: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:149: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:150: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:151: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:152: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:153: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:154: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:155: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:156: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:157: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:158: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:159: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:160: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:161: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
client/../ref_gl/qgl.h:163: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:164: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:165: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:166: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:167: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:168: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:169: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:170: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:171: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:172: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:173: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:174: error: expected ‘)’ before ‘mask’
client/../ref_gl/qgl.h:175: error: expected ‘)’ before ‘type’
client/../ref_gl/qgl.h:176: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:177: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:178: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:179: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:180: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:181: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:182: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:183: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:184: error: expected ‘)’ before ‘c’
client/../ref_gl/qgl.h:185: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:187: error: expected ‘)’ before ‘format’
client/../ref_gl/qgl.h:188: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:188: error: expected ‘)’ before ‘cap’
client/../ref_gl/qgl.h:189: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:189: error: expected ‘)’ before ‘list’
client/../ref_gl/qgl.h:190: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:190: error: expected ‘)’ before ‘texture’
client/../ref_gl/qgl.h:191: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:192: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:193: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:194: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:195: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:196: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:197: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:198: error: expected ‘)’ before ‘light’
client/../ref_gl/qgl.h:199: error: expected ‘)’ before ‘factor’
client/../ref_gl/qgl.h:200: error: expected ‘)’ before ‘width’
client/../ref_gl/qgl.h:201: error: expected ‘)’ before ‘base’
client/../ref_gl/qgl.h:203: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:204: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:205: error: expected ‘)’ before ‘name’
client/../ref_gl/qgl.h:206: error: expected ‘)’ before ‘opcode’
client/../ref_gl/qgl.h:207: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:208: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:209: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:210: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:211: error: expected ‘)’ before ‘un’
client/../ref_gl/qgl.h:212: error: expected ‘)’ before ‘un’
client/../ref_gl/qgl.h:213: error: expected ‘)’ before ‘un’
client/../ref_gl/qgl.h:214: error: expected ‘)’ before ‘un’
client/../ref_gl/qgl.h:215: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:216: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:217: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:218: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:219: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:220: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:221: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:222: error: expected ‘)’ before ‘list’
client/../ref_gl/qgl.h:223: error: expected ‘)’ before ‘nx’
client/../ref_gl/qgl.h:224: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:225: error: expected ‘)’ before ‘nx’
client/../ref_gl/qgl.h:226: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:227: error: expected ‘)’ before ‘nx’
client/../ref_gl/qgl.h:228: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:229: error: expected ‘)’ before ‘nx’
client/../ref_gl/qgl.h:230: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:231: error: expected ‘)’ before ‘nx’
client/../ref_gl/qgl.h:232: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:233: error: expected ‘)’ before ‘type’
client/../ref_gl/qgl.h:234: error: expected ‘)’ before ‘left’
client/../ref_gl/qgl.h:235: error: expected ‘)’ before ‘token’
client/../ref_gl/qgl.h:236: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:237: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:238: error: expected ‘)’ before ‘map’
client/../ref_gl/qgl.h:239: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:240: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:241: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:242: error: expected ‘)’ before ‘pname’
client/../ref_gl/qgl.h:243: error: expected ‘)’ before ‘xfactor’
client/../ref_gl/qgl.h:244: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:245: error: expected ‘)’ before ‘face’
client/../ref_gl/qgl.h:246: error: expected ‘)’ before ‘factor’
client/../ref_gl/qgl.h:247: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:252: error: expected ‘)’ before ‘n’
client/../ref_gl/qgl.h:253: error: expected ‘)’ before ‘mask’
client/../ref_gl/qgl.h:254: error: expected ‘)’ before ‘mask’
client/../ref_gl/qgl.h:256: error: expected ‘)’ before ‘name’
client/../ref_gl/qgl.h:257: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:258: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:259: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:260: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:261: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:262: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:263: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:264: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:265: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:266: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:267: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:268: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:269: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:270: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:271: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:272: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:273: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:274: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:275: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:276: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:277: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:278: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:279: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:280: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:281: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:282: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:283: error: expected ‘)’ before ‘x1’
client/../ref_gl/qgl.h:284: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:285: error: expected ‘)’ before ‘x1’
client/../ref_gl/qgl.h:286: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:287: error: expected ‘)’ before ‘x1’
client/../ref_gl/qgl.h:288: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:289: error: expected ‘)’ before ‘x1’
client/../ref_gl/qgl.h:290: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:291: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:291: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:292: error: expected ‘)’ before ‘angle’
client/../ref_gl/qgl.h:293: error: expected ‘)’ before ‘angle’
client/../ref_gl/qgl.h:294: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:295: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:296: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:297: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:298: error: expected ‘)’ before ‘mode’
client/../ref_gl/qgl.h:299: error: expected ‘)’ before ‘func’
client/../ref_gl/qgl.h:300: error: expected ‘)’ before ‘mask’
client/../ref_gl/qgl.h:301: error: expected ‘)’ before ‘fail’
client/../ref_gl/qgl.h:302: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:303: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:304: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:305: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:306: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:307: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:308: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:309: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:310: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:311: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:312: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:313: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:314: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:315: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:316: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:317: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:318: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:319: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:320: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:321: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:322: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:323: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:324: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:325: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:326: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:327: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:328: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:329: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:330: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:331: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:332: error: expected ‘)’ before ‘s’
client/../ref_gl/qgl.h:333: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:334: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:335: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:336: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:337: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:338: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:339: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:340: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:341: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:342: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:343: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:344: error: expected ‘)’ before ‘coord’
client/../ref_gl/qgl.h:345: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:346: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:347: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:348: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:349: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:350: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:351: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:352: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:353: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:354: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:355: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:356: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:357: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:358: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:359: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:360: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:361: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:362: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:363: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:364: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:365: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:366: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:367: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:368: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:369: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:370: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:371: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:372: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:373: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:374: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:375: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:376: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:377: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:378: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:379: error: expected ‘)’ before ‘size’
client/../ref_gl/qgl.h:380: error: expected ‘)’ before ‘x’
client/../ref_gl/qgl.h:382: error: expected ‘)’ before ‘param’
client/../ref_gl/qgl.h:383: error: expected ‘)’ before ‘param’
client/../ref_gl/qgl.h:389: warning: parameter names (without types) in function declaration
client/../ref_gl/qgl.h:390: warning: parameter names (without types) in function declaration
client/../ref_gl/qgl.h:391: warning: parameter names (without types) in function declaration
client/../ref_gl/qgl.h:393: warning: parameter names (without types) in function declaration
client/../ref_gl/qgl.h:394: warning: parameter names (without types) in function declaration
client/../ref_gl/qgl.h:396: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:462: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:475: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
client/../ref_gl/qgl.h:476: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:476: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:477: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:478: error: expected declaration specifiers or ‘...’ before ‘*’ token
client/../ref_gl/qgl.h:478: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:479: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:480: error: expected ‘)’ before ‘*’ token
client/../ref_gl/qgl.h:483: error: expected ‘)’ before ‘target’
client/../ref_gl/qgl.h:572: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglGenProgramsARB’
client/../ref_gl/qgl.h:573: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglDeleteProgramsARB’
client/../ref_gl/qgl.h:574: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglBindProgramARB’
client/../ref_gl/qgl.h:575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglProgramStringARB’
client/../ref_gl/qgl.h:576: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglProgramEnvParameter4fARB’
client/../ref_gl/qgl.h:577: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qglProgramLocalParameter4fARB’
client/cl_fx.c: In function ‘CL_ParticleEffect’:
client/cl_fx.c:523: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:523: error: (Each undeclared identifier is reported only once
client/cl_fx.c:523: error: for each function it appears in.)
client/cl_fx.c:524: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:560: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BulletSparks’:
client/cl_fx.c:644: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:645: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_SplashEffect’:
client/cl_fx.c:684: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:685: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_ItemRespawnParticles’:
client/cl_fx.c:824: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:825: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_ExplosionParticles’:
client/cl_fx.c:875: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:876: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_MuzzleParticles’:
client/cl_fx.c:936: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:937: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlueMuzzleParticles’:
client/cl_fx.c:963: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:964: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_MuzzleFlashParticle’:
client/cl_fx.c:1026: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1027: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_SmartMuzzle’:
client/cl_fx.c:1059: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1060: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_Voltage’:
client/cl_fx.c:1095: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1096: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_Deathfield’:
client/cl_fx.c:1128: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1129: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_SayIcon’:
client/cl_fx.c:1169: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1170: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_DustParticles’:
client/cl_fx.c:1201: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1202: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BigTeleportParticles’:
client/cl_fx.c:1238: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1239: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_SmallHealthParticles’:
client/cl_fx.c:1274: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1275: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_MedHealthParticles’:
client/cl_fx.c:1307: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1308: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_LargeHealthParticles’:
client/cl_fx.c:1340: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1341: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlasterParticles’:
client/cl_fx.c:1381: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1382: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlasterBall’:
client/cl_fx.c:1435: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlueTeamLight’:
client/cl_fx.c:1495: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_RedTeamLight’:
client/cl_fx.c:1523: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_DiminishingTrail’:
client/cl_fx.c:1607: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1608: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_ShipExhaust’:
client/cl_fx.c:1731: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1732: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_RocketExhaust’:
client/cl_fx.c:1776: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1777: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BulletMarks’:
client/cl_fx.c:1821: error: ‘GL_ZERO’ undeclared (first use in this function)
client/cl_fx.c:1822: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BeamgunMark’:
client/cl_fx.c:1850: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1851: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlasterMark’:
client/cl_fx.c:1903: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1904: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_VaporizerMarks’:
client/cl_fx.c:1958: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:1959: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_DisruptorBeam’:
client/cl_fx.c:2047: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2048: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_LaserBeam’:
client/cl_fx.c:2124: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2125: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BlasterBeam’:
client/cl_fx.c:2211: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2212: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_VaporizerBeam’:
client/cl_fx.c:2291: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2292: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_NewLightning’:
client/cl_fx.c:2425: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:2426: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_LaserBlast’:
client/cl_fx.c:2481: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2482: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_RedBlasterBeam’:
client/cl_fx.c:2560: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c:2561: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BubbleTrail’:
client/cl_fx.c:2644: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:2645: error: ‘GL_ONE_MINUS_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_BFGExplosionParticles’:
client/cl_fx.c:2686: error: ‘GL_SRC_ALPHA’ undeclared (first use in this function)
client/cl_fx.c:2687: error: ‘GL_ONE’ undeclared (first use in this function)
client/cl_fx.c: In function ‘CL_TeleportParticles’:
client/cl_fx.c:2737: error: ‘GL_ONE’ undeclared (first use in this function)
make[1]: *** [release/client/cl_fx.o] Error 1
make[1]: Leaving directory `/home/principe/Games/alienarena2008/source'
make: *** [build-release] Error 2

```

---

### Post by Perfect Storm on 2008-03-09
> **Chame_Wizard said:**
> ```
chrimbo@JMWF:~$ chmod +x ~/.Games/AlienArena-launch.sh
chmod: cannot access `/home/chrimbo/.Games/AlienArena-launch.sh': No such file or directory

```](*,):frown:

have also  extracted the zip on the Desktop,give me headache.

Read the guide carefully - even the things that aren't in a code box.

I can see you have kubuntu, so you have to make some changes when it comes to the launcher part as the guide is written for/on Ubuntu (gnome).

---

### Post by Brebs on 2008-03-09
> **Melcar said:**
> client/../ref_gl/qgl.h:31:19: error: GL/gl.h: No such file or directory
client/../ref_gl/qgl.h:35:20: error: GL/glx.h: No such file or directory
```
$ pacman -Qo /usr/include/GL/gl.h 
/usr/include/GL/gl.h is owned by mesa 7.0.3rc1-1
```
Install mesa - whatever it's called in your distro.

---

### Post by Melcar on 2008-03-09
> **Brebs said:**
> ```
$ pacman -Qo /usr/include/GL/gl.h 
/usr/include/GL/gl.h is owned by mesa 7.0.3rc1-1
```
Install mesa - whatever it's called in your distro.



libgl1-mesa-dri
libgl1-mesa-glx

I have those installed already.

---

### Post by Brebs on 2008-03-09
You want [mesa-common-dev](http://packages.ubuntu.com/gutsy/all/mesa-common-dev/filelist).

Blame Debian and its ridiculous practice of splitting one package into many :)

---

### Post by Melcar on 2008-03-09
> **Brebs said:**
> You want [mesa-common-dev](http://packages.ubuntu.com/gutsy/all/mesa-common-dev/filelist).

Blame Debian and its ridiculous practice of splitting one package into many :)

Installed that one too, and still the same errors.  There is also another one, X something; will install that one and try compiling again.

---

### Post by Brebs on 2008-03-09
In Ubuntu, install [libsdl1.2-dev](http://packages.ubuntu.com/gutsy/libsdl1.2-dev)

---

### Post by Melcar on 2008-03-09
Got a different output, but it still ends in errors:


```
principe@magicbox:~/Games/alienarena2008/source$ make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8"
make[1]: Entering directory `/home/principe/Games/alienarena2008/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_ai.o -c game/acesrc/acebot_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_cmds.o -c game/acesrc/acebot_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_compress.o -c game/acesrc/acebot_compress.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_items.o -c game/acesrc/acebot_items.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_movement.o -c game/acesrc/acebot_movement.c
game/acesrc/acebot_movement.c: In function &#8216;ACEMV_Wander&#8217;:
game/acesrc/acebot_movement.c:673: warning: the address of &#8216;M_CheckBottom&#8217;, will always evaluate as &#8216;true&#8217;
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_nodes.o -c game/acesrc/acebot_nodes.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/acebot_spawn.o -c game/acesrc/acebot_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/c_cam.o -c game/c_cam.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/cow.o -c game/cow.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -fPIC -o release/game/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_ai.o -c game/g_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_chase.o -c game/g_chase.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_cmds.o -c game/g_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_combat.o -c game/g_combat.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_ctf.o -c game/g_ctf.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_deathball.o -c game/g_deathball.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_func.o -c game/g_func.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_items.o -c game/g_items.c
game/g_items.c:1097: warning: initialization from incompatible pointer type
game/g_items.c:1120: warning: initialization from incompatible pointer type
game/g_items.c:1143: warning: initialization from incompatible pointer type
game/g_items.c:1165: warning: initialization from incompatible pointer type
game/g_items.c:1188: warning: initialization from incompatible pointer type
game/g_items.c:1211: warning: initialization from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_main.o -c game/g_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_misc.o -c game/g_misc.c
game/g_misc.c:1494:2: warning: no newline at end of file
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_monster.o -c game/g_monster.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_phys.o -c game/g_phys.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_save.o -c game/g_save.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_spawn.o -c game/g_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_svcmds.o -c game/g_svcmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_target.o -c game/g_target.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_trigger.o -c game/g_trigger.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_utils.o -c game/g_utils.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_weapon.o -c game/g_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/g_vehicles.o -c game/g_vehicles.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/m_move.o -c game/m_move.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_client.o -c game/p_client.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_hud.o -c game/p_hud.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_light.o -c game/p_light.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_trail.o -c game/p_trail.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_view.o -c game/p_view.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/game/p_weapon.o -c game/p_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -shared -o release/game.so release/game/acebot_ai.o release/game/acebot_cmds.o release/game/acebot_compress.o release/game/acebot_items.o release/game/acebot_movement.o release/game/acebot_nodes.o release/game/acebot_spawn.o release/game/c_cam.o release/game/cow.o release/game/q_shared.o release/game/g_ai.o release/game/g_chase.o release/game/g_cmds.o release/game/g_combat.o release/game/g_ctf.o release/game/g_deathball.o release/game/g_func.o release/game/g_items.o release/game/g_main.o release/game/g_misc.o release/game/g_monster.o release/game/g_phys.o release/game/g_save.o release/game/g_spawn.o release/game/g_svcmds.o release/game/g_target.o release/game/g_trigger.o release/game/g_utils.o release/game/g_weapon.o release/game/g_vehicles.o release/game/m_move.o release/game/p_client.o release/game/p_hud.o release/game/p_light.o release/game/p_trail.o release/game/p_view.o release/game/p_weapon.o
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_ai.o -c game/acesrc/acebot_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_cmds.o -c game/acesrc/acebot_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_compress.o -c game/acesrc/acebot_compress.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_items.o -c game/acesrc/acebot_items.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_movement.o -c game/acesrc/acebot_movement.c
game/acesrc/acebot_movement.c: In function &#8216;ACEMV_Wander&#8217;:
game/acesrc/acebot_movement.c:673: warning: the address of &#8216;M_CheckBottom&#8217;, will always evaluate as &#8216;true&#8217;
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_nodes.o -c game/acesrc/acebot_nodes.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/acebot_spawn.o -c game/acesrc/acebot_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -fPIC -o release/arena/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/c_cam.o -c game/c_cam.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/cow.o -c game/cow.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_ai.o -c game/g_ai.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_chase.o -c game/g_chase.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_cmds.o -c game/g_cmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_combat.o -c game/g_combat.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_ctf.o -c game/g_ctf.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_deathball.o -c game/g_deathball.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_func.o -c game/g_func.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_items.o -c game/g_items.c
game/g_items.c:1097: warning: initialization from incompatible pointer type
game/g_items.c:1120: warning: initialization from incompatible pointer type
game/g_items.c:1143: warning: initialization from incompatible pointer type
game/g_items.c:1165: warning: initialization from incompatible pointer type
game/g_items.c:1188: warning: initialization from incompatible pointer type
game/g_items.c:1211: warning: initialization from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_main.o -c game/g_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_misc.o -c game/g_misc.c
game/g_misc.c:1494:2: warning: no newline at end of file
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_monster.o -c game/g_monster.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_phys.o -c game/g_phys.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_save.o -c game/g_save.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_spawn.o -c game/g_spawn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_svcmds.o -c game/g_svcmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_target.o -c game/g_target.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_trigger.o -c game/g_trigger.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_utils.o -c game/g_utils.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_vehicles.o -c game/g_vehicles.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/g_weapon.o -c game/g_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/m_move.o -c game/m_move.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_client.o -c game/p_client.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_hud.o -c game/p_hud.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_light.o -c game/p_light.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_trail.o -c game/p_trail.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_view.o -c game/p_view.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DARENA -fPIC -o release/arena/p_weapon.o -c game/p_weapon.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -shared -o release/arena/game.so release/arena/acebot_ai.o release/arena/acebot_cmds.o release/arena/acebot_compress.o release/arena/acebot_items.o release/arena/acebot_movement.o release/arena/acebot_nodes.o release/arena/acebot_spawn.o release/arena/q_shared.o release/arena/c_cam.o release/arena/cow.o release/arena/g_ai.o release/arena/g_chase.o release/arena/g_cmds.o release/arena/g_combat.o release/arena/g_ctf.o release/arena/g_deathball.o release/arena/g_func.o release/arena/g_items.o release/arena/g_main.o release/arena/g_misc.o release/arena/g_monster.o release/arena/g_phys.o release/arena/g_save.o release/arena/g_spawn.o release/arena/g_svcmds.o release/arena/g_target.o release/arena/g_trigger.o release/arena/g_utils.o release/arena/g_vehicles.o release/arena/g_weapon.o release/arena/m_move.o release/arena/p_client.o release/arena/p_hud.o release/arena/p_light.o release/arena/p_trail.o release/arena/p_view.o release/arena/p_weapon.o
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cmd.o -c qcommon/cmd.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cmodel.o -c qcommon/cmodel.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/common.o -c qcommon/common.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/crc.o -c qcommon/crc.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cvar.o -c qcommon/cvar.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/files.o -c qcommon/files.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/mdfour.o -c qcommon/mdfour.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/net_chan.o -c qcommon/net_chan.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_ccmds.o -c server/sv_ccmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_ents.o -c server/sv_ents.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_game.o -c server/sv_game.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_init.o -c server/sv_init.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_main.o -c server/sv_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_send.o -c server/sv_send.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_user.o -c server/sv_user.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sv_world.o -c server/sv_world.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/q_shunix.o -c unix/q_shunix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/sys_unix.o -c unix/sys_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/glob.o -c unix/glob.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/net_udp.o -c unix/net_udp.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -DDEDICATED_ONLY -o release/ded/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/pmove.o -c qcommon/pmove.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DDEDICATED_ONLY -o release/ded/cl_null.o -c null/cl_null.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/crded release/ded/cmd.o release/ded/cmodel.o release/ded/common.o release/ded/crc.o release/ded/cvar.o release/ded/files.o release/ded/mdfour.o release/ded/net_chan.o release/ded/sv_ccmds.o release/ded/sv_ents.o release/ded/sv_game.o release/ded/sv_init.o release/ded/sv_main.o release/ded/sv_send.o release/ded/sv_user.o release/ded/sv_world.o release/ded/q_shunix.o release/ded/sys_unix.o release/ded/glob.o release/ded/net_udp.o release/ded/q_shared.o release/ded/pmove.o release/ded/cl_null.o -lm -ldl
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_cin.o -c client/cl_cin.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_ents.o -c client/cl_ents.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_fx.o -c client/cl_fx.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_input.o -c client/cl_input.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_inv.o -c client/cl_inv.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_main.o -c client/cl_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_newfx.o -c client/cl_newfx.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_parse.o -c client/cl_parse.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_pred.o -c client/cl_pred.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_tent.o -c client/cl_tent.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_scrn.o -c client/cl_scrn.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_view.o -c client/cl_view.c
make[1]: curl-config: Command not found
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cl_http.o -c client/cl_http.c 
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/console.o -c client/console.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/keys.o -c client/keys.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/menu.o -c client/menu.c
client/menu.c: In function &#8216;Options_MenuInit&#8217;:
client/menu.c:2203: warning: assignment from incompatible pointer type
client/menu.c:2212: warning: assignment from incompatible pointer type
client/menu.c:2221: warning: assignment from incompatible pointer type
client/menu.c: In function &#8216;RulesChangeFunc&#8217;:
client/menu.c:3941: warning: assignment from incompatible pointer type
client/menu.c: In function &#8216;StartServer_MenuInit&#8217;:
client/menu.c:4143: warning: assignment from incompatible pointer type
client/menu.c: In function &#8216;ModelCallback&#8217;:
client/menu.c:5042: warning: assignment from incompatible pointer type
client/menu.c: In function &#8216;PlayerConfig_MenuInit&#8217;:
client/menu.c:5339: warning: assignment from incompatible pointer type
client/menu.c:5348: warning: assignment from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/snd_dma.o -c client/snd_dma.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/snd_mem.o -c client/snd_mem.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/snd_mix.o -c client/snd_mix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/qmenu.o -c client/qmenu.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cmd.o -c qcommon/cmd.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cmodel.o -c qcommon/cmodel.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/common.o -c qcommon/common.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/crc.o -c qcommon/crc.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/cvar.o -c qcommon/cvar.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/files.o -c qcommon/files.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/mdfour.o -c qcommon/mdfour.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/net_chan.o -c qcommon/net_chan.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_ccmds.o -c server/sv_ccmds.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_ents.o -c server/sv_ents.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_game.o -c server/sv_game.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_init.o -c server/sv_init.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_main.o -c server/sv_main.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_send.o -c server/sv_send.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_user.o -c server/sv_user.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sv_world.o -c server/sv_world.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -O -o release/client/q_shunix.o -c unix/q_shunix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/vid_menu.o -c client/vid_menu.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/vid_so.o -c unix/vid_so.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/sys_unix.o -c unix/sys_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -O -o release/client/rw_unix.o -c unix/rw_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/glob.o -c unix/glob.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/net_udp.o -c unix/net_udp.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -g -ggdb -o release/client/q_shared.o -c game/q_shared.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/pmove.o -c qcommon/pmove.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_bloom.o -c ref_gl/r_bloom.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_draw.o -c ref_gl/r_draw.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_image.o -c ref_gl/r_image.c
ref_gl/r_image.c: In function &#8216;jpeg_mem_src&#8217;:
ref_gl/r_image.c:597: warning: assignment from incompatible pointer type
ref_gl/r_image.c: In function &#8216;GL_InitImages&#8217;:
ref_gl/r_image.c:1851: warning: passing argument 2 of &#8216;FS_LoadFile&#8217; from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_light.o -c ref_gl/r_light.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_main.o -c ref_gl/r_main.c
ref_gl/r_main.c: In function &#8216;R_DrawEntitiesOnList&#8217;:
ref_gl/r_main.c:483: warning: assignment from incompatible pointer type
ref_gl/r_main.c:535: warning: assignment from incompatible pointer type
ref_gl/r_main.c: In function &#8216;R_Init&#8217;:
ref_gl/r_main.c:1776: warning: assignment from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_mesh.o -c ref_gl/r_mesh.c
ref_gl/r_mesh.c: In function &#8216;R_DrawAliasModel&#8217;:
ref_gl/r_mesh.c:1431: warning: assignment from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_misc.o -c ref_gl/r_misc.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_model.o -c ref_gl/r_model.c
ref_gl/r_model.c: In function &#8216;Mod_ForName&#8217;:
ref_gl/r_model.c:372: warning: assignment from incompatible pointer type
ref_gl/r_model.c:403: warning: passing argument 2 of &#8216;FS_LoadFile&#8217; from incompatible pointer type
ref_gl/r_model.c: In function &#8216;Mod_LoadAliasModel&#8217;:
ref_gl/r_model.c:1482: warning: assignment from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_refl.o -c ref_gl/r_refl.c
ref_gl/r_refl.c: In function &#8216;R_init_refl&#8217;:
ref_gl/r_refl.c:119: warning: passing argument 2 of &#8216;FS_LoadFile&#8217; from incompatible pointer type
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_math.o -c ref_gl/r_math.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_script.o -c ref_gl/r_script.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_surf.o -c ref_gl/r_surf.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_vlights.o -c ref_gl/r_vlights.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/r_warp.o -c ref_gl/r_warp.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/qgl_unix.o -c unix/qgl_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/client/snd_unix.o -c unix/snd_unix.c
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -DELF -x assembler-with-cpp -o release/client/snd_mixa.o -c unix/snd_mixa.s
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/gl_glx.o -c unix/gl_glx.c
make[1]: curl-config: Command not found
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -o release/crx release/client/cl_cin.o release/client/cl_ents.o release/client/cl_fx.o release/client/cl_input.o release/client/cl_inv.o release/client/cl_main.o release/client/cl_newfx.o release/client/cl_parse.o release/client/cl_pred.o release/client/cl_tent.o release/client/cl_scrn.o release/client/cl_view.o release/client/cl_http.o release/client/console.o release/client/keys.o release/client/menu.o release/client/snd_dma.o release/client/snd_mem.o release/client/snd_mix.o release/client/qmenu.o release/client/cmd.o release/client/cmodel.o release/client/common.o release/client/crc.o release/client/cvar.o release/client/files.o release/client/mdfour.o release/client/net_chan.o release/client/sv_ccmds.o release/client/sv_ents.o release/client/sv_game.o release/client/sv_init.o release/client/sv_main.o release/client/sv_send.o release/client/sv_user.o release/client/sv_world.o release/client/q_shunix.o release/client/vid_menu.o release/client/vid_so.o release/client/sys_unix.o release/client/rw_unix.o release/client/glob.o release/client/net_udp.o release/client/q_shared.o release/client/pmove.o release/ref_gl/r_bloom.o release/ref_gl/r_draw.o release/ref_gl/r_image.o release/ref_gl/r_light.o release/ref_gl/r_main.o release/ref_gl/r_mesh.o release/ref_gl/r_misc.o release/ref_gl/r_model.o release/ref_gl/r_refl.o release/ref_gl/r_math.o release/ref_gl/r_script.o release/ref_gl/r_surf.o release/ref_gl/r_vlights.o release/ref_gl/r_warp.o release/ref_gl/qgl_unix.o release/client/snd_unix.o release/client/snd_mixa.o -lm -ldl  release/ref_gl/gl_glx.o -L/usr/X11R6/lib64 -L/usr/local/lib64 -lX11 -lXext -lXxf86dga -lXxf86vm -lm -ljpeg -lGL -lGLU  -ljpeg
release/client/cl_http.o: In function `CL_InitHttpDownload':
cl_http.c:(.text+0x55): undefined reference to `curl_multi_init'
cl_http.c:(.text+0x66): undefined reference to `curl_easy_init'
release/client/cl_http.o: In function `CL_HttpDownloadCleanup':
cl_http.c:(.text+0xaf): undefined reference to `curl_multi_remove_handle'
release/client/cl_http.o: In function `CL_ShutdownHttpDownload':
cl_http.c:(.text+0x191): undefined reference to `curl_easy_cleanup'
cl_http.c:(.text+0x1a8): undefined reference to `curl_multi_cleanup'
release/client/cl_http.o: In function `CL_HttpDownloadThink':
cl_http.c:(.text+0x1eb): undefined reference to `curl_multi_perform'
cl_http.c:(.text+0x211): undefined reference to `curl_multi_info_read'
cl_http.c:(.text+0x275): undefined reference to `curl_easy_getinfo'
release/client/cl_http.o: In function `CL_HttpDownload':
cl_http.c:(.text+0x3a8): undefined reference to `curl_easy_reset'
cl_http.c:(.text+0x3c0): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x3d8): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x401): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x419): undefined reference to `curl_easy_setopt'
cl_http.c:(.text+0x42c): undefined reference to `curl_multi_add_handle'
collect2: ld returned 1 exit status
make[1]: *** [release/crx] Error 1
make[1]: Leaving directory `/home/principe/Games/alienarena2008/source'
make: *** [build-release] Error 2
```

---

### Post by Brebs on 2008-03-09
> make[1]: curl-config: Command not found
```
$ which curl-config
/usr/bin/curl-config

$ pacman -Qo /usr/bin/curl-config
/usr/bin/curl-config is owned by curl 7.18.0-1

$ find /usr/include/ -type f | xargs grep curl_easy_reset
/usr/include/curl/easy.h: * NAME curl_easy_reset()
```
So install curl and [libcurl4-openssl-dev](http://packages.ubuntu.com/gutsy/amd64/libcurl4-openssl-dev/filelist) and [libcurl3](http://packages.ubuntu.com/gutsy/libcurl3).

---

### Post by Melcar on 2008-03-10
Thanks.  Now it works perfectly.  A few game related questions thought: 

- Is there a way to speed up mouse movement?  I like high sensitivity, but even if I have the setting at high the pointer moves ever so slow (particularly in the menu).

- Is there some sort of FPS counter for the game?  I like to see how well my card handles the game.

- Where do the screenshots get copied to?  I am able to take screenshots in-game (F12) but I can't find them anywhere in my alienarena folder (where I have all game files in).

---

### Post by Brebs on 2008-03-10
The config file is ~/.codered/arena/config.cfg - edit it:
```
set cl_drawfps "1"
set sensitivity "7"
```
That refers to the in-game mouse sensitivity, and not to the in-menu mouse sensitivity - file a [bug report](http://corent.proboards42.com/index.cgi) ;)

Screenshots are saved in ~/.codered/arena/scrnshot/

---

### Post by Melcar on 2008-03-10
> **Brebs said:**
> The config file is ~/.codered/arena/config.cfg - edit it:
```
set cl_drawfps "1"
set sensitivity "7"
```
That refers to the in-game mouse sensitivity, and not to the in-menu mouse sensitivity - file a [bug report](http://corent.proboards42.com/index.cgi) ;)

Screenshots are saved in ~/.codered/arena/scrnshot/

Any way to change the default location the screenies are saved to?  I'm a neat freak and would like to have everything in one place :).

---

### Post by Irritant on 2008-03-10
The only way I can think of, would be to change your "HOME" env var to where you wanted them to be stored.  Not sure if that's a good idea or not.

---

### Post by grimdeath on 2008-03-11
ok im having another weird issue, don't see anyone talking about this on the AA forums either:

-ive downloaded the .zip
-unzipped it into the /usr/loca/games/alienarena2008 directory
-tried running .crx and cannot seem to get it to work
-ls shows:
```
Aa1.ico  arena    crded  crx.sdl  docs  source
aa.png   botinfo  crx    data1    FUSE  Tools

```

here's what I get:

```
./crx: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory
```

I looked on synaptic but could not locate libcurl.so and wasnt sure what to do after that (today marks exactly my first week in ubuntu!)

any help would be appreciated.

---

### Post by Perfect Storm on 2008-03-11
Just search for libcurl not libcurl.so

---

### Post by emonkey on 2008-03-11
We've got now a wishlist-bug, please keep on voting.

[[IMG]http://brainstorm.ubuntu.com/idea/3876/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3876/)

---

### Post by desertboy on 2008-03-12
Works beautifully here I guess I already had the packages installed although I did have alien arena 2007 on the machine.

Nice update

---

### Post by Chame_Wizard on 2008-03-12
> **Artificial Intelligence said:**
> Read the guide carefully - even the things that aren't in a code box.

I can see you have kubuntu, so you have to make some changes when it comes to the launcher part as the guide is written for/on Ubuntu (gnome).

damn it sucks  :(

---

### Post by Perfect Storm on 2008-03-12
> **Chame_Wizard said:**
> damn it sucks  :(

Just where it says alacarte. Instead you open/edit KDE menu (launcher) . Or make your own launcher. - The info is there.

---

### Post by Chame_Wizard on 2008-03-12
strange at all,i even moved+cut the Alien Arena folder to my home.

---

### Post by Irritant on 2008-03-12
> **grimdeath said:**
> ok im having another weird issue, don't see anyone talking about this on the AA forums either:

-ive downloaded the .zip
-unzipped it into the /usr/loca/games/alienarena2008 directory
-tried running .crx and cannot seem to get it to work
-ls shows:
```
Aa1.ico  arena    crded  crx.sdl  docs  source
aa.png   botinfo  crx    data1    FUSE  Tools

```

here's what I get:

```
./crx: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory
```

I looked on synaptic but could not locate libcurl.so and wasnt sure what to do after that (today marks exactly my first week in ubuntu!)

any help would be appreciated.

You need to install libcurl, that should fix that problem.

---

### Post by Melcar on 2008-03-17
Very good game.  A few questions thought.  Is it supposed to look this dark?

[IMG]http://img217.imageshack.us/img217/1792/alienarena012bd3.jpg[/IMG]

Or is it just on certain maps?  I have only played in a few maps (like 3 or 4) but they all look dark.  Even if I turn the ambient and texture brightness to the max the objects themselves remain very dark.
Another thing is that in certain maps it appears as if textures were missing.  I'm not sure, but the screenshots and in game footage I have been watching from the site look a bit "richer" than how the game looks on my machine, and I'm running it at max eye candy.  I have also noticed this when I launch the game and when a map loads:
```


------------------------------------
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode -1: 1680 1050
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: ATI Technologies Inc.
GL_RENDERER: ATI Radeon HD 2900 XT
GL_VERSION: 2.1.7414 Release
GL_EXTENSIONS: GL_AMD_performance_monitor GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_meminfo GL_ATI_separate_stencil GL_ATI_texture_compression_3dc GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_vertex_array GL_KTX_buffer_region GL_NV_blend_square GL_NV_texgen_reflection GL_SGIS_generate_mipmap GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_WIN_swap_hint WGL_EXT_swap_control 
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
------------------------------------
======== CRX Initialized ========

```

Maybe it's the ATI card I'm running.

---

### Post by Brebs on 2008-03-17
> **Melcar said:**
> ATI card
Try different [ATI drivers](http://corent.proboards42.com/index.cgi?board=general&action=display&thread=1204946224&page=2).

---

### Post by Melcar on 2008-03-17
Reverting to previous driver revisions is not an option.  My card did not start performing until the 8.1s and stopped suffering from segmentation faults in 8.2.

Another screeni (texture and ambient lighting to the max):

[IMG]http://img223.imageshack.us/img223/6146/alienarena013mx6.jpg[/IMG]

Several maps display that black foreground, where I think detailed textures should be.  

```
...allowing CDS
...enabling GL_EXT_compiled_vertex_array
...ignoring GL_EXT_point_parameters
...3DFX_set_global_palette not found
...GL_EXT_shared_texture_palette not found
...using GL_ARB_multitexture
...GL_SGIS_multitexture not found
...using GL_ARB_texture_env_combine
...GL_NV_texture_shader not found
```

Are these extensions the game uses that the driver lacks?  According to the thread you linked to the ATI driver is unable to correctly process some ARB shader (I also suffer from the "candy" water when reflections are on).  Is this the only extension the driver has problems with or are there others?  Planing on filing a report to the ATI beta mailing list about this and see where it goes.

---

### Post by Polygon on 2008-03-17
Looks like a cool game, but ati's shoddy drivers for linux prevent me from playing this game on linux...i get like 5 fps on this game, but like 30 fps on a much more intensive game (team fortress 2) on windows? stupid ati =/

ill try it on windows later

---

### Post by Melcar on 2008-03-17
> **Polygon said:**
> Looks like a cool game, but ati's shoddy drivers for linux prevent me from playing this game on linux...i get like 5 fps on this game, but like 30 fps on a much more intensive game (team fortress 2) on windows? stupid ati =/

ill try it on windows later


What card are you using?  Aside from the above rendering problems, the game runs fast with all the eye candy on (except reflective water because that causes problems) at a 1680x1050 resolution, with a HD2900XT.  The game also runs decently on my laptop's 200M (800x600, low settings). However, the problems I detailed on previous posts render the game unplayable on certain maps, simply because I can't see anything.

---

### Post by Polygon on 2008-03-19
an ATI Radeon 9800

on windows im able to play games quite well, even with wide open areas such as this one i get at least 30-40 fps (see attachment)

but on this game its pretty much unplayable...and i havent changed any of the settings from the default, which leads me to believe its something with the drivers

---

### Post by Melcar on 2008-03-19
Try turning off all the effects, specially bumpmapping, since that is causing severe rendering issues on my machines.  Dynamic shadows and lights will beat up your GPU, so turn them off too.  Play with the rest of the options until you get favorable results.  My 200M can dish out between 15-20fps at a 800x600 resolution with low settings on most maps, and that chip is like 1/10 of your card.

---

### Post by Wobedraggled on 2008-03-20
I tried this last night, pretty cool, Like Mars attacks the video game :)

---

### Post by Irritant on 2008-03-20
> **Melcar said:**
> Several maps display that black foreground, where I think detailed textures should be. 
 
Are these extensions the game uses that the driver lacks?  According to the thread you linked to the ATI driver is unable to correctly process some ARB shader (I also suffer from the "candy" water when reflections are on).  Is this the only extension the driver has problems with or are there others?  Planing on filing a report to the ATI beta mailing list about this and see where it goes.

The "candy" water is definitely a driver issue.  ATI drivers seem to have a problem processing the fragment shader for reflective water.  This used to work, then stopped on their newest driver set.  

Now the dark maps, that may or may not be a driver issue.  Is this happening on all maps, or just a few?  Does it happen on default settings, or maybe when bumpmapping is enabled only?  It almost appears as if you were unable to load the lightmap data for the map.

---

### Post by Melcar on 2008-03-20
> **Irritant said:**
> The "candy" water is definitely a driver issue.  ATI drivers seem to have a problem processing the fragment shader for reflective water.  This used to work, then stopped on their newest driver set.  

Now the dark maps, that may or may not be a driver issue.  Is this happening on all maps, or just a few?  Does it happen on default settings, or maybe when bumpmapping is enabled only?  It almost appears as if you were unable to load the lightmap data for the map.

It was the bumpmaps.

---

### Post by dgel on 2008-03-20
Hi, I like what this game looks like and promises, so I installed it with a .deb from GetDeb. It runs fine on my pc, except that the sound is distorted. 
I've already got (define devices '(native)) in my .openalrc and the openal soft package doesn't seem to work for me. Any ideas what else I might try?
 btw I had the same issue with alien arena 2007. It's the only thing keeping me from playing this game..

Na-Fiann

---

### Post by Melcar on 2008-03-20
Have you tried messing around with the sampling rate? On my laptop anything besides 48HKz causes distortion.  Also, I don't know about the .deb package, but on the regular AA folder (the one you get from their site) they have two binaries, crx and crx.sdl; crx.sdl seems to be more compatible on different systems, but for me it causes sound distortion.

---

### Post by dgel on 2008-03-20
Well I just played around with the surround settings of my pc and found a nice fix for this problem that at least works for me. It is easy to implement and has made all my games output perfect sound = through alsa!.

simply define in the file .asoundrc (make one if it doesn't exist) a default alsa configuration. in my case it became this:

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

For me this worked like a charm and I don't need the .openalrc file anymore either.

note though that this version tries to upmix audio with less channels. Simply leave 
"route_policy duplicate" out if you don't want it.

Hope this helps someone else as well.

---

### Post by Polygon on 2008-03-20
i also had problems with sound, until i read on a forum to try renaming crx to crx.old and then renamed crx.sdl or whatever to crx and then running it, and then sound worked

i played a match today (on the lowest settings, 1024x768 res) and i cant help but feel this is exactly like every other linux shooter out there. Sure it has different weapons and models and atmosphere, but its just quake, there is a railgun, machine gun, rocket launcher, etc etc. I feel that its just the same game that ive been playing with nexiuz and warsow and all that..... this game needs something different that no other game has,

---

### Post by Brebs on 2008-03-20
> **Polygon said:**
> renaming crx to crx.old
That renaming is pointless - just run the desired executable.

Edit: Presumably, you had a desktop link pointing to /usr/bin/crx, and didn't have a desktop link pointing to /usr/bin/crx.sdl - it would have been easier to change the desktop link, which is probably in /usr/share/applications/

---

### Post by Irritant on 2008-03-21
> **Polygon said:**
> i also had problems with sound, until i read on a forum to try renaming crx to crx.old and then renamed crx.sdl or whatever to crx and then running it, and then sound worked

i played a match today (on the lowest settings, 1024x768 res) and i cant help but feel this is exactly like every other linux shooter out there. Sure it has different weapons and models and atmosphere, but its just quake, there is a railgun, machine gun, rocket launcher, etc etc. I feel that its just the same game that ive been playing with nexiuz and warsow and all that..... this game needs something different that no other game has,

It has mechanical cows :) (Cattle prod Mode)  Vehicles in All Out Assault, and giant metal spiders in Team Core Assault :)

---

### Post by Irritant on 2008-03-21
> **Melcar said:**
> It was the bumpmaps.

OK - yeah that's the driver failing to handle the GL_CUBEMAP extension.  This is something we are looking into, because even though it is a driver issue, there are other games using similar bumpmapping techniques that don't have the problem, so I do believe we'll have a workaround for it.  Same goes with the reflective water issue.  It is kinda frustrating for us though, having things working fine, and then a new driver release comes out and *bang* stuff stops working correctly.  

We've already done quite a bit of work since this release in regards to the renderer, changing some techniques that have further improved speed, and I expect that in a couple of months a new version will be released, hopefully repairing any of these driver related bugs if possible.

---

### Post by Melcar on 2008-03-21
> **Irritant said:**
> OK - yeah that's the driver failing to handle the GL_CUBEMAP extension.  This is something we are looking into, because even though it is a driver issue, there are other games using similar bumpmapping techniques that don't have the problem, so I do believe we'll have a workaround for it.  Same goes with the reflective water issue.  It is kinda frustrating for us though, having things working fine, and then a new driver release comes out and *bang* stuff stops working correctly.  

We've already done quite a bit of work since this release in regards to the renderer, changing some techniques that have further improved speed, and I expect that in a couple of months a new version will be released, hopefully repairing any of these driver related bugs if possible.

I submitted a simple report to the driver mailing list, so you can be sure the devs will at least glance at it :).

---

### Post by sit22 on 2008-03-29
i managed to get it running on Ubuntu 7.10 x64. problem is when i try to join any server i get crash to desktop and this: 
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3000002
  Serial number of failed request:  87
  Current serial number in output stream:  90
Singleplayer works fine. Any ideas?

---

### Post by ReLiK on 2008-05-25
I used to be a big fan of the original Unreal Tournament, so this game has really brought a smile to my face.  However every 3 or 4 games I get thrown to the desktop.

I'm running Hardy with an Ati card. 

This is the output from the console:

Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  162 (GLX)
  Minor opcode of failed request:  11 (X_GLXSwapBuffers)
  Serial number of failed request:  189661
  Current serial number in output stream:  189671

And more recently:

ctf-corrosion
*** stack smashing detected ***: /usr/lib/games/alien-arena/crx.sdl terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7b14138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7b140f0]
/usr/lib/games/alien-arena/crx.sdl[0x80d0814]
/usr/lib/games/alien-arena/crx.sdl[0x80b442c]


I would like to try the renaming crx fix  but I can only find crx.sdl not crx

Any help would be appreciated.

---

### Post by Irritant on 2008-05-25
[http://ubuntuforums.org/showthread.php?t=797869](http://ubuntuforums.org/showthread.php?t=797869)

That will fix your stack smashing problem.

---

### Post by spydefender on 2008-06-15
if you see 
```
./crx.sdl: error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory
``` error, you must install **libcurl**.
Or you may try to create link in /usr/lib/ to **libcurl.so.4** (or later) named **libcurl.so.3** and play it)

---

### Post by Hooya on 2008-07-01
> **Artificial Intelligence said:**
> Read the guide carefully - even the things that aren't in a code box.

I can see you have kubuntu, so you have to make some changes when it comes to the launcher part as the guide is written for/on Ubuntu (gnome).

I'm having the same Error2 message on my box, but the link for the guide you put here is down.  Any suggestions or a mirror to that guide?  I'm running an Ubuntu installation, but log in to a Fluxbox manager, not Gnome.  I can log back into Gnome if I have to just to get it set up right.

Edit:   No different if I log into Gnome.

---

### Post by cov on 2008-11-10
I'm getting an error running 'make' on my AMD64 Shuttle:
```
root@Gimli:/opt/alienarena2008/source# make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8"
make[1]: Entering directory `/opt/alienarena2008/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/gl_glx.o -c unix/gl_glx.c
unix/gl_glx.c:57:36: error: X11/extensions/xf86dga.h: No such file or directory
unix/gl_glx.c:58:38: error: X11/extensions/xf86vmode.h: No such file or directory
unix/gl_glx.c:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
unix/gl_glx.c: In function ‘install_grabs’:
unix/gl_glx.c:130: error: ‘XF86DGADirectMouse’ undeclared (first use in this function)
unix/gl_glx.c:130: error: (Each undeclared identifier is reported only once
unix/gl_glx.c:130: error: for each function it appears in.)
unix/gl_glx.c: In function ‘GLimp_SetMode’:
unix/gl_glx.c:540: error: ‘vidmodes’ undeclared (first use in this function)
unix/gl_glx.c: In function ‘GLimp_Shutdown’:
unix/gl_glx.c:676: error: ‘vidmodes’ undeclared (first use in this function)
make[1]: *** [release/ref_gl/gl_glx.o] Error 1
make[1]: Leaving directory `/opt/alienarena2008/source'
make: *** [build-release] Error 2

```

I think I've got the dependencies installed correctly (well, obviously not!).

I'm using Intepid 8.10.

---

### Post by Grishka on 2008-11-10
> **cov said:**
> I'm getting an error running 'make' on my AMD64 Shuttle:
```
root@Gimli:/opt/alienarena2008/source# make
make targets BUILDDIR=release CFLAGS=" -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8"
make[1]: Entering directory `/opt/alienarena2008/source'
cc -Dstricmp=strcasecmp -D_stricmp=strcasecmp -I/usr/X11R6/include -fno-strict-aliasing -fmerge-constants -DHAVE_CURL -O2 -fomit-frame-pointer -fexpensive-optimizations -march=k8 -fPIC -o release/ref_gl/gl_glx.o -c unix/gl_glx.c
unix/gl_glx.c:57:36: error: X11/extensions/xf86dga.h: No such file or directory
unix/gl_glx.c:58:38: error: X11/extensions/xf86vmode.h: No such file or directory
unix/gl_glx.c:89: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
unix/gl_glx.c: In function ‘install_grabs’:
unix/gl_glx.c:130: error: ‘XF86DGADirectMouse’ undeclared (first use in this function)
unix/gl_glx.c:130: error: (Each undeclared identifier is reported only once
unix/gl_glx.c:130: error: for each function it appears in.)
unix/gl_glx.c: In function ‘GLimp_SetMode’:
unix/gl_glx.c:540: error: ‘vidmodes’ undeclared (first use in this function)
unix/gl_glx.c: In function ‘GLimp_Shutdown’:
unix/gl_glx.c:676: error: ‘vidmodes’ undeclared (first use in this function)
make[1]: *** [release/ref_gl/gl_glx.o] Error 1
make[1]: Leaving directory `/opt/alienarena2008/source'
make: *** [build-release] Error 2

```

I think I've got the dependencies installed correctly (well, obviously not!).

I'm using Intepid 8.10.

obviously not. :-) try these: [apt://libxxf86dga-dev]("apt://libxxf86dga-dev"), [apt://libxxf86vm-dev]("apt://libxxf86vm-dev").

---

### Post by Mason Whitaker on 2008-11-10
Heh, this game looks really close to Nexuiz.
I might just give it a try :3

---

### Post by MaxIBoy on 2008-11-10
> **Mason Whitaker said:**
> Heh, this game looks really close to Nexuiz.
The way Ender's Game looks like Foundation. Okay, maybe not such a good analogy, but you get the idea.

---

### Post by cov on 2008-11-11
> **Grishka said:**
> obviously not. :-) try these: [apt://libxxf86dga-dev]("apt://libxxf86dga-dev"), [apt://libxxf86vm-dev]("apt://libxxf86vm-dev").

Great! :)

I've got it working now.

Incidentally, after calling 'make' in the sources directory.

cd ..
cp -f source/release/game.so arena/game.so
cp -f source/release/cr* .

doesn't work for me...

...but 'make install' does.:guitar:

---

### Post by allbestmessages on 2008-11-11
Alien Arena is most intresting game and now discuss about this game.This is new and difficult game.Alien Arena 2008 is a free, stand-alone deathmatch game based on source code released by id Software. Begun by COR Entertainment in 2004, the game combines a 1950s-era sci-fi atmosphere with gameplay similar to the Quake, Doom, and Unreal Tournament series. Alien Arena focuses mainly on online multiplayer action, although it does contain single-player campaigns against bots.

Alien Arena has been released for Microsoft Windows, Linux and FreeBSD. The game has been free to play since its inception, and there are currently no plans to change it to a pay-to-play format. However, as of October 15, 2008, the latest SVN builds now feature in-game advertising, in the main menu and in some maps.

---

### Post by cov on 2008-11-11
I was able to run the game initially, but now I'm getting this error:
> dave@Gimli:~ $ /opt/alienarena2008/crx
using /home/dave/.codered/data1/ for writing
using /home/dave/.codered/arena/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
recursive shutdown
Error: Couldn't load pics/colormap.pcx


---

### Post by Brebs on 2008-11-11
Use [strace](http://corent.proboards42.com/index.cgi?board=rookie&action=display&thread=86&page=2), to see *where* the executable is looking for its data files.

---

### Post by cov on 2008-11-12
Um.

It was looking for ./data1/pics/ for files.

Once I changed directory to /opt/alienarena, it started ok.:oops:

---

### Post by The Datkitecht on 2009-01-06
hey guys am kinda new to linux. I've managed alot of things so far but am having problem with Alien Arena i dont know how to install it coz its a .zip.
I was googling around and I've seen that alot of people were saying about <directory> /./crx but I get an error which is 
**
agathodaimon@agathodaimon:~$ /home/agathodaimon/Desktop/alienarena2008-linux20081016/./crx
using /home/agathodaimon/.codered/data1/ for writing
using /home/agathodaimon/.codered/arena/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Master server at 69.143.100.63:27900
Sending shutdown to 69.143.100.63:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx
**

I hope that you can help me out here. thanks 

am runing Ubuntu 8.10
Intel p4 2.8 Ghz
512mb ram
Ati Radeon 9200Se Family Edition 128mb

---

### Post by Brebs on 2009-01-06
People really [shouldn't be faced](http://corent.proboards42.com/index.cgi?board=bugreport&action=display&thread=3543) with such baffling error messages :( Isn't 2009 supposed to be the year of Linux On The Desktop?

---

### Post by MaxIBoy on 2009-01-06
> **Brebs said:**
> Isn't 2009 supposed to be the year of Linux On The Desktop?

Oh, no, not another one!

---

### Post by Perfect Storm on 2009-01-07
> **MaxIBoy said:**
> Oh, no, not another one!

where? where? where?

---

### Post by wolfyking2 on 2009-01-07
I can't play this because I have 64 bit D:  and a bunch of other games...Here's an easy way to install it, though.  Go to Add/Remove programs, then go to games, just scroll a little and it should be there.  (There are a bunch of games on the Add/Remove thing, but unfortunately I can't play them since I have 64bit)

---

### Post by Brebs on 2009-01-07
> **wolfyking2 said:**
> I can't play this because I have 64 bit
Oh yes you can. In fact, you can run either the 32-bit or 64-bit version, after [installing the appropriate libs](http://corent.proboards42.com/index.cgi?board=rookie&action=display&thread=3420) and [compiling it](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena).

It's farcical that [Ubuntu's official version](http://packages.ubuntu.com/intrepid/alien-arena) is [out-of-date](https://bugs.launchpad.net/ubuntu/+source/alien-arena/+bug/279429) (ver 7.00 instead of 7.20).

---

### Post by zepppaosla on 2009-01-08
> **Brebs said:**
> Oh yes you can. In fact, you can run either the 32-bit or 64-bit version, after [installing the appropriate libs](http://corent.proboards42.com/index.cgi?board=rookie&action=display&thread=3420) and [compiling it](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena).

It's farcical that [Ubuntu's official version](http://packages.ubuntu.com/intrepid/alien-arena) is [out-of-date](https://bugs.launchpad.net/ubuntu/+source/alien-arena/+bug/279429) (ver 7.00 instead of 7.20).

World is in financial crise. Learn how to survive and play virtual stock exchange. Only the best wins!

[http://borsegame.cjb.net](http://borsegame.cjb.net)




See rankings:

[img]http://i48.servimg.com/u/f48/11/28/59/10/26670010.jpg[/img]

---

### Post by zepppaosla on 2009-01-08
> **Brebs said:**
> Oh yes you can. In fact, you can run either the 32-bit or 64-bit version, after [installing the appropriate libs](http://corent.proboards42.com/index.cgi?board=rookie&action=display&thread=3420) and [compiling it](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena).

It's farcical that [Ubuntu's official version](http://packages.ubuntu.com/intrepid/alien-arena) is [out-of-date](https://bugs.launchpad.net/ubuntu/+source/alien-arena/+bug/279429) (ver 7.00 instead of 7.20).

World is in financial crise. Learn how to survive and play virtual stock exchange. Only the best wins!

http://borsegame.cjb.net




See rankings:

[img]http://i48.servimg.com/u/f48/11/28/59/10/26670010.jpg[/img]

---

### Post by kafkaian on 2009-05-24
> **Brebs said:**
> It's farcical that [Ubuntu's official version](http://packages.ubuntu.com/intrepid/alien-arena) is [out-of-date](https://bugs.launchpad.net/ubuntu/+source/alien-arena/+bug/279429) (ver 7.00 instead of 7.20). And months on it's still farcical.

So I'm trying to build this myself to no avail. Keep getting build errors. The latest falls over almost immediately with:

make[1]: *** [release/client/qal_unix.o] Error 1
make[1]: Leaving directory `/home/ian/alienarena2008/source'
make: *** [build-release] Error 2

Any ideas?

---

### Post by Irritant on 2009-05-24
Do you have OpenAL installed properly?  It needs it to compile.

---

### Post by kafkaian on 2009-05-25
> **Irritant said:**
> Do you have OpenAL installed properly?  It needs it to compile.
Thanks I'll take a look - although looking at the available packages I'm a bit at a loss to understand what I would need. Is there any output I could drop by you to assess this?

---

### Post by Irritant on 2009-05-25
> **kafkaian said:**
> Thanks I'll take a look - although looking at the available packages I'm a bit at a loss to understand what I would need. Is there any output I could drop by you to assess this?

If you go to the forums at [http://red.planetarena.org](http://red.planetarena.org) I believe there is a thread that explains the dependencies needed.

---

### Post by kafkaian on 2009-05-25
> **Irritant said:**
> If you go to the forums at [http://red.planetarena.org](http://red.planetarena.org) I believe there is a thread that explains the dependencies needed.Thanks again Irritant, but I still don't know why the old failing version is still in the repositories. I'll give it a go, but if I have to search through reams of material to get to the point then I'll simply give up. Too much on at the moment.

---

