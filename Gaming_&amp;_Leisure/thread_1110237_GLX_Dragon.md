---
title: "GLX Dragon"
date: 2009-03-29
forum: Gaming &amp; Leisure
---

### Post by TrueTom on 2009-03-29
A lot of people use [FONT="Courier New"]glxgears[/FONT] as cheap benchmark. Unfortunately it does a pretty bad job as such since the displayed scene has an extremely low poly count. Therefore I've put some code together that creates a bit more of a challenge for your graphics card (foremost for integrated chips) by rendering the [Stanford dragon]("http://www-graphics.stanford.edu/data/3Dscanrep/").

This still isn't a comprehensive benchmark but at least the results don't just represent SwapBuffer performance. I've also included a version compiled for Windows, so if you happen to have a dual boot system you can check how much Linux is slower... ;)

```

# Required packages for building
sudo apt-get install build-essential libsdl1.2-dev libgl1-mesa-dev libglu1-mesa-dev

# Actually build the program
make

# Run it
./glxdragon
```


**Linux version**
[http://dl.getdropbox.com/u/963697/glxdragon.tar.lzma]("http://dl.getdropbox.com/u/963697/glxdragon.tar.lzma")

**Windows version**
[http://dl.getdropbox.com/u/963697/glxdragon.win.zip]("http://dl.getdropbox.com/u/963697/glxdragon.win.zip")

---

### Post by Chemical Imbalance on 2009-03-29
Looks good, I'll have to give it a try sometime.  It'd be awesome if you could package a .deb for it.

---

### Post by TrueTom on 2009-03-29
Yeah, I have to look into packaging sometime. But building is actually quite simple: Just download it, unzip it and type 'make'. It just compiles one file and takes about second or so...

---

### Post by Chemical Imbalance on 2009-03-29
> **TrueTom said:**
> Yeah, I have to look into packaging sometime. But building is actually quite simple: Just download it, unzip it and type 'make'. It just compiles one file and takes about second or so...

Oh, I know.  It would be nice though :).

---

### Post by hikaricore on 2009-03-29
> **TrueTom said:**
> Yeah, I have to look into packaging sometime. But building is actually quite simple: Just download it, unzip it and type 'make'. It just compiles one file and takes about second or so...

You overestimate the ability of some of our less than stellar members to follow simple instructions.  ^_^
(for example most won't know to extract an lzma file with 7z)

> GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION  : 3.0.0 NVIDIA 185.13

1.8 seconds for 180 frames = 98.9 FPS
1.9 seconds for 180 frames = 95.7 FPS
1.8 seconds for 180 frames = 100.6 FPS
1.8 seconds for 180 frames = 98.4 FPS
1.8 seconds for 180 frames = 98.4 FPS
1.8 seconds for 180 frames = 101.7 FPS


^ hehe yay

---

### Post by Chemical Imbalance on 2009-03-29
> **hikaricore said:**
> You overestimate the ability of some of our less than stellar members to follow simple instructions.  ^_^

Are you referring to me?  That was pretty rude for a moderator.

It would be nice for new users to have a one-click deb to install and be able to easily find with synaptic to uninstall.
Debs are definitely a better option than compiling.  Compiled apps aren't easily found after you forget about them and can clog your system.

---

### Post by hikaricore on 2009-03-29
> **Chemical Imbalance said:**
> Are you referring to me?  That was pretty rude for a moderator.

No i wasn't talking about you... geez lighten up. :guitar:

---

### Post by binbash on 2009-03-29
Nice job ! Please some1 make a deb :)

---

### Post by kaivalagi on 2009-03-29
Works like a charm...

```

GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GTS/PCI/SSE2
GL_VERSION  : 2.1.2 NVIDIA 177.82

1.6 seconds for 180 frames = 114.6 FPS
1.5 seconds for 180 frames = 119.2 FPS
1.5 seconds for 180 frames = 120.0 FPS
1.4 seconds for 180 frames = 125.0 FPS
1.5 seconds for 180 frames = 122.4 FPS

```

Now to boot up that dusty old XP install to compare with :)

