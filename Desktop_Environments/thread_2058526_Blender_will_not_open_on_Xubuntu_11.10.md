---
title: "Blender will not open on Xubuntu 11.10"
date: 2012-09-15
forum: Desktop Environments
---

### Post by gorellana09 on 2012-09-15
Hello folks I hope someone here can help me. I have been using Linux Mint for a little over 2 years now and have gotten used to it. However because of some kernel and compatibility problems I had to install Xubuntu 11.10.

Now my problem is that I need to install blender 2.63a which is the latest. I have downloaded it and unpacked it to my home folder as I have always done in Mint. But on Xubuntu 11.10 blender will not open. Clicking on the blender shortcut does nothing and running it from the terminal gives me this error.

```

geo@geo-HP:~/blender-2.63a$ ./blender
./blender: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

```

Installing from the repo is not an option for me since the one on it is a very very old version. Due to some new features that I need it has to be 2.63a. 

Also I know there are some 3rd party ppas out there but those only seem to install nightly builds which is also not an option for me as I cannot risk using nightly build stuff that breaks often on this production machine. 

If anyone can help me it would be greatly appreciated.

---

### Post by Toz on 2012-09-16
libSDL-1.2.so.0 is part of the **libsdl1.2debian** package. Make sure you have it installed.

```
$ apt-file search libSDL-1.2.so.0
libsdl1.2debian: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
libsdl1.2debian: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0.11.3

```

---

### Post by gorellana09 on 2012-09-16
Thanks for your response. It seems to be installed as I get this:

```

eo@geo-HP:~$ apt-file search libSDL-1.2.so.0
libsdl1.2debian-all: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-all: /usr/lib/libSDL-1.2.so.0.11.3
libsdl1.2debian-alsa: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-alsa: /usr/lib/libSDL-1.2.so.0.11.3
libsdl1.2debian-esd: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-esd: /usr/lib/libSDL-1.2.so.0.11.3
libsdl1.2debian-nas: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-nas: /usr/lib/libSDL-1.2.so.0.11.3
libsdl1.2debian-oss: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-oss: /usr/lib/libSDL-1.2.so.0.11.3
libsdl1.2debian-pulseaudio: /usr/lib/libSDL-1.2.so.0
libsdl1.2debian-pulseaudio: /usr/lib/libSDL-1.2.so.0.11.3


```

Any idea what I should do?

---

### Post by gorellana09 on 2012-09-16
Correction Synaptic showed it was not installed. Just installed it and Blender is working fine now. Man I could hug you right now. Thanks for the help! :D

---

### Post by gorellana09 on 2012-09-16
I know I just marked this as SOLVED but hopefully someone can see this. Blender does open now but when I close it, it continues to run in the background taking up CPU and I have to manually kill the process. Any idea why this is going on?

---

