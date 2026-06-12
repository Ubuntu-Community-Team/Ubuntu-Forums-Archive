---
title: "Kubuntu 11.10 switch -- No desktop effects? Ubuntu One?"
date: 2012-01-01
forum: Desktop Environments
---

### Post by spielball on 2012-01-01
Hello, I'm currently thinking about switching to Kubuntu 11.10. Burned a Live DVD in order to try it. I like KDE 4.7 a lot. I'd like to install it. However, I have two questions:

1. When trying the Live DVD, application windows have no shadows. Is this because it's the Live DVD? My graphics card is an integrated Intel HD.

2. Can I use Ubuntu One in Kubuntu 11.10? So far, I only found an outdated alpha client that is broken. Is or will there be a client for Kubuntu?

Thank you in advance!

---

### Post by schnelle on 2012-01-01
1) Probably desktop effects were disabled. Sometimes they don't work out of box (kwin settings get corrupted somehow) so you have to remove *kwinrc* file from *~/.kde/share/config* and then hit alt+f2 and type *kwin --replace* . Kwin will be back to its default and effects should work.

2) I know nothing about Ubuntu One. Sorry.

---

### Post by giowck on 2012-01-01
for ubuntu one see [http://askubuntu.com/questions/58983/how-do-i-install-ubuntu-one-in-kubuntu](http://askubuntu.com/questions/58983/how-do-i-install-ubuntu-one-in-kubuntu)

---

### Post by 2F4U on 2012-01-01
You can try to enable desktop effects in the liveCD. They should be enabled by default. If your graphics card is not capable of displaying desktop effects, KDE will let you know. KDE usually tells you which effects don't work and you could try enabling some of the others.

---

### Post by oldos2er on 2012-01-01
> **spielball said:**
> 2. Can I use Ubuntu One in Kubuntu 11.10? So far, I only found an outdated alpha client that is broken. Is or will there be a client for Kubuntu?


I haven't tried it myself, but you should be able to install and run the gtk Ubuntu One software on Kubuntu.

As for a native KDE Ubuntu One client, see [https://bugs.launchpad.net/ubuntuone-client/+bug/375145](https://bugs.launchpad.net/ubuntuone-client/+bug/375145)

> **giowck said:**
> for ubuntu one see [http://askubuntu.com/questions/58983...one-in-kubuntu](http://askubuntu.com/questions/58983...one-in-kubuntu)

Looks like that only applies to Maverick and older releases.

---

### Post by inobe on 2012-01-01
> **spielball said:**
> 
1. When trying the Live DVD, application windows have no shadows. Is this because it's the Live DVD? My graphics card is an integrated Intel HD.


> The minimum system requirements for a desktop installation are a 300 MHz x86 processor, 512 MB of RAM, 5 GB of hard drive space, and a video card which supports VGA at 640x480 resolution. The recommended system requirements for the desktop installation are a 1 GHz or better x86 processor, 1 GB of RAM, 15 GB of hard drive space, and a video card which supports VGA at 1024×768 resolution, **and optionally supporting visual effects**.

those specs are the lowest you can go.

i suggest a minimum of 3ghz pentium 4 cpu, 2 gigs ddr memory, nvidia 6600gt, 16gig hard drive.

intel and ati/ amd cards are known for consistent problems.

you can try, the intel driver may give you some affects, just don't expect anything extreme.

---

### Post by spielball on 2012-01-02
Thanks for all the replies. I guess I'll have to make a test installation and then fiddle around with it. By the way, my computer is not that old. My processor an Intel P6200 Dual Core 2.1GHz with and integrated Intel HD. I suppose that should be by far enough to have shadows under my application windows as desktop effects. I just wondered why there aren't any. Don't need no 3d cubes and stuff. I simply want shadows. Maybe it's a driver issue as for the live DVD which might just use generic drivers. So, I guess I have to install it.

---

### Post by spielball on 2012-01-04
Hello, I'm running a test install now. Kubuntu works fine. The 'shadows' are actually some sort of illuminating effect around the application windows borders. Also, the windows are half-transparent when dragging them around. Everything looks nice and clean. I like that Plasma desktop stuff very much. And as for how KDE is organized, it feels better than Unity so far. But let's see. Both paradigms have their advantages and disadvantages I guess. Even though I never really started to like Unity, but got used to it. KDE is better though, I have a feeling.

---

