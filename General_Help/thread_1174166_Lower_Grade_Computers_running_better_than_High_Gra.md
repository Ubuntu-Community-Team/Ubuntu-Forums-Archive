---
title: "Lower Grade Computers running better than High Grade Computers in Ubuntu?"
date: 2009-05-30
forum: General Help
---

### Post by Prominence on 2009-05-30
My laptop is a HP Pavilion dv6000, Intel Pentium Dual Core 1.86 GHz with 3 gigs of RAM. 

My previous laptop, which has been handed down to my cousin, is an Acer Aspire 5315 with a Intel Celeron Processor 1.76 GHz with 2 gigs of RAM. 

Both have Intel Integrated Graphics. This Acer far out preforms the HP, in boot times, to overall system performance, even with Compiz. 

The Acer is about 6 months older than the HP. 

Then there is a desktop computer that also runs Ubuntu, it is years old, and has an ancient Nvidia graphics card, it runs Ubuntu, and it handles Compiz greatly. It only has MBs of RAM, not much at all. 

The question is really, why is the HP not functioning as well as the others? 

(All of the computers run Ubuntu 9.04, EXT3)

---

### Post by KhurramM on 2009-05-30
I think that like windows, there should be device drivers available for linux too.

For any machine u get windows drivers, but never for linux.

This is a down issue with linux today.

Regarding the new hardware, their linux built-in kernel drivers are yet to be tested by many and much feedback is still awaited I suppose, like yours.

Hope u find some solution for speed issues.

---

### Post by Prominence on 2009-05-30
Well, aright.

---

### Post by lykwydchykyn on 2009-05-30
> **KhurramM said:**
> I think that like windows, there should be device drivers available for linux too.

:confused:

They're in the kernel, dude.  They saved you the trouble of installing them yourself.

@OP: What are the chipsets in each laptop?  Jaunty has some trouble with Intel graphics, but from my experiences it only happens with certain chipsets.  

You may benefit from some of the intel tweaks out there.  Google "intel jaunty" and one of the first few links will be a post on these forums with tweaks for intel chipsets.

---

### Post by Prominence on 2009-05-30
Yeah that's what I was thinking. 

How do I tell the chipsets?

---

### Post by asmoore82 on 2009-05-30
> **Prominence said:**
> My laptop is a HP Pavilion dv6000, Intel Pentium Dual Core 1.86 GHz with 3 gigs of RAM. 

My previous laptop, which has been handed down to my cousin, is an Acer Aspire 5315 with a Intel Celeron Processor 1.76 GHz with 2 gigs of RAM.

Both have Intel Integrated Graphics. This Acer far out preforms the HP, in boot times, to overall system performance, even with Compiz.

Boot time and "overall performance" can be greatly impacted by the
*speed* of the hard drive, regardless of its *size*. Most laptops have only 5400 rpm drives which, despite what some may say,
is actually noticeably slower. Maybe this Acer is one of those gems with a 7200 rpm drive.

There are also different *speeds* of RAM, maybe the Acer's is faster. Even when RAM *speeds* are equal, more expensive RAM can have lower *latency*(delay), which yields better performance. Use the "Memory Test" boot option to get an idea of the cache sizes and speeds and the RAM speeds.
> **Prominence said:**
> The Acer is about 6 months older than the HP. 

Then there is a desktop computer that also runs Ubuntu, it is years old, and has an ancient Nvidia graphics card, it runs Ubuntu, and it handles Compiz greatly. It only has MBs of RAM, not much at all. 

The question is really, why is the HP not functioning as well as the others? 

(All of the computers run Ubuntu 9.04, EXT3)
In Linux, an nVidia card coupled with the official non-free drivers should always provide much better performance - this is to be expected because nVidia cards will have their own on-board high-speed vRAM, whereas integrated graphics chipsets must "borrow" vRAM from the main system RAM.

---

### Post by lykwydchykyn on 2009-05-30
Try this command:
```

lspci |grep -i vga

```
should list info about the intel video.

---

### Post by Prominence on 2009-05-30
grayson@iGrayson:~$ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by lykwydchykyn on 2009-05-30
> **Prominence said:**
> grayson@iGrayson:~$ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

I take it that's the new one?  The 965 chipset seems to come up a lot in support forums.  My desktop at work has a 965, and it seems like it was pretty sluggish in Jaunty; eventually I was given an Nvidia card to use instead.

It could be your hard drive speed as well as asmoore82 suggested.  I'm not sure of a command to show HDD speed, it's probably in your laptop's documentation somewhere.

---

### Post by Prominence on 2009-05-30
Any fixes or anything for the chipset? That's true though.

---

### Post by lykwydchykyn on 2009-05-30
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

