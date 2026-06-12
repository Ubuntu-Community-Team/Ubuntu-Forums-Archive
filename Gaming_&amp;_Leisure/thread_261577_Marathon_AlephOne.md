---
title: "Marathon: AlephOne"
date: 2006-09-20
forum: Gaming &amp; Leisure
---

### Post by Fictorus Garuva on 2006-09-20
Help!!!, I have a problem with the game Aleph One ([Http://source.bungie.org)](Http://source.bungie.org)), after downloading the RPM pack there, converting it with Alien and installing it (everything perfect so far) and installing its data files, I run it from a terminal with "alephone" and it displays this message:

**"alephone: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by alephone)"**

I searched all over the web and Synaptic and I found no GLIBC_2.4. Only solution I found was running the windows version (yuck) with Wine, but it can't use the OpenGL renderer of the game. Again: Help!!! please.

And excuse my bad english :D

---

### Post by haxer on 2006-09-20
dude the game sux monkey :) try Truecombat elite instead!! :-({|=

---

### Post by skymt on 2006-09-20
@haxer: Shut up.

@FG: What version of libc do you have? (Search in Synaptic.) Be warned that alien is imperfect, you may have to compile it yourself.

---

### Post by haxer on 2006-09-20
Why shut up? I though if i wanted to teas i could do it?

---

### Post by Fictorus Garuva on 2006-09-20
I have libc6-i686 2.3.6-0ubuntu20.

---

### Post by haxer on 2006-09-20
Ok nothing bad about the game i think it looks old deosnt meen that you find it old sry about the other post

---

### Post by Fictorus Garuva on 2006-09-20
*Like A1's VacBobs* "He he... no hard feelings" :D

---

### Post by haxer on 2006-09-20
> **Fictorus Garuva said:**
> *Like A1's VacBobs* "He he... no hard feelings" :D

Meaning for thoose people like me that deosnt know what it means? :-({|=

---

### Post by skymt on 2006-09-20
Anyway, it looks like you need to compile from source. The rpm for A1 is made for a system with a more recent version of glibc than Dapper has. Post back if you need help with the compile. I've done it, it was fairly problem-free.

---

### Post by Fictorus Garuva on 2006-09-21
Considering that 6.10 will have the glibc 2.4, I think it would be easier to upgrade to 6.10 next month.

---

### Post by Fictorus Garuva on 2006-09-21
But i'll try, how do I compile it? (i'm a noob :D)

---

### Post by skymt on 2006-09-21
> **Fictorus Garuva said:**
> But i'll try, how do I compile it? (i'm a noob :D)

I'm downloading it right now, so I can give you specifics.

I was thinking of playing through the trilogy again anyway, it's been a while.

EDIT: Okay, download done. I've read through the INSTALL.Unix file, and it looks like a mostly problem-free install, just with a lot of dependencies.

1. Install build-essential:```
sudo aptitude install build-essential
```2. Install the SDL requirements:```
sudo aptitude install libsdl1.2debian-all libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl-gfx1.2-4 libsdl-gfx1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-sound1.2 libsdl-sound1.2-dev
```3. Install the libboost requirements. The readme says it requires "libboost," but doesn't say what bits. Debian/Ubuntu split libboost into a lot of packages, so I picked most of them to be on the safe side. If anyone knows which are actually used, please say so! Here we go:```
sudo aptitude install libboost-date-time1.33.1 libboost-date-time-dev libboost-dev libboost-filesystem1.33.1 libboost-filesystem-dev libboost-iostreams1.33.1 libboost-iostreams-dev libboost-program-options1.33.1 libboost-program-options-dev libboost-regex1.33.1 libboost-regex-dev libboost-signals1.33.1 libboost-signals-dev libboost-test1.33.1 libboost-test-dev libboost-thread1.33.1 libboost-thread-dev
```4. Install the Lua requirements:```
sudo aptitude install lua50 liblua50 liblua50-dev
```5. (Optional) If you want to play online and use voice chat, you need the following:```
sudo aptitude install libspeex1 libspeex-dev
```6. Now for the easy part, I hope. This assumes you saved it to your desktop, the default. If you didn't change it:```
cd Desktop
tar -xjf AlephOne-20060701.tar.bz2
cd AlephOne-20060701
./configure
make
sudo checkinstall
```7. When checkinstall asks you things, just hit return.
8. You should be done! I hope! Let me know if you have any trouble.

---

### Post by Fictorus Garuva on 2006-09-22
ThanX, it works perfectly, ThanX a lot. and if you are going to play it I really say you should play the All-New-(Revamped?) Rubicon X here: [http://www.marathonrubicon.com/](http://www.marathonrubicon.com/) (it's like 124 Mbs)

---

### Post by Fictorus Garuva on 2006-09-22
Actually there is a problem, the system kills the game when I finish a level (using OpenGl Rendering)

---

### Post by skymt on 2006-09-22
Actually, Rubicon (the original 2001 release) is what first got me hooked on Marathon. :) 

Anyway, about your problem. I may have run into something similar. Does it happen when you click past a "splash screen" (like the "Arrival" image at the start of the game)? I've found that A1 doesn't like that. You should wait a few seconds before clicking through.

If that isn't the problem, run it from a terminal and post the error message.

---

### Post by Fictorus Garuva on 2006-09-24
Rubicon is the best A1 scenario. The problem still exist, this is what it says: Aleph One SDL linux-gnu i686 Sep 22 2006
[http://marathon.sourceforge.net/](http://marathon.sourceforge.net/)

Original code by Bungie Software <http://www.bungie.com/>
Additional work by Loren Petrich, Chris Pruett, Rhys Hill et al.
TCP/IP networking by Woody Zenfell
Expat XML library by James Clark
SDL port by Christian Bauer <Christian.Bauer@uni-mainz.de>

This is free software with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
For details, see the file COPYING.

Built with network play enabled.
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6200/AGP/SSE2
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.62)
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6200/AGP/SSE2
GL_VERSION: 1.2 (2.0.2 NVIDIA 87.62)
libpng warning: Ignoring gAMA chunk with gamma=0
libpng warning: Invalid cHRM white point
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  144 ()
  Serial number of failed request:  40412
  Current serial number in output stream:  40413

---