It'll be interesting to see if any speed improvements come with future versions of the nvidia drivers

Thanks!

P.S. IMHO If someone can't build and use this tool based on the simple instructions in the first post they don't deserve use of it. It took me less than a minute to compile it, that's including downloading the dependencies...

---

### Post by wingnux on 2009-03-29
I've encountered a problem while trying to build it on Intrepid 32bit:

> wingnux@wingnux-desktop ~/Downloads/glxdragon $ sudo apt-get install build-essential libsdl1.2-dev libgl1-mesa-dev libglu1-mesa-dev
[sudo] password for wingnux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libsdl1.2-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libgl1-mesa-dev set to manually installed.
libglu1-mesa-dev is already the newest version.
libglu1-mesa-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wingnux@wingnux-desktop ~/Downloads/glxdragon $ make
gcc -O2 -Wall -I/usr/include/SDL -o glxdragon glxdragon.cpp -lSDL -lGL -lGLU
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [glxdragon] Error 1

---

### Post by TrueTom on 2009-03-30
I checked the package of *libgl1-mesa-dev* for Intrepid, it should install the necessary files. To check it, you can use this, it should output a file or symlink called *libGL.so*:

```
ls /usr/lib/libGL.* -l
```

---

### Post by wingnux on 2009-03-30
Here's the output:

> wingnux@wingnux-desktop ~ $ ls /usr/lib/libGL.* -l
lrwxrwxrwx 1 root root     15 2009-03-02 02:49 /usr/lib/libGL.so.1 -> libGL.so.180.11
-rw-r--r-- 1 root root 701784 2009-01-06 19:02 /usr/lib/libGL.so.180.11


---

### Post by kaivalagi on 2009-03-30
> **wingnux said:**
> Here's the output:

Here's what I have with a working compile:

```
ls /usr/lib/libGL.* -l
lrwxrwxrwx 1 root root     10 2009-03-29 21:09 /usr/lib/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root     15 2009-01-07 08:09 /usr/lib/libGL.so.1 -> libGL.so.177.82
-rw-r--r-- 1 root root 830176 2008-12-07 20:15 /usr/lib/libGL.so.177.82

```

Looks like you need to add a symlink for libGL.so.1

run the following to add it:

```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so
```

Fingers crossed you compile will complete after this

---

### Post by wingnux on 2009-03-30
Thank you very much!

> GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GS/PCI/SSE2/3DNOW!
GL_VERSION  : 2.1.2 NVIDIA 180.11

2.5 seconds for 180 frames = 71.4 FPS
2.5 seconds for 180 frames = 73.5 FPS
2.4 seconds for 180 frames = 75.0 FPS
2.5 seconds for 180 frames = 72.9 FPS
2.4 seconds for 180 frames = 74.4 FPS


Cool, I've just updated the nvidia driver and got a nice speed boost!

> GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GS/PCI/SSE2/3DNOW!
GL_VERSION  : 3.0.0 NVIDIA 185.13

2.2 seconds for 180 frames = 82.9 FPS
2.1 seconds for 180 frames = 84.9 FPS
2.0 seconds for 180 frames = 90.5 FPS
2.1 seconds for 180 frames = 85.7 FPS
2.1 seconds for 180 frames = 86.1 FPS
2.1 seconds for 180 frames = 87.4 FPS


Both test results were achieved with compiz-fusion turned on.

---

### Post by kaivalagi on 2009-03-31
Good to see the performance actually improving with a new version of drivers :)

---

### Post by SGAZ on 2009-03-31
Cool tool.  I don't have a dual boot but it is nice to see the Windows tool runs and outputs identically.

Here are some numbers for **ATI **folks:
[INDENT]**Compiz**:
sgaz@sgaz-desktop:~/glxdragon$ ./glxdragon
GL_VENDOR   : ATI Technologies Inc.
GL_RENDERER : ATI Radeon HD 3850
GL_VERSION  : 2.1.8087 Release

