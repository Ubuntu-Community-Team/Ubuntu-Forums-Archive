---
title: "Does Ubuntu Netbook Remix make any sense on a DualCore Atom PC with 24&quot; LCD?"
date: 2009-04-16
forum: Desktop Environments
---

### Post by Master One on 2009-04-16
I was just wondering, if the Ubuntu Netbook Remix is only about limited resources on a netbook, especially with low screen resolution, or if there are any more optimizations for the Atom platform involved.

I have a silent PC here with a DualCore Atom 330 1.6 MHz, 2GB RAM, connected to a 24" LCD with 1920x1200.

Would it make any sense, to run Ubuntu Netbook Remix instead of normal Ubuntu on that machine?

Actually I have Ubuntu Intrepid installed, it generally runs well, except that I can not playback 720p videos (which is very strange, because with an Atom 330 and Intel IGP even 1080p should be possible).

---

### Post by andrea000 on 2009-04-16
> **Master One said:**
> I was just wondering, if the Ubuntu Netbook Remix is only about limited resources on a netbook, especially with low screen resolution, or if there are any more optimizations for the Atom platform involved.

I have a silent PC here with a DualCore Atom 330 1.6 MHz, 2GB RAM, connected to a 24" LCD with 1920x1200.

Would it make any sense, to run Ubuntu Netbook Remix instead of normal Ubuntu on that machine?

Actually I have Ubuntu Intrepid installed, it generally runs well, except that I can not playback 720p videos (which is very strange, because with an Atom 330 and Intel IGP even 1080p should be possible).

If it was me i would just run ubuntu on it from the 
specs you listed sounds like you have a good system.
Your right on the videos could you post what you 
have installed on the computer.

---

### Post by Master One on 2009-04-16
It's pretty much a stock Ubuntu Intrepid installation, kept up-to-date, with additionally VLC and MPlayer installed for media playback.

Neither Totem, nor VLC or MPlayer is able to playback the 720p videos in question, it is all just jerky with massive frame loss and audio & video out of sync. These typically are of format avc1 in a matroska container. I just took a look of the info, SMplayer provides on such a file:```
Allgemein
Datei
*TESTFILE*.mkv
Größe
1145419 KB (1118 MB)
Dauer
00:42:17
Demuxer
mkv

Video
Auflösung
1280 x 720
Aspect Ratio
1.7778
Format
avc1
Bitrate
0 kbps
Bilder pro Sekunde
23.976
Verwendeter Codec
ffh264

Startwert Audio Stream
Format
8192
Bitrate
384 kbps
Samplingrate
48000 Hz
Kanäle
2
Verwendeter Codec
a52
```
I already did some reading, looks like x264 is not that easy on resources, like it is on some OS from M$. The term "CoreAVC" came up, and some instructions on how to get it going with recompiling MPlayer from SVN, but I did not fiddle around with that stuff yet.

Nevertheless, if Ubuntu Netbook Remix should be more than just about the user interface, I really would be interested in it, especially because I plan to use it on my new Asus Eee PC 901GO as well. But I guess there is not much hope for specific Atom platform optimizations, giving it no advantage over normal Ubuntu on such a machine.

---

### Post by Psychopump on 2009-04-16
The netbook remix is really for netbooks with limited screen real-estate. You have no need of it at all...IMHO.

---

### Post by Stupendoussteve on 2009-04-16
> **Psychopump said:**
> The netbook remix is really for netbooks with limited screen real-estate. You have no need of it at all...IMHO.

This is true. Something to consider with the remix is any window takes up the whole screen. You can chance windows through the menu bar, but the new window will also be full screen. I, at least, would not like this behavior on a large screen.

They say there are some optimizations for the Atom, it is unlikely to be that noticeable.

---

### Post by snowpine on 2009-04-16
Netbook Remix is simply a different interface. You can install the NBR interface on regular Ubuntu, and likewise, you can ditch the NBR interface on a NBR installation and revert to the regular Ubuntu desktop. There are no Atom-specific optimizations in Ubuntu NBR that aren't in the regular version, as far as I know.

