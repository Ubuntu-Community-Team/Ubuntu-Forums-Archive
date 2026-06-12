---
title: "Mupen64plus choppy sound"
date: 2010-03-01
forum: Gaming &amp; Leisure
---

### Post by Pastinakel on 2010-03-01
I'v got a strange and very annoying problem with mupen64plus: the system I want to use it on most games run fine but some are stuttering with choppy sound. *Mario Kart* runs fine mostly (some crackling sound) but *Hot Weels Turbo Racing* runs slow, choppy with interupted sound, especially when there is more then one car in sight.

System: Asrock ION 330, Intel Atom N330, Ubuntu 9.10, Kernel 2.6.31-19-generic #56-Ubuntu SMP Arch: x86_64 GNU/Linux

What I tried:

Different versions of mupen64plus: 1.5, 1.99-1, 1.99-3 and compile from hg: no difference, same sound problems.

Different SDL solutions:
I have tried libsdl1.2debian-alsa, libsdl1.2debian-esd, libsdl1.2debian-oss and libsdl1.2debian-pulseaudio with the appropriate settings for $SDL_AUDIODRIVER set. No solution.

This CPU has four cores. Mupen64plus uses one of them. When the sound stutters, the cpu use of that core reaches 100 %. 

A different system with much older hardware, same 9.10 Ubuntu and AMD64 has no problems at all.

Anyone got a clue?

---

### Post by apis on 2010-03-02
I have exactly the same issue here on some old Dell OptiPlex GX400 box used as media centre. Ubuntu 9.10, external usb sound card with optical out, alsa (need to pass-through digital pcm stream from xbmc to receiver and it is not supported by pulseaudio). Sound perfectly works in xbmc and zsnes - no sound issues! 
In mupen64plus sound is choppy/very choppy. I tried mupen64plus 1.99-3 binaries or compiled from hg. Was playing with settings in ~/.config/mupen64plus/mupen64plus.cfg. Tried any possible setting there like DEFAULT_FREQUENCY, buffers, RESAMPLE (btw SINC resample only works in hg version, and fails in binary version). But it doesn't change anything, sound still unbearable. Tried different libsdl1.2 debs as well it didn't work for me either. 
I almost gave up on this, but now I see I am not alone.

---

### Post by Ghost|BTFH on 2010-03-02
My guess would be an issue with PulseAudio.  There are plenty of how-tos for "fixing" it or ripping its guts out and replacing it with ALSA.  Pick your poison, my bet is it'll resolve your issues.

Cheers,
Ghost|BTFH

---

### Post by apis on 2010-03-02
> **Ghost|BTFH said:**
> My guess would be an issue with PulseAudio.  There are plenty of how-tos for "fixing" it or ripping its guts out and replacing it with ALSA.  Pick your poison, my bet is it'll resolve your issues.

In my case I replaced pulseaudio with alsa because of the pcm pass-through issues in xbmc. But even with alsa I still have choppy sound with mupen64plus.

---

### Post by Ghost|BTFH on 2010-03-02
> **apis said:**
> In my case I replaced pulseaudio with alsa because of the pcm pass-through issues in xbmc. But even with alsa I still have choppy sound with mupen64plus.

The only other thing I can think of would be an issue with the onboard sound.

An Asrock motherboard is not exactly good quality and the onboard sound could be having issues.  Have you run Windows on this box w/o a problem?

Cheers,
Ghost|BTFH

---

### Post by Pastinakel on 2010-03-03
> **Ghost|BTFH said:**
> The only other thing I can think of would be an issue with the onboard sound.

An Asrock motherboard is not exactly good quality and the onboard sound could be having issues.  Have you run Windows on this box w/o a problem?

Cheers,
Ghost|BTFH

Yes I did. It ran flawlessly. No other app is giving sound problems.

I have a reply from Richard on the mupen64plus google group: [http://groups.google.com/group/mupen64plus/t/158ed8f473acf2ff](http://groups.google.com/group/mupen64plus/t/158ed8f473acf2ff)

> Sorry, but your CPU just isn't fast enough to run all the games at full speed.
 That Atom 330 is actually impressive for only 8 watts of power, but it's much
simpler and less capable than desktop CPUs.  Mupen64Plus only uses 1 CPU, so
it can't take advantage of the multiple cores.  One thing that you can do to
get more performance is use the 32-bit version of Mupen64Plus, because it is
somewhat faster than the 64-bit version.

Richard

I haven't tried that 32 bit version yet.

---

### Post by Ghost|BTFH on 2010-03-03
Now that's a surprise - I would have expected something with a quad core to have some power behind it.

Well, knowledge gained on this one. Atom processors are cute and low power - figuratively and literally! :)

Cheers,
Ghost|BTFH

---

### Post by apis on 2010-03-03
> **Pastinakel said:**
> Yes I did. It ran flawlessly. No other app is giving sound problems.

I have a reply from Richard on the mupen64plus google group: [http://groups.google.com/group/mupen64plus/t/158ed8f473acf2ff](http://groups.google.com/group/mupen64plus/t/158ed8f473acf2ff)



I haven't tried that 32 bit version yet.

Pastinakel can you try to run windows version of mupen64plus on your box and see if you have any issues with sound? If you don't it is not a problem with CPU speed but rather some Linux/configuration issue. 

Unfortunately it very problematic to install windows on my box. 

I have really big doubts that this is CPU speed issue since video works flawlessly and sound not. Sound by definition should take much less CPU resources than video.

---

### Post by kuric on 2010-12-24
Same problem here, but I believe it's possible to increase audio performance by changing the graphic settings.

First, Options > Configure > Choose **Glide64 Mupen64Plus**.
Then, press Config button.
**Uncheck** all options, **except** Autodetect Microcode, Vertical Sync and Fast CRC.
Buffer swapping method > old. 
Apply changes.

Hopefully, You'll notice sound will be smoother after this.

---

### Post by emoguitarist06 on 2011-01-23
> **kuric said:**
> Same problem here, but I believe it's possible to increase audio performance by changing the graphic settings.

First, Options > Configure > Choose **Glide64 Mupen64Plus**.
Then, press Config button.
**Uncheck** all options, **except** Autodetect Microcode, Vertical Sync and Fast CRC.
Buffer swapping method > old. 
Apply changes.

Hopefully, You'll notice sound will be smoother after this.

I have the same processor as Pastinakel ATOM 330 on my Asus 1201N and an Nvidia Ion (first gen) graphics and I'm running v1.5 on Ubuntu 10.10 64bit in which I installed via Software Center

I used your suggestions and I"m still having the choppy sounds.

I may try apis suggestion and trying mupen on my 32bit Windows partition
and I'll post if/when I do

Anyways just putting my two cents in

Edit: BTW How do I go about upgrading my v1.5 to 1.99.4 safely?

---

