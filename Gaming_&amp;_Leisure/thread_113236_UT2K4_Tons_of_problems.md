---
title: "UT2K4: Tons of problems"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by jtk on 2006-01-06
I am trying to set up UT2K4 on BB but I'm having some technical troubles.

I set up my box initially with a GeForce MX400, and I had everything running well. I switched to a GeForce 6800GT, reconfigured my xorg.conf correctly without too many problems, and I thought I was ready to go. Fired up UT2K4 and joined my clan's server, only to discover that I was getting 8 FPS with all standard settings except running at 1280x1024 (my LCD's native). I know this can't be right because my old 6600 used to get 40-50 FPS on this same map and resolution, but in Windows.

So i figure I need the latest nVidia driver. I went through various steps to get the right libraries installed so I can compile whatever it is that needs to be compiled for the newest driver. I almost got it to work, but the last error was that my kernel was compiled with GCC 3.4 and the current compiler is 4.0. I thought the command to switch that was export=GCC-3.4, but that didn't work, so I was then going to come back here to find the thread I was using as a reference. Only now Gnome won't start. I was using 

sudo /etc/init.d/gdm stop

and

sudo /etc/init.d/gdm start

but all I get is that Gnome failed to start. This also occurs after a reboot.

So, 2 questions:

1. What do I need to do to get proper framerates in UT2K4?
2. What do I need to do to fix Gnome?

Thanks!

---

### Post by Zeroedout on 2006-01-06
did you install gcc-3.4? if not, ```
sudo apt-get install gcc-3.4
``` Why gnome isn't starting, that's odd, try looking in xorg.conf, you may have mispelled something you changed, that's the only explaination i have since that's the only thing you touched. If you can't figure it out, post it and maybe someone will spot something; if you don't have the patience for that (like me) just generate a new xorg.conf ```
sudo dpkg-reconfigure xserver-xorg
``` and change the approprate setting to use your newly compiled nvidia driver. The other thing you could do is install a kernel that was compiled with gcc-4.0

---

### Post by Harleen on 2006-01-06
X propably refuses to start, because you tried to replace the display driver and failed with that. You can use the 2D-only nv driver as fallback, until you get your nvidia driver working.

---

### Post by handy on 2006-01-06
**Automatix** does a great job of installing the nVidia (c) drivers.  Painless.

**[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)**

All the best...  :p 

handy

---

### Post by jtk on 2006-01-06
Thanks guys!

A couple things:

I did install gcc-3.4. I may have installed 4.0 on accident before that using

sudo apt-get install gcc

I didn't actually edit my xorg.conf, I generated a new one using that xserver-xorg command, and Gnome actually worked fine for a while with the new one.

I used Easy Breezy to install the nVidia driver because I'm on 64 bit (maybe that is the problem?) but it only has up to 7176 (I think) and nVidia has 8184 on their website. But again, I don't really know how much of a difference that will make in my framerate issue.

I'll have some more time to play with this tonight. I'll post if I can find anything new.

---

### Post by handy on 2006-01-06
**Automatix** installed most of what I asked, including the nVidia (c) drivers, on my 64 bit rig, running Breezy 64 bit, & again tonight, running Breezy 32 bit on the same 64 bit hardware.

The difference in drivers is probably inconsequential.

Here's to a quick resolution. :smile: 

handy

---

### Post by jtk on 2006-01-06
Interesting... I was under the impression that Automatix didn't really work with 64-bit.

Anyway, I've got a clear idea of what needs to happen for this to start working again. I'll post later with my progress.

---

### Post by jtk on 2006-01-06
OK, some problems solved, more discovered....

1. Gnome is working again. I went through the xserver command and rebuilt xorg.conf, and at some point it started working.

2. Latest Nvidia driver is installed. Having done that, I never will again... too much trouble.

Edit: Got AGP enabled (who ever heard of a hidden BIOS menu) :P

---

### Post by jtk on 2006-01-07
Well, I finally just reinstalled Ubuntu. Everything seems to be working fine now!

---

### Post by handy on 2006-01-08
[QUOTE=jtk]Interesting... I was under the impression that Automatix didn't really work with 64-bit.

Anyway, I've got a clear idea of what needs to happen for this to start working again. I'll post later with my progress.[/QUOTE]

I've run Automatix under both 64 & 32bit, a few more things install under 32bit, but not all on my machine under either.

No problems with Automatix, can't recommend it highly enough to 64 or 32bit Breezy users...:KS 

handy

---