Ubuntu also makes a port for lpia (low power intel architecture) if you want something specific for your Atom. I haven't really read many reviews of the lpia port, though--I think it is still kind of experimental. If you decide to try it, I would be curious to know your experience. :)

---

### Post by Stupendoussteve on 2009-04-16
From the Netbook-Remix page:

> All of the initial Ubuntu Netbook remixes combine optimisations from the Moblin project for Intel® Atom™ processors and it is specially designed for netbooks.

Not very specific, of course.

---

### Post by Master One on 2009-04-16
The only advantages from the Moblin project, I've read about so far, are concerning shortened boot time, which should not really be an issue, if the device properly suspends to RAM.

As long as there are no optimizations concerning march and cflags (which isn't the case, because it would require all packages to be recompiled for the Atom platform), or for the use with a solid state disk instead of a harddisk, there really seems to be no point for running NBR on anything else than a netbook.

I have never heard of the term "lpia" before, and also could not find any info concerning an Ubuntu lpia port. Any details on that?

---

### Post by snowpine on 2009-04-16
Here's where to get the latest lpia port: [http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

And a couple of threads on the topic: [http://ubuntuforums.org/showthread.php?t=1053153&highlight=lpia](http://ubuntuforums.org/showthread.php?t=1053153&highlight=lpia)
[http://ubuntuforums.org/showthread.php?t=1061907&highlight=lpia](http://ubuntuforums.org/showthread.php?t=1061907&highlight=lpia)

---

### Post by Master One on 2009-04-16
This is indeed quite interesting, although there is no lpia 64bit edition available (netbooks only have the 32bit N270 Atom, but the DualCore Atom 330 is 64bit capable), and there is not really any useful info on the differences in the mentioned threads, with even more confusion:> Others have good experiences with Ubuntu Netbook Remix (which is LPIA), though this installs with a ext3 filesystem which is very slow with slow-ish SSD units. It is best converted back to ext2 for SSD drives.and> I notice for the jaunty downloads that there is the UNR file and then there is the MID file. The UBN is not LPIA but the regular i386 or what not but the MID file is LPIA but for MID devices not netbooks. So what do we people with atom chips use? Or is there one that UNR LPIA?
I am actually running Ubuntu Intrepid 64bit on my Atom 330 machine, and I intend to use Ubuntu Netbook Remix Jaunty on my Asus Eee PC 901GO (since that one has the Atom N270).

ATM the Atom 330 machine has a regular 80GB SATA harddisk, but my idea was to swap that one for a 32GB SLC SSD, and since the lpia port shows, that the Atom is to be seen as a different architecture (much like i386 vs. amd64), I am totally unsure, where this is heading. I guess it's just best to stick with normal Ubuntu 64bit, altough optimizations for low power consumptions, use of SSD instead of HDD and full use of the 64bit capability would be preferred.

---

### Post by souta95 on 2009-04-16
As stated before, Netbook Remix is just another interface designed for use with 1024 x 600 resolution screens.  It would make little sense to use it on a full-sized screen as all windows are maximized by default, and the title bar is hidden when the window is maximized.

If you want to use fewer resources you could consider using Xubuntu/ XFCE as it is lighter on resources than Gnome, yet somewhat similar in look and feel.

---

### Post by Master One on 2009-04-17
Already used Xfce and Xubuntu, but it's not the same, there is too much functionality missing, at only a very small advantage on resource usage (if at all!).

The issue here is pretty clear now, no UNR on my Atom 330 machine, but on my Asus Eee PC 901GO.

But the question about normal Ubuntu 64bit vs. Ubuntu lpia still stays, there is just not enough info on the lpia platform, and why it's 32bit only, although there are more than just the Atom 330 with 64bit capability. I guess, if I find the time, I just have to try.

---