1.3 seconds for 180 frames = 135.3 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 145.2 FPS
1.3 seconds for 180 frames = 142.9 FPS
1.2 seconds for 180 frames = 146.3 FPS
1.2 seconds for 180 frames = 146.3 FPS
1.3 seconds for 180 frames = 139.5 FPS
1.2 seconds for 180 frames = 145.2 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.3 seconds for 180 frames = 141.7 FPS[/INDENT]

[INDENT]**Metacity:** 
sgaz@sgaz-desktop:~/glxdragon$ ./glxdragon
GL_VENDOR   : ATI Technologies Inc.
GL_RENDERER : ATI Radeon HD 3850
GL_VERSION  : 2.1.8087 Release

1.3 seconds for 180 frames = 140.6 FPS
1.2 seconds for 180 frames = 145.2 FPS
1.3 seconds for 180 frames = 136.4 FPS
1.3 seconds for 180 frames = 137.4 FPS
1.3 seconds for 180 frames = 137.4 FPS
1.3 seconds for 180 frames = 137.4 FPS
1.3 seconds for 180 frames = 141.7 FPS
1.5 seconds for 180 frames = 116.9 FPS
1.3 seconds for 180 frames = 142.9 FPS[/INDENT]

---

### Post by hikaricore on 2009-04-18
Up a bit with the new Nvidia 185.19 driver.

> [hikaricore@devistate:/media/devistate/glxdragon (4.8 Mb)]$ glxdragon
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION  : 3.0.0 NVIDIA 185.19

1.8 seconds for 180 frames = 102.9 FPS
1.7 seconds for 180 frames = 104.7 FPS
1.7 seconds for 180 frames = 105.3 FPS
1.7 seconds for 180 frames = 105.9 FPS
1.7 seconds for 180 frames = 106.5 FPS
1.7 seconds for 180 frames = 104.0 FPS
1.8 seconds for 180 frames = 102.9 FPS


---

### Post by hikaricore on 2009-04-18
Seems the author's original link has gone dead, repost here: [http://www.mediafire.com/download.php?mmgwuzjzymo](http://www.mediafire.com/download.php?mmgwuzjzymo)
I'm just linking it so don't bug me about it. :p

---

### Post by Mr. Picklesworth on 2009-04-19
I'd be interested to see a direct comparison of performance for the Windows and Linux versions :)

Here's my awesome output!

```
dmccall@dylan-laptop ~/Desktop/glxdragon
 % ./glxdragon 
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600M GT/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.44

1.4 seconds for 180 frames = 126.8 FPS
1.3 seconds for 180 frames = 134.3 FPS
1.4 seconds for 180 frames = 133.3 FPS
1.3 seconds for 180 frames = 134.3 FPS
1.4 seconds for 180 frames = 133.3 FPS
1.3 seconds for 180 frames = 135.3 FPS
1.3 seconds for 180 frames = 134.3 FPS
1.3 seconds for 180 frames = 135.3 FPS
1.3 seconds for 180 frames = 134.3 FPS
1.5 seconds for 180 frames = 121.6 FPS

```

Really interesting that it's going faster than hikaricore's desktop 8600 GT. Things must have really improved with Jaunty... or it's not as precise as we're hoping ;)
I'm running Metacity with compositing as my window manager, and not much in the background, for what it's worth.

---

### Post by TrueTom on 2009-04-19
Please note that the results get somewhat imprecise on high-end video cards due to the short sampling time. I still have to fix that.

---

### Post by Nevon on 2009-04-19
I got some very... Interesting results. 

