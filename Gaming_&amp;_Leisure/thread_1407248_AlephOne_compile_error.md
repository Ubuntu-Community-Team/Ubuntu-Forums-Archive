---
title: "AlephOne compile error"
date: 2010-02-15
forum: Gaming &amp; Leisure
---

### Post by Lepy on 2010-02-15
On two different 9.10 boxes, I am getting the same error when trying to "make" AlephOne. "./configure" completes without error. I'm using the latest version: AlephOne-20100118

I've installed all the dependencies (as far as I can tell) and here is the relevant message for both:
```
Making all in XML
make[3]: Entering directory `/home/xbmc/Downloads/AlephOne-20100118/Source_Files/XML'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/xbmc/Downloads/AlephOne-20100118/Source_Files/XML'
make[3]: Entering directory `/home/xbmc/Downloads/AlephOne-20100118/Source_Files'
g++  -g -O2   -o alephone shell.o shell_misc.o DefaultStringSets.o CSeries/libcseries.a Expat/libexpat.a Files/libfiles.a GameWorld/libgameworld.a Input/libinput.a Lua/liba1lua.a Misc/libmisc.a ModelView/libmodelview.a Network/libnetwork.a Network/Metaserver/libmetaserver.a RenderMain/librendermain.a RenderOther/librenderother.a Sound/libsound.a XML/libxml.a CSeries/libcseries.a Expat/libexpat.a Files/libfiles.a GameWorld/libgameworld.a LibNAT/libnat.a Input/libinput.a Lua/liba1lua.a Misc/libmisc.a ModelView/libmodelview.a Network/libnetwork.a Network/Metaserver/libmetaserver.a RenderMain/librendermain.a RenderOther/librenderother.a Sound/libsound.a TCPMess/libtcpmess.a XML/libxml.a -lasound -lspeex -lvorbisfile -lvorbis -lm -logg   -lsndfile -lmad -lsmpeg -lpng12   -Wl,-Bsymbolic-functions -lzzip -lz   -lz -lSDL_net -lSDL_image  -L/usr/lib -lSDL -lGL -lpthread -lGLU
Network/libnetwork.a(network_speex.o): In function `destroy_speex_encoder()':
/home/xbmc/Downloads/AlephOne-20100118/Source_Files/Network/network_speex.cpp:78: undefined reference to `speex_preprocess_state_destroy'
Network/libnetwork.a(network_speex.o): In function `init_speex_encoder()':
/home/xbmc/Downloads/AlephOne-20100118/Source_Files/Network/network_speex.cpp:56: undefined reference to `speex_preprocess_state_init'
/home/xbmc/Downloads/AlephOne-20100118/Source_Files/Network/network_speex.cpp:59: undefined reference to `speex_preprocess_ctl'
/home/xbmc/Downloads/AlephOne-20100118/Source_Files/Network/network_speex.cpp:61: undefined reference to `speex_preprocess_ctl'
/home/xbmc/Downloads/AlephOne-20100118/Source_Files/Network/network_speex.cpp:64: undefined reference to `speex_preprocess_ctl'
collect2: ld returned 1 exit status
make[3]: *** [alephone] Error 1
make[3]: Leaving directory `/home/xbmc/Downloads/AlephOne-20100118/Source_Files'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xbmc/Downloads/AlephOne-20100118/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/xbmc/Downloads/AlephOne-20100118'
make: *** [all] Error 2

```

I have most of the speex packages (and devs) installed.

