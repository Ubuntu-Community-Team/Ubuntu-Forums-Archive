---
title: "Not being able to run Quake 4 and Doom3 demo"
date: 2015-09-01
forum: Gaming &amp; Leisure
---

### Post by cleiton-xavier on 2015-09-01
Hello, I am unable to run the demo version of these two demos on ubuntu 14.04.

When I try to run the Doom3 demo I realize that the screen resolution is changed, and then I see a black screen with the mouse pointer in this new resolution and nothing else happens. I am forced to logout so I can't read the terminal info (if any). I tried to output it to a file with > ./doom3-demo >> a.txt but nothing is stored in this file. So I have no clue about what to do

With Quake4 i get these messages: > --------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  33
  Current serial number in output stream:  34

So any ideas of what I can do? Many thanks.

---

### Post by NathanRodriguez on 2015-09-01
Other 3D applications that use OpenGL are working correctly on your system ?

---

### Post by ethan27 on 2015-09-01
I am a Noob but it looks like there are drivers missing from the looks of it:

```
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
```

You may need more lib libraries but I don't know just a suggestion?

---

### Post by efflandt on 2015-09-02
Note that **./doom3-demo >> a.txt** only appends stdout to that file and not stderr. So errors that use stderr would not show up in that file. If you wanted both stdout and stderr to go to that file you would do **./doom3-demo >> a.txt 2>&1**. But where did you install the demo that it is not in your $PATH, since running the demo install puts it in your path and you should not need to cd and use ./ prefix:```
efflandt@XPS-8100-1404:~$ which doom3-demo
/usr/local/bin/doom3-demo

efflandt@XPS-8100-1404:~$ echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```Since the Doom 3 demo is 32-bit, if you are running 64-bit Ubuntu maybe you are missing some 32-bit libs or the game does not know where to find the 32-bit libs. From the libs it is looking for I am guessing that you are using Intel graphics which are not exactly optimum for gaming.

I am downloading Doom 3 demo now (< 100 KB/s), but it may be evening (Chicago time) before I can try it. I forget if I ever had Doom 3 or just the original Doom and Doom 2 (and Quake & 2 & 3). I know that I found my Quake 3 pak files on my old PC for playing Quake 3 on a Raspberry Pi, but otherwise might need to see what Doom/Quake CDs I can dig up from my basement. I don't think I ever had Quake 4. I think it was Quake 2 CTF that I used to play on-line for many hours many years ago. Currently I mostly play Team Fortress 2 on Steam (In Ubuntu 14.04), but was doing some minecraft Tekkit mod last year.

PS: **doom3-demo** runs fine for me as far as video (64-bit 14.04 using nvidia graphics), other than only having 4:3 video modes that get stretched on my 1080p HDTV. But I have to figure out how to get audio working because it cannot find /dev/dsp which does not exist. I tried what was in following post, except substituting **doom3-demo** for what it shows for **quake4**, but still no sound and doom3-demo cannot find /dev/dsp: [http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760)

PPS: I figured out how to get sound for this on a 64-bit system (needed 32-bit alsa-oss, although, I used synaptic to install it)```
sudo apt-get install alsa-oss:i386
doom3-demo +set s_driver oss +set s_numberOfSpeakers 2

(then to run it with audio)
aoss doom3-demo
```

---

### Post by cleiton-xavier on 2015-09-07
> **NathanRodriguez said:**
> Other 3D applications that use OpenGL are working correctly on your system ?

Yes, I executed PCSX2 (although with several visual glitches) and UT2004 perfectly (except for speed))

> **ethan27 said:**
> I am a Noob but it looks like there are drivers missing from the looks of it:

```
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
```

You may need more lib libraries but I don't know just a suggestion?

Where I can get these?

 > **efflandt said:**
> Note that ./doom3-demo >> a.txt only appends stdout to that file and not stderr. So errors that use stderr would not show up in that file. If you wanted both stdout and stderr to go to that file you would do ./doom3-demo >> a.txt 2>&1. 