```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.2

41.6 seconds for 180 frames = 4.3 FPS
25.6 seconds for 180 frames = 7.0 FPS
0.5 seconds for 180 frames = 333.3 FPS
0.5 seconds for 180 frames = 346.2 FPS
0.6 seconds for 180 frames = 327.3 FPS
0.5 seconds for 180 frames = 375.0 FPS
0.5 seconds for 180 frames = 360.0 FPS
0.5 seconds for 180 frames = 352.9 FPS
0.5 seconds for 180 frames = 360.0 FPS
0.5 seconds for 180 frames = 333.3 FPS
0.6 seconds for 180 frames = 321.4 FPS
0.5 seconds for 180 frames = 360.0 FPS
0.5 seconds for 180 frames = 375.0 FPS
2.0 seconds for 180 frames = 90.0 FPS
0.6 seconds for 180 frames = 321.4 FPS
0.5 seconds for 180 frames = 360.0 FPS
0.5 seconds for 180 frames = 333.3 FPS
0.5 seconds for 180 frames = 339.6 FPS
0.5 seconds for 180 frames = 383.0 FPS
0.5 seconds for 180 frames = 375.0 FPS
0.6 seconds for 180 frames = 305.1 FPS
0.5 seconds for 180 frames = 375.0 FPS
0.5 seconds for 180 frames = 383.0 FPS
0.5 seconds for 180 frames = 400.0 FPS
0.5 seconds for 180 frames = 367.3 FPS
0.5 seconds for 180 frames = 375.0 FPS
0.5 seconds for 180 frames = 360.0 FPS
0.5 seconds for 180 frames = 391.3 FPS
```

The extreme increase in fps was when I moved the dragon thingy over to the other workspace. I'm guessing that was cheating... Also, why the heck do I get like 4 and 7 fps? It's not like my graphics card sucks. Sure, it's integrated Intel, but I can run games like Oblivion in Windows without too much lag. :S

---

### Post by TrueTom on 2009-04-19
> **Nevon said:**
> Also, why the heck do I get like 4 and 7 fps? It's not like my graphics card sucks. Sure, it's integrated Intel, but I can run games like Oblivion in Windows without too much lag. :S

I have the same video card and get 15 FPS under windows. That's the current state of the Linux Intel driver...

---

### Post by Nevon on 2009-04-19
> **TrueTom said:**
> I have the same video card and get 15 FPS under windows. That's the current state of the Linux Intel driver...

Wow. That's sad. :(

---

### Post by hugmenot on 2009-08-06
Why do I get so much better values than you guys on Intel?
Is it because my driver and mesa is newer, or is it the hardware?

```
$ ./glxdragon 
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION  : 2.1 Mesa 7.6-devel

5.7 seconds for 180 frames = 31.4 FPS
5.6 seconds for 180 frames = 32.0 FPS
5.6 seconds for 180 frames = 32.3 FPS
5.5 seconds for 180 frames = 32.4 FPS
```

---

### Post by CharmyBee on 2009-08-06
Did anyone say anything about ATI drivers being bad? :D

Linux:
```

GL_VENDOR   : ATI Technologies Inc.
GL_RENDERER : ATI Radeon HD 3850
GL_VERSION  : 2.1.8575

1.3 seconds for 180 frames = 140.6 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 148.8 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 148.8 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 148.8 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 148.8 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 148.8 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 147.5 FPS
1.2 seconds for 180 frames = 145.2 FPS
1.2 seconds for 180 frames = 147.5 FPS

```

Windows:
to come in the next edit of this post **if i can find it.**

---

### Post by BigSilly on 2009-08-06
My results:

```
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 9800 GT/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.44

2.6 seconds for 180 frames = 70.3 FPS
2.4 seconds for 180 frames = 75.3 FPS
2.4 seconds for 180 frames = 76.6 FPS
2.2 seconds for 180 frames = 81.8 FPS
2.2 seconds for 180 frames = 81.4 FPS
2.2 seconds for 180 frames = 82.2 FPS
2.2 seconds for 180 frames = 82.2 FPS
2.2 seconds for 180 frames = 82.6 FPS
2.2 seconds for 180 frames = 81.8 FPS
2.2 seconds for 180 frames = 81.4 FPS
2.2 seconds for 180 frames = 81.8 FPS
2.2 seconds for 180 frames = 81.4 FPS
2.2 seconds for 180 frames = 81.1 FPS
2.2 seconds for 180 frames = 81.4 FPS
2.2 seconds for 180 frames = 81.8 FPS
2.2 seconds for 180 frames = 81.8 FPS
2.2 seconds for 180 frames = 81.1 FPS
2.2 seconds for 180 frames = 80.7 FPS
```

Still using the older driver. Though I don't usually upgrade until it turns up in the repo!

