---
title: "A problem that i bumped into with dangerdeep(This might even trouble OpenSSN players)"
date: 2011-08-16
forum: Gaming &amp; Leisure
---

### Post by onkadude on 2011-08-16
I 'll try to be as precise as possible..
I have the intel 945GCNL motherboard. which comes with the 945G integ. graphics.
2.2Ghz core 2 duo & 1 GB ram.(Well in range for this game)

I compiled Dangerdeep after following instructions from the website home page which says.

```

apt-get install subversion g++ scons libsdl1.2-dev libsdl-mixer1.2-dev libsdl-image1.2-dev libfftw3-dev libbz2-dev

```after installing then i commit to their svn repo with their command

```

svn co https://dangerdeep.svn.sourceforge.net/svnroot/dangerdeep/trunk/dangerdeep/ dangerdeep

```Then again diligently following their instructions, i compile it using the command

```
cd dangerdeep
scons debug=1 datadir=`pwd`/data 

```It compiled successfully and dangerdeep binary was in the ./build/linux/ folder.

So far so good..

When i ran the game using the debug flag, it spat out this exception.
```
[COLOR=Red][__main__] <399> src/mymain.cpp:59 Caught exception: GLSL shaders are not supported![/COLOR]
```Well this seemed to indicate an absence of a library that provided this.

After rummaging around the internet, i found that  package libgl.so.1 seemed to provide it.
When firing this up in synaptic. it directed me to this package 
libgl1-mesa-swx11
But in the description it hints that it renders in software mode and does not use my hardware acceleration.
To make myself clear about the presence of hardware acceleration.(**NOTE:This step was carried out before installing libgl1-mesa-swx11.**)

```
glxinfo | grep -i opengl
```Threw out this.
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.9-devel
OpenGL extensions:

```This made it clear that well my driver is running fine.but it also shows no OpenGL extensions are available. (My intuition said well GLSL might be an extension that wasnt there.)

But since libgl1-mesa-swx11 seemed to apparently solve the problem i  installed it and fired up dftd.
The game loaded fine. but was painfully slow, suggesting HW accl. was not used.(Expected situation..hmmm)(And yes it didn crash while doing anything,just doing it too slow).
i put glxinfo | grep -i opengl into terminal and found this
```
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

```Suggesting the use of new drivers,(but this also caused HW accl to be disabled.This was evident in slowing down of all games incl,Urban terror and Openarena..)

I reverted to my original drivers by removing the offending library, and everything became normal again,but dangerdeep wont run..

Can anyone help me in sorting out this issue... I really wanna play this game.
Since openSSN also uses very similiar stuff i thought i might even inform its dev about it..That why i put up its name in the title..

---