The package found [here](http://xzcallaway.synthasite.com/rpg.php) works, but I would rather compile the latest version.

Also, if I can get the game to successfully compile, is there an easy way to install and launch multiple scenarios (at seperate time, of course)?

---

### Post by Lepy on 2010-02-15
False alarm? I tried compiling again, and it worked! 

I didn't install any extra packages, I just rebooted the machines at some point in between and ran "./configure" again. However, one machine did require me to run "sudo make" because it failed on a permission error.

Now, I just need to figure out how I am going to get the scenarios working with MythGame and hope Aleph One works with qjoypad!

---

### Post by Lepy on 2010-02-16
I also got multiple scenarios working with MythGame.

I made two directories:
~/games/alephone/roms
~/games/alephone/scenarios

I unpacked each scenario to its own folder in the scenario path. I then created executable scripts for each scenario in the roms folder which contained:

```
#!/bin/bash

rm ~/.alephone
ln -s ~/games/alephone/scenarios/*scenariofoldername* ~/.alephone
alephone
```

After making a script like this for each scenario, launching said script would launch the correct game without having to replace scenario files. To launch from MythGame:

Player Name: Alephone
Type: Other
Rom Path: ~/games/alephone/roms

You will have to reconfigure preferences for each scenario on first launch...but it should be ok after that.

---

### Post by jukzh on 2010-11-13
Hi, I can't build too :(

```

AlephOne-20100424/Source_Files/Network/network_speex.cpp:64: undefined reference to `speex_preprocess_ctl'

```

---

### Post by Rustybolts on 2010-11-13
Hi this forum post of  mine may help its not a step by step walkthrough but more of an account on how I accomplished installing it and the problems I encountered, there are links for 32bit and 64bit debs located within post.
[http://www.gamingonlinux.info/community/viewtopic.php?f=13&t=96](http://www.gamingonlinux.info/community/viewtopic.php?f=13&t=96)

---

### Post by WienerWuerstel on 2010-11-13
Why compile when there is a [PPA]("https://launchpad.net/~gjditchfield/+archive/ppa")? It's easier to install and works just fine.

---

### Post by iamanidiot123 on 2011-07-24
Copy this and paste it into your terminal:
```
sudo apt-get install libsdl1.2-dev libsdl-net1.2 libsdl-net1.2-dev zziplib-bin libzzip-dev libboost-dev libsndfile1 libsndfile1-dev libsdl-ttf2.0-dev libsdl-image1.2-dev libmadlib-dev libsmpeg-dev libspeex-dev libspeexdsp-dev libmad0-dev
```
it will prompt you if you want to install a long list of stuff, type y, and then every thing should work just fine. (this is for the others who come to this thread with compile errors)
The alephone version i successfully compiled with these instructions was 2011-06-26 (beta3)


Instructions came from:
[http://www.mariusnet.com/ubbthreads.php?ubb=showflat&Number=25157](http://www.mariusnet.com/ubbthreads.php?ubb=showflat&Number=25157)

---

### Post by ranger12 on 2011-08-30
Hey guys in conjunction with this. I have compiled it successfully and i tried the Marathon Infinity game files and it runs great. How would I set it up in the /usr/local/share/AlephOne directory so I could download all three game file sets and be able to play Marathon, Marathon 2 and Marathon Infinity?

---

### Post by hulkman on 2011-08-30
You can install a bunch of marathons side by side by installing the deb files from [http://www.dotdeb.com/rpg.php](http://www.dotdeb.com/rpg.php)  Then run them.

---

### Post by ranger12 on 2011-08-31
Ah but that is an earlier source dated back to February. The latest source for Linux is dated 20110730. I compiled the engine from that source. All I want to do is put the 3 separate game set files in their respective folders under /usr/local/share/Alephone and than create desktop files for each and tell the AlephOne engine where to find the games files for each game like:

/usr/local/share/AlephOne/Marathon
/usr/local/share/AlephOne/Marathon 2
/usr/local/share/AlephOne/Marathon Infinity

I assume their must be an environment variable that can be set for each from with the desktop file before it runs the AlephOne game engine to tell it where to find the game files for each. I can just create my own desktop file for each. That's all.

---

### Post by ranger12 on 2011-09-01
Never mind, after doing a little research - i figured out the correct syntax with the AlephOne environment variable and if works just fine now. I can drop all three game file sets in their respective directories under /usr/local/share/AlephOne and run anyone of the three games now. Cool.

---

