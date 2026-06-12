---
title: "Need help installing Nvidia Drivers"
date: 2005-08-05
forum: Desktop Environments
---

### Post by glowstick on 2005-08-05
Okay, I'm totally new to linux, as in I don't know ANYTHING about linux, but the idea of linux sounded nice so I decided to download this distro and try it.

Well I downloaded the 'NVIDIA-Linux-x86-1.0-7667-pkg2.run' from the nvidia website and I don't know what do do with it.

Remember, I'm totally new to Linux so if anyone can carefully explain the steps and help me it would it be great!

Thanks in advance.

---

### Post by GavinX on 2005-08-05
I would advise that you don't travel that route. Instead, use the instructions given here [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by lman on 2005-08-05
Ok, thats for graphics.  How about for Nvidia Sound?  Any advice?

---

### Post by GavinX on 2005-08-05
[QUOTE=lman]Ok, thats for graphics.  How about for Nvidia Sound?  Any advice?[/QUOTE]
I'm not too familiar with Nvidia sound issues. Give me a little time and I'll do some resarch and get back to you.:-\"

---

### Post by GavinX on 2005-08-05
[QUOTE=lman]Ok, thats for graphics.  How about for Nvidia Sound?  Any advice?[/QUOTE]
I think I've found something which may interest you, Iman. Sheck this link. The instructions should be included also. [http://www.nvidia.com/object/linux_nforce_1.0-0301](http://www.nvidia.com/object/linux_nforce_1.0-0301)

Cheers,
GavinX

---

### Post by lman on 2005-08-06
I have amd64... and I found that link (they have a driver for amd64) and I got a lot of errors when I tried installing that.  I hoped ubuntu would include some sort of nforce sound driver... or at least there would be some open drivers that would work.  I'm surprised more people don't have this problem.. since it seems nforce does not work with alsa.

---

### Post by lman on 2005-08-06
Ok I finally got the 64 driver for nvidia working...
I modprobe nvsound.... update-modules etc.. lsmod shows nvsound there, but my sound isn't working.  I read you have to remove the snd_intel8x0 module but don't know how, and I can't find it in the modules.d files.  I'm utterly stuck. All around the web it seems people are having this problem and the ones that fix it don't seem to know how they did it.   I got ubuntu cause I thought it would fix all these problems... but at least my sound worked in debian sarge.

---

### Post by f1dave on 2005-08-06
Perhaps i'm jumping to conclusions here, but whatever you were running to have your sound working in sarge should also work here in ubuntu- they are both .deb based after all. 

Whats more, my onboard sound on my nforce2 board works fine.

---

### Post by lman on 2005-08-06
I really wish this was the case, but if it was it should have worked out of the box on ubuntu.  To get my sound to work in sarge I installed/compiled ALSA, and when I modprobed the modules, bam, it worked.  Since ubuntu runs alsa out of the box my sound should have worked out of the box.  Here's my thoughts on why it didn't.  UBUNTU DOES NOT COME WITH ALSACONF.  WHY!???  WHY!??  I don't understand.  Thats the only difference I can see between sarge and ubuntu for sound, I ran alsaconf in sarge but could not in ubuntu.  Can someone please explain what ubuntu's replacement for alsaconf is?

---

### Post by lman on 2005-08-06
Oh and I have an nforce 3 board.  Chaintech nforce3 250 to be exact.

---

### Post by mo_x on 2005-08-07
See my post in the following thread:
[http://www.ubuntuforums.org/showthread.php?t=48863](http://www.ubuntuforums.org/showthread.php?t=48863)

I currently use the snd-intel8x0 module for alsa, the (K)Ubuntu default. It works fine, I only had to adjust the sample rate for the KDE sound server to 48000 Hz. I have a nforce4 motherboard with Realtek ALC850 sound.

---