I did it and it wrote on a.txt > libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast 

Same error as Quake4


> But where did you install the demo that it is not in your $PATH, since running the demo install puts it in your path and you should not need to cd and use ./ prefix:```
efflandt@XPS-8100-1404:~$ which doom3-demo
/usr/local/bin/doom3-demo

efflandt@XPS-8100-1404:~$ echo $PATH
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

 I installed it on a custom directory outside the path

> Since the Doom 3 demo is 32-bit, if you are running 64-bit Ubuntu maybe you are missing some 32-bit libs or the game does not know where to find the 32-bit libs.

I am using a 32 bit Ubuntu

 > But I have to figure out how to get audio working because it cannot find /dev/dsp which does not exist. I tried what was in following post, except substituting doom3-demo for what it shows for quake4, but still no sound and doom3-demo cannot find /dev/dsp: [http://ubuntuforums.org/showthread.php?t=1705760](http://ubuntuforums.org/showthread.php?t=1705760)

PPS: I figured out how to get sound for this on a 64-bit system (needed 32-bit alsa-oss, although, I used synaptic to install it)```
sudo apt-get install alsa-oss:386
doom3-demo +set s_driver oss +set s_numberOfSpeakers 2

(then to run it with audio)
aoss doom3-demo
```

I think I had the same problem running UT2004 Demo. "Solved" it by running the demo on older Ubuntu (10.04). So it's not only a 64bit problem I think.


Am I using mesa software rendering? That would explain the extreme low performance (6-10fps) running Gran Turismo 3 on PCSX2 (altough the developers said in the PCSX2 forum that this game is extremely heavy and I need more cpu power to run it) and the bad performance in UT2004, where the frame rate is too slow to play on a large map (16 players) with all the graphical settings of the demo version at their maximum. But when I run the software rendering mode on the same map with all the graphical settings of the software rendering mode at their maximum, it run perfectly. My Glxgears frame rate seems low on Ubuntu 10.04 (on Thrust tahr the frame rate is limited to the refresh rate, so it's useless), about 4200 fps, with a Core 2 Duo 7500 (2.93Ghz) with a G41 IGP. With a Pentium 3 at 700Mhz and a GF4 TI4200 I think I used to get a little more than 4000 fps!. Basically the same. So even with a integrated gpu, I think I should be getting better frame rates, after all the G41 is about 6 years newer than a GF4TI. Another thing  is that the frame rates start to fall after some iterations of glxgears, with can be related to the speed step stuff of lowering the clock rate as necessary. Testing it again after a few minutes get me only about 3600fps. I have to admit that the clock reduction of 2.93Ghz to 1.6Ghz doesn't make the frame rate decrease nearly as much proportionally

This is part of my glxinfo:
> server glx vendor string: SGI
server glx version string: 1.4

client glx vendor string: Mesa Project and SGI
client glx version string: 1.4

GLX version: 1.4

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) G41 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 10.5.2
OpenGL shading language version string: 1.20

So It seems I am running accelerated OGL or Mesa software GL? If it's the latter, how I could install the needed drivers?

---

### Post by efflandt on 2015-09-08
Those files should be on your system, see if they are with the **locate** command. Then look through the output of **LIBGL_DEBUG=verbose glxinfo** to see if that gives a clue if it is looking in a different path.

Otherwise do you use the Software Updater when it comes up to update your system, or some other method? What do you get for:```
dpkg-query -l libgl1-mesa* | grep ii
```

---

### Post by cleiton-xavier on 2015-09-09
> **efflandt said:**
> Those files should be on your system, see if they are with the **locate** command. Then look through the output of **LIBGL_DEBUG=verbose glxinfo** to see if that gives a clue if it is looking in a different path.

Otherwise do you use the Software Updater when it comes up to update your system, or some other method? What do you get for:```
dpkg-query -l libgl1-mesa* | grep ii
```

They are both (i965_dri.so and the swrast_dri.so) at the dir /usr/lib/dri/.

The output of **LIBGL_DEBUG=verbose glxinfo** command it is (the first five lines): > libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL: Can't open configuration file /etc/drirc: No such file or directory.
libGL: Can't open configuration file /home/leopoldo/.drirc: No such file or directory.

I didn't used Software Updater yet.

From the ```
dpkg-query -l libgl1-mesa* | grep ii
``` i get: > ii  libgl1-mesa-dri                      7.7.1-1ubuntu3.1                                A free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx                      7.7.1-1ubuntu3.1                                A free implementation of the OpenGL API -- GLX runtime

---

### Post by efflandt on 2015-09-12
Not sure why your mesa files are older than mine (do you ignore Software Updater?). But even with those in version 10.1.3 currently in 14.04 and response from the glxinfo with prefix, on my laptop, doom3-demo errors and will NOT run with Intel graphics, but runs fine with Nvidia graphics. Although, I have not gotten audio for doom3-demo working on my laptop.```
ii  libgl1-mesa-dri:amd64                                 10.1.3-0ubuntu0.4                                   amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                                  10.1.3-0ubuntu0.4                                   i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                                 10.1.3-0ubuntu0.4                                   amd64        free implementation of the OpenGL API -- GLX runtime
ii  libgl1-mesa-glx:i386                                  10.1.3-0ubuntu0.4                                   i386         free implementation of the OpenGL API -- GLX runtime


