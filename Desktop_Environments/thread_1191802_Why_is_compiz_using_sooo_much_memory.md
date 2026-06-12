---
title: "Why is compiz using sooo much memory?"
date: 2009-06-19
forum: Desktop Environments
---

### Post by gymophett on 2009-06-19
I have Ubuntu 9.04, and not running compiz, I use 150MB, using it I use 650MB!
What is wrong here?!
Is there a fix? Or do I just have to turn it off. :/
I only have the settings on Normal.

---

### Post by NightwishFan on 2009-06-19
Check the actual memory usage for me in Gnome System Monitor. If it is that high right away, there might be an issue, however I would think not. If you have a high amount of RAM, say 4gb, Ubuntu will tend to use more of it.

You can also check the CD you installed Ubuntu with to make sure there are no errors. Weird things happen with a bad media.

Insert the CD in the drive and run this command. If it does not say something along the lines of 'Checksum Mismatch', and just ends, then your media is fine.

```
cd /media/cdrom0 && md5sum -c md5sum.txt
```

---

### Post by H2SO_four on 2009-06-19
> **NightwishFan said:**
> Check the actual memory usage for me in Gnome System Monitor. If it is that high right away, there might be an issue, however I would think not. If you have a high amount of RAM, say 4gb, Ubuntu will tend to use more of it.

Strange but true.  Im at about 400MB and I only have Opera running at the moment.  It seems that when one has the memory, the system will require more.  Strange.

---

### Post by gymophett on 2009-06-19
> **H2SO_four said:**
> Strange but true.  Im at about 400MB and I only have Opera running at the moment.  It seems that when one has the memory, the system will require more.  Strange.

Quite annoying. I got a 3GB laptop and it uses like 150MB, and on my mom's one gig it uses about 75. :/

---

### Post by iponeverything on 2009-06-19
> **gymophett said:**
> I have Ubuntu 9.04, and not running compiz, I use 150MB, using it I use 650MB!
What is wrong here?!
Is there a fix? Or do I just have to turn it off. :/
I only have the settings on Normal.

This is a bit like asking why a hummer uses so much gas.

compiz is meant to add high end graphics and that comes at a price in terms of memory use.

---

### Post by LesterPalooza on 2009-06-19
I think the memory used by Compiz-Fusion is positively proportional to the amount of effects you are actively running on Compiz. Burn effect siginificantly increases my memory usage and memory usage reduces when I don't have Burn effect.

---

### Post by NightwishFan on 2009-06-20
Kubuntu is worse. Plasma, Kwin, Xorg, and the printer applet, which I cannot figure out how to disable (save killing it manually) all use over 60mb of RAM. Which means my RAM use is always about 600/900.. I do not think it is actually a problem, I just hope it is not a memory leak. Well Xorg once used like 200mb, which probably was a memory leak, because it normally settles around 80.

---

