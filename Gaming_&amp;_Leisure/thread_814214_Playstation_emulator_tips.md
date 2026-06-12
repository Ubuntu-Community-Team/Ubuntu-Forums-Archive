---
title: "Playstation emulator tips"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by MdaG on 2008-05-31
Hi!

I was wondering which Playstation emulator you recommend for playing on 8.04. I've tried PCSX, but it doesn't seem to respond to keyboard input and just keeps repeating whatever intro is running when I load a ISO.

---

### Post by Grishka on 2008-05-31
> **MdaG said:**
> Hi!

I was wondering which Playstation emulator you recommend for playing on 8.04. I've tried PCSX, but it doesn't seem to respond to keyboard input and just keeps repeating whatever intro is running when I load a ISO.

the easiest to use is psx: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/). there's also ePSXe: [http://www.epsxe.com](http://www.epsxe.com), but you'll need to spend some time installing and configuring plugins with this one.

---

### Post by MdaG on 2008-05-31
> **Grishka said:**
> the easiest to use is psx: [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/). there's also ePSXe: [http://www.epsxe.com](http://www.epsxe.com), but you'll need to spend some time installing and configuring plugins with this one.

I assume none of these are available as packages in Adept? (Couldn't find them)
I've downloaded and extracted PSX, but according to the readme it needs:
> Under Linux pSX requires the following shared libraries/packages :

        OpenGL
        ALSA
        GTK
        GTKGLEXT
        libxml2

Is there a package I can download in Adept that sets this up or is the only way to download the files individually?

---

### Post by Grishka on 2008-05-31
> **MdaG said:**
> I assume none of these are available as packages in Adept? (Couldn't find them)
I've downloaded and extracted PSX, but according to the readme it needs:

Is there a package I can download in Adept that sets this up or is the only way to download the files individually?

try to run it from the terminal and see what it complains about, then look for the needed libraries in adept. or you can try using packages from [http://webhop.dfreer.org:8080/](http://webhop.dfreer.org:8080/), it will handle the dependencies by itself.

---

### Post by acoustibop on 2008-05-31
You can cd into your new pSX folder and do```
ldd ./pSX
```to find what dependencies are missing, MdaG.  However, most of those libraries are part of a standard Ubuntu installation.  The only one that isn't is GTKGLEXT: if you do```
apt-get install libgtkglext1
```that should do it.

---

### Post by MdaG on 2008-05-31
I tried installing the appropriate package according to:
```
$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```
However the only library I found in Adept was *libgtkglext-x11-1.2* and *libgtkglext1*. After installing the package I still get the same message when I try to run pSX from the terminal. Any idea, I'm aware that the version requested is 1.0 and not 1.2...?

*edit*
Reading up on the net I see that this might be because of me running the 64-bit version of Kubuntu...

*edit*
Why isn't there a Ubuntu package for pSX?

---

### Post by acoustibop on 2008-05-31
You'll need to install a 32bit version of libgtkglext1, then, MdaG.  See dfreer's very useful [How-To: install pSX on AMD64/i386 thread]("http://ubuntuforums.org/showthread.php?t=394097") - he also maintains a repository with pSX packages.

---

### Post by MdaG on 2008-06-01
> **acoustibop said:**
> You'll need to install a 32bit version of libgtkglext1, then, MdaG.  See dfreer's very useful [How-To: install pSX on AMD64/i386 thread]("http://ubuntuforums.org/showthread.php?t=394097") - he also maintains a repository with pSX packages.

Thank you!
Though his repository didn't seem to work, I did manage to download the software and with the use of getlib I fetched the appropriate libraries for it. It works fine now. :D

---

### Post by proactivedarwin on 2008-12-08
I'm still cant load psx, it gives me this error:

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

please help

---

### Post by dfreer on 2008-12-09
proactivedarwin:
You need to kill/stop pulseaudio before you run pSX. This is one way to do it:
```
sudo killall pulseaudio
```

As for the others in this thread that tried to use my repository, sorry about it not working. Even though this thread is somewhat old, I have since posted packages of pSX for ubuntu 8.04 and 8.10, both 32 and 64 bit versions in that thread that you are welcome to use.

---