libGL: screen 0 does not appear to be DRI3 capable
libGL: pci id for fd 4: 8086:0416, driver i965
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
libGL: Can't open configuration file /home/efflandt/.drirc: No such file or directory.
libGL: Can't open configuration file /home/efflandt/.drirc: No such file or directory.
libGL: Can't open configuration file /home/efflandt/.drirc: No such file or directory.
```I know that when I was doing graphic benchmarks to compare the Intel and Nvidia graphics on my laptop, many of the benchmarks would not run at all on Intel graphics due to missing features. Maybe someone else knows how to get around the shortcomings of Intel graphics could help, but I have run out of ideas.

---

### Post by Kale_Freemon on 2015-10-07
> **efflandt said:**
> Maybe someone else knows how to get around the shortcomings of Intel graphics could help, but I have run out of ideas.

How old are your guys' laptops? My Lemur, with Intel Graphics 5500, plays Doom 3 perfectly well even with a small mod to up the graphics a bit.

But my laptop from 2010, also with Intel Graphics, struggled to play the game under Windows (never tried it Linux until recently).

Quite possible that, if you guys are running older gear, the versions of Intel Graphics you have just aren't up to par to play the game due to just general compatibility issues. Part of trying to game with GPUs that aren't meant for gaming.

---

### Post by efflandt on 2015-10-07
The Intel graphics on my laptop is HD 4600, which does not work for doom3-demo in whatever default Intel drivers are in 64-bit 14.04. And for example Unigine-Valley benchmark runs and plays audio, but just displays a gray screen (I did not pay attention to the exact errors in the terminal valley was launched from). But I know that when running other graphic benchmarks there were some GL features missing such that some benchmarks would not run. For some reason the OP seemed to have an older version of Intel related drivers than I have.

But fortunately that laptop with hybrid graphics also has Nvidia GTX 765M which works fine for doom3-demo using nvidia drivers, other than trying to figure out audio, and works fine for other things like Steam games. I was running nvidia-331-updates, but just upgraded to nvidia-355 from graphics-drivers/ppa.

---

### Post by mastablasta on 2015-10-08
i doubt intel that is in core 2 duo can run doom3. even if it can - it won't run it fast. even first gen Core i5 GPU are bad for gaming.

as for the geeforce chips -  see if additional driver exist.

as for the "latest" 4600 - you can see if there is newer kernel available (hardware enablement stack) or if there are drivers from Intel you can use to patch the kernel ones.

---

### Post by R33D3M33R on 2015-10-11
> **cleiton-xavier said:**
> Loading GL driver 'libGL.so.1' through SDL
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

Try to rename libstdc++.so.6 and libgcc_s.so.1 in the game folder to something else.

---