---

### Post by kaivalagi on 2009-08-06
> **kaivalagi said:**
> Works like a charm...

```

GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GTS/PCI/SSE2
GL_VERSION  : 2.1.2 NVIDIA 177.82

1.6 seconds for 180 frames = 114.6 FPS
1.5 seconds for 180 frames = 119.2 FPS
1.5 seconds for 180 frames = 120.0 FPS
1.4 seconds for 180 frames = 125.0 FPS
1.5 seconds for 180 frames = 122.4 FPS

```

Now to boot up that dusty old XP install to compare with :)

It'll be interesting to see if any speed improvements come with future versions of the nvidia drivers

Thanks!

P.S. IMHO If someone can't build and use this tool based on the simple instructions in the first post they don't deserve use of it. It took me less than a minute to compile it, that's including downloading the dependencies...

The newer drivers have a positive effect (just), I have the exact same hardware as before

```
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GTS/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.44

1.5 seconds for 180 frames = 121.6 FPS
1.5 seconds for 180 frames = 120.8 FPS
1.4 seconds for 180 frames = 125.9 FPS
1.5 seconds for 180 frames = 122.4 FPS
1.4 seconds for 180 frames = 125.0 FPS
```

---

### Post by CharmyBee on 2009-08-23
Bump, just tried the newer 9.8's. Nice framerate jump here:

```

GL_VENDOR   : ATI Technologies Inc.
GL_RENDERER : ATI Radeon HD 3850
GL_VERSION  : 2.1.8870

1.2 seconds for 180 frames = 153.8 FPS
1.1 seconds for 180 frames = 156.5 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 162.2 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 166.7 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 162.2 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 162.2 FPS
1.1 seconds for 180 frames = 163.6 FPS
1.1 seconds for 180 frames = 165.1 FPS
1.1 seconds for 180 frames = 163.6 FPS

```

---

### Post by hikaricore on 2009-10-18
> **hikaricore said:**
> Seems the author's original link has gone dead, repost here: [http://www.mediafire.com/download.php?mmgwuzjzymo](http://www.mediafire.com/download.php?mmgwuzjzymo)
I'm just linking it so don't bug me about it. :p


Updated mirror, the author really should update his post with a working link.
[http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar](http://www.mediafire.com/file/wjzozg0mgth/glxdragon.tar)

---

### Post by TrueTom on 2009-10-19
**Windows**
```
GL_VENDOR   : Intel
GL_RENDERER : Intel 945GM
GL_VERSION  : 1.4.0 - Build 7.14.10.4926

12.1 seconds for 180 frames = 14.9 FPS
```

**Linux (Jaunty Jackalope)**
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090114 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.3

37.8 seconds for 180 frames = 4.8 FPS
```

**Linux (Karmic Koala)**
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.7-devel

23.4 seconds for 180 frames = 7.7 FPS

```

---

### Post by joeelmex on 2009-10-19
This is cool I will post mine tonight when I get home.  Thanks for the great work on this.

---

### Post by joeelmex on 2009-10-20
Sorry I didn't do it yesterday but started playing Wow with my friends.  Here are my results:

```

GL_RENDERER : GeForce 9800M GS/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 185.18.36

1.1 seconds for 180 frames = 171.4 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 174.8 FPS
1.1 seconds for 180 frames = 166.7 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 174.8 FPS
1.0 seconds for 180 frames = 174.8 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 174.8 FPS
1.1 seconds for 180 frames = 171.4 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 178.2 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.0 seconds for 180 frames = 176.5 FPS
1.1 seconds for 180 frames = 171.4 FPS
1.0 seconds for 180 frames = 173.1 FPS
1.0 seconds for 180 frames = 173.1 FPS

```

I will update these results as I update my drivers.  thanks

---

### Post by cajual on 2009-10-20
```
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 9800 GTX/9800 GTX+/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 185.18.36

1.0 seconds for 180 frames = 178.2 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 185.6 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 183.7 FPS
1.0 seconds for 180 frames = 180.0 FPS

```Not a bad program...

---

