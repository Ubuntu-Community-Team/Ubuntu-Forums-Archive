---
title: "What am I doing wrong?"
date: 2009-05-23
forum: General Help
---

### Post by walterp98@gmail.com on 2009-05-23
*Warning:  This post is rather long, and covers a variety of topics.*

I've always read (and believed) that linux (ubuntu in specific) would perform better on older hardware than XP.  Sadly, I haven't found that to be the case.

By modern standards, my computer would ***probably*** be considered slow (AMD 2600 with 1 Gb).

I don't play games on my pc, so I want to ditch windoze (I'm dual-booting with XP SP3).

The main things I do on my computer are:

[LIST]
[*]Internet (firefox)
[*]Audio editing (audacity)
[*]Audio converting (soundconverter and foobar when necessary ... I've been too lazy to install the ape tools and I often need to split .flac files with .cue files and foobar is just too easy to ditch)
[*]Video transcoding (mencoder) and authoring (none yet on linux, tmpgenc on xp).
[/LIST]
Things got a lot smoother when I went from 512 mb to 1024 mb.

Firefox just _**feels**_ faster on XP, (it certainly starts quicker) though I can't quantify how much faster it is.

Audacity is more responsive on XP (especially when I used gnome instead of xfce4).

Audio converting is a wash since I use foobar on both (it runs fine for me under wine, though the fonts are a bit funky).

I haven't gotten menuing to work within dvd authoring because my athlon 2600 chokes on some of the tools that have sse2 instructions (though this isn't ubuntu's fault).  Mencoder is much quicker than tmpgenc, but the .mpg files it creates show up as double the size when I try to author them in XP.  Dvdauthor creates appropriate video_ts and audio_ts for me, but without the authoring, it's not easy to use the DVD in my standalone player (Denon 5000).  Qdvdauthor crashes regularly for me.  Todisc chokes on mpeg2enc.  Haven't tried devede (sp?) yet.

Windows explorer is as fast as thunar in my opinion, but thunar lacks some features that nautilus and konqueror have, but they're too slow for my tastes.

I keep up to date with synaptic and apt.

I've never over-clocked my machine, and would hesitate to do so.  

_**Where can I find the bottlenecks in my system?**_  My thoughts are:

Video: Geforce 6200 (using nvidia 180.29 - not the proprietary ones)

Hard disc: 2xWD 160 ATA-100 drives (ext3 for boot, root, storage -- rw to NTFS partitions) 1 WD SATA 300 Gb (ntfs, storage)

Memory: Will be going to 2 Gb shortly.

Any other thoughts (short of buying a new computer)?

Well, thanks for reading my post, and I hope you have suggestions that will help me get rid of XP.

Walter

---

### Post by lovinglinux on 2009-05-23
> **walterp98@gmail.com said:**
> I've always read (and believed) that linux (ubuntu in specific) would perform better on older hardware than XP.  Sadly, I haven't found that to be the case.

I guess you shouldn't compare Windows XP with a recent release of Ubuntu. XP is old and works better than recent Windows releases too. You could have a good idea of performance differences if you compare Ubuntu 9.04 with Vista or Windows 7.

> **walterp98@gmail.com said:**
> Firefox just _**feels**_ faster on XP, (it certainly starts quicker) though I can't quantify how much faster it is.

It is [faster on Windows or even under Wine](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox), which is kind of disappointing. Nevertheless Firefox 3.5 is comming soon and should improve speed considerably.

> **walterp98@gmail.com said:**
> 

_**Where can I find the bottlenecks in my system?**_  My thoughts are:

Video: Geforce 6200 (using nvidia 180.29 - not the proprietary ones)

Hard disc: 2xWD 160 ATA-100 drives (ext3 for boot, root, storage -- rw to NTFS partitions) 1 WD SATA 300 Gb (ntfs, storage)

Memory: Will be going to 2 Gb shortly.

Any other thoughts (short of buying a new computer)?

I think you are using the proprietary drivers. Anyways, it would help if you mentioned which Ubuntu version you are using. I presume it's Jaunty 9.04.

I'm experiencing some performance issues since I installed Jaunty. I was previously using Hardy and it was considerably more responsive. I think one of the problems is the video driver. I also have nvidia.

One thing that helped was including this in /etc/X11/xorg.conf

```

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

This will enable direct rendering and compositing. I don't know exactly what they do, but I had a huge flash performance boost after this, Firefox is much more responsive and fast and the system is more responsive too.

If you have Jaunty, then Python 2.5 might be slowing you down. Since Jaunty comes with Python 2.6, I removed Python 2.5 and the unessential applications still dependent on it. There was a considerable performance improvement. [color=#FF0000]If you decide to do this, make sure Python 2.6 is installed and that removing Python 2.5 won't remove essential packages, otherwise you might brake your system.[/color]

I also had a considerable performance improvement after formatting all my partitions as ext4. But since [ext4 still has issues](http://ubuntuforums.org/showthread.php?t=1133719), you might want to leave the file system alone for now.

---

