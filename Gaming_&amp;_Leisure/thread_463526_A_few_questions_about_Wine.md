---
title: "A few questions about Wine"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by Bohlio on 2007-06-03
Hello all :-)

I just got wine and am kinda a noob at how it works. I ran Nester with it by using the command... ```
wine nester.exe
```
and it works great. The only problems i have are when I try to go fullscreen, it just shows up in the middle of the screen with black all around it. It doesnt really go fullscreen. And the audio doesn't work, I get a bunch of funky messages in the terminal.

Aside from my problems. I have a question about programs that are already on my windows partition. I have full access to the drive and am wondering if I can run applications straight from there, without having to use the "virtual C:\ drive" that wine sets up. I just want to avoid having to double install applications on both partitions.

Thanks in advance :-)

---

### Post by blackened on 2007-06-03
Run winecfg and, under the "Drives" tab, change the location from your virtual C: drive (that resides in your user directory) to the mountpoint for your real C: drive a la /media/hdb1 or where ever it is. You might be able to fix some of your audio and video problems with the options in winecfg also.

---

### Post by hikaricore on 2007-06-03
I'm going to add my advice to this:

**_DO NOT_** change from the virtual drive C unless you have a very good reason to do so and know exactly what you're doing.
If wine can't access certain files including configuration files (when needed) in your fake windows directory I'd imagine this could cause problems.

Always check the wine application database to make sure your game actually runs and you aren't just wasting time:  [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by YokoZar on 2007-06-03
> **blackened said:**
> Run winecfg and, under the "Drives" tab, change the location from your virtual C: drive (that resides in your user directory) to the mountpoint for your real C: drive a la /media/hdb1 or where ever it is. You might be able to fix some of your audio and video problems with the options in winecfg also.Don't do this, ever.  It won't work, and you'll very likely break your windows install as Wine tries to make it work.

> **Bohlio said:**
> Aside from my problems. I have a question about programs that are already on my windows partition. I have full access to the drive and am wondering if I can run applications straight from there, without having to use the "virtual C:\ drive" that wine sets up. I just want to avoid having to double install applications on both partitions.From the Wine FAQ: [http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541](http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541)

> **Can I run applications directly off of a Windows installation without reinstalling them?**

Generally, no. Unless you know otherwise, you should leave your Windows installation alone and install things "fresh" into Wine. Most applications store their configuration data outside of their own folders, such as in the Windows registry.

This isn't unique to Wine: you'll run into a similar problem under Windows itself if you try and run applications from another Windows installation. Wine (or the other Windows installation) has no way of seeing this data unless it was written into Wine's registry by the program installer.

Some applications, however, are designed to be "portable" and don't use the registry at all, instead storing all of their settings in a file alongside the executable.

---

### Post by blackened on 2007-06-03
> **YokoZar said:**
> Don't do this, ever.  It won't work, and you'll very likely break your windows install as Wine tries to make it work.

From the Wine FAQ: [http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541](http://wiki.winehq.org/FAQ#head-3647fcb12328bf8f43d7cfce4d0dcbcee12c0541)

Good to know, maybe this is what borked my Windows install some months ago. I had always attributed it to something entirely different.

---

### Post by Bohlio on 2007-06-03
thank you very much Yokozar, thats all i needed to know :-)

---

