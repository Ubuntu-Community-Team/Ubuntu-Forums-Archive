---
title: "No sound in ZSNES, &quot;unable to open slave&quot;"
date: 2008-04-27
forum: Gaming &amp; Leisure
---

### Post by ParanoidArtemus on 2008-04-27
Hey there everybody. I have yet another ZSNES sound issue. The issue is... I have none. :)

I ran it in terminal and this is what came up. Can anyone help me? Thanks ahead of time.

```
Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA snd_pcm_open error: Device or resource busy
Audio Open Failed
ZSNES could not find any joysticks.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
michael@michael-laptop:~$ 

```

---

### Post by acoustibop on 2008-04-28
First install libsdl1.2debian-all, ParanoidArtemus (in the repositories).  It'll uninstall libsdl1.2debian-alsa but don't worry; alsa support is included as part of the libsdl1.2debian-all package.

Then do 'zsnes --help' to get a list of sound drivers that ZSNES can use, and try each one with 'zsnes -ad <sound driver>'

When you've found the one that works best, edit your ~/.zsnes/zsnesl.cfg and insert the driver that works for 'libAoDriver'

---

### Post by eyecreate on 2008-08-08
no matter if I use libsdl for all or pulseaudio or alsa, etc, I cannot get any sound. zsnes says I only have sdl as an audio driver. I am running 64bit, which may be a part of the problem. Everything else works fine, and zsnes on my 32bit machine works fine. And ideas?

---

### Post by grossaffe on 2008-08-08
As I always suggest in these SNES related threads, get the GTK port of SNES9x.  It has a 64 bit version and works great.  you won't regret it.

---

### Post by eyecreate on 2008-08-08
Thanks, so far that version seems to work great. Hope things stay that way. I'd still love zsnes to work, though.

---

### Post by Yellow Pasque on 2008-08-09
On 32-bit, You can get it to work without sound by using zsnes -ad null.

Better yet, install ALSA's OSS wrapper and the oss version of sdl.
```
sudo apt-get install libsdl1.2debian-oss alsa-oss
```

On amd64 arch, I've built a .deb by hacking the 386 .deb. I replaced the zsnes binary with the K8-optimized build by Nach on the zsnes forums and you can use getlibs to install the appropriate 32-bit libraries like so:
```
cd ~/
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libao2 libc6 libgcc1 libgl1-mesa-glx libpng12-0 alsa-oss libsdl1.2debian-oss libstdc++6 zlib1g
```

PM me your e-mail if you're interested in the 64-bit .deb

---

### Post by thrasher6900 on 2008-08-11
> **Temüjin said:**
> On 32-bit, You can get it to work without sound by using zsnes -ad null.

Better yet, install ALSA's OSS wrapper and the oss version of sdl.
```
sudo apt-get install libsdl1.2debian-oss alsa-oss
```

On amd64 arch, I've built a .deb by hacking the 386 .deb. I replaced the zsnes binary with the K8-optimized build by Nach on the zsnes forums and you can use getlibs to install the appropriate 32-bit libraries like so:
```
cd ~/
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -p libao2 libc6 libgcc1 libgl1-mesa-glx libpng12-0 alsa-oss libsdl1.2debian-oss libstdc++6 zlib1g
```

PM me your e-mail if you're interested in the 64-bit .debI tried this and still I cannot get any sound as well.

Is there some setting that I'm doing wrong?  I've tried all the setting and they don't work (I was using the gui front end)

---

### Post by thrasher6900 on 2008-08-11
> **grossaffe said:**
> As I always suggest in these SNES related threads, get the GTK port of SNES9x.  It has a 64 bit version and works great.  you won't regret it.
There's like no features on it, unless there is a different version in synaptic that I don't know of.

links?

---

### Post by grossaffe on 2008-08-11
> **thrasher6900 said:**
> There's like no features on it, unless there is a different version in synaptic that I don't know of.

links?

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)

---

### Post by bigdee973 on 2008-08-20
open terminal

zsnes -ad sdl

sound should work from now on

---

### Post by Master O on 2008-08-20
Would this help?:

[For Users having sound problems with ZSNES and Hardy](http://ubuntuforums.org/showthread.php?p=5332137)

---

