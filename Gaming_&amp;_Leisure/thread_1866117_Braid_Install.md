---
title: "Braid Install"
date: 2011-10-21
forum: Gaming &amp; Leisure
---

### Post by kbarz on 2011-10-21
From the 11.10 software center, I paid my $ and installed Braid.  When run, I get a complete black screen for about 7-8 seconds, then it closes and my screen resolution is altered.  I've tried making the changes to the exec statement posted in the install center reviews.  I get a window that doesn't mess with my resolution, but it's still just black for the same time before it closes.  Is there something else this program depends upon for it to work?  This is a new installation of Ubuntu on this machine.
Thanks,
Ken

---

### Post by Perfect Storm on 2011-10-21
Try start it through the terminal and post the output.
Also your computer specs would be a good idea to post.

Though Braid is platform games it require some horsepower to run.

Braid System Requirement
Intel CPU -	Pentium 4 2.0GHz	
AMD CPU -	Athlon XP 2000+
Nvidia GFX Card -	GeForce 6800 Series 128MB	
ATI GFX Card -	Radeon HD 2400 Series
RAM (Memory) -	 1 GB	
Hard disk space -	 256 MB

---

### Post by kbarz on 2011-10-21
System wise I have:
Intel Core 2 Quad Q6700 2.66Ghz Socket 775 
Crucial 2048MB PC5400 DDR2 667Mhz
Intel DG35EC Socket 775 Motherboard
Power Up Silver 5511 ATX Mid-T Case w/450w PSU

and if I'm looking at the right box, the video card is a Galaxy GeForce GT 430 1024MB/MO DDR3

When I have access to that box, I'll post what the terminal echos back.

---

### Post by kbarz on 2011-10-21
If I call Braid with the -windowed parameter I get no feedback, just a black window.  Calling it without the parameter gives me the following:


ken@Pyramid:~$ /opt/braid/braid -windowed -width 1440 -height 900
ken@Pyramid:~$ /opt/braid/braid
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3a0000e
  Serial number of failed request:  173
  Current serial number in output stream:  175
ken@Pyramid:~$

---

### Post by Perfect Storm on 2011-10-21
Check this: [http://ubuntuforums.org/archive/index.php/t-1818163.html](http://ubuntuforums.org/archive/index.php/t-1818163.html)

---

### Post by kbarz on 2011-10-22
Tried everything mentioned in the link, + logged in as full root, tried running it there and made myself owner so I could play with permissions in the gui under my user logon.  Still nothing but black screen or black window if I pass in -windowed -width .  This is a pretty new install of 11.10 so I'm not too worried if I break anything just yet.  It is a little disappointing that the game featured for purchase in the banner ad of Ubuntu Software Center won't work out of the proverbial box (and won't tell you why.)

---

### Post by kbarz on 2011-10-22
Alright, more dinking around and I finally found the problem.  Seems that while every other app works just fine with the 11.10 install, for the game I found the proprietary drivers for the graphics card under system settings.  Everyone's playing nicely again.  Thanks.

---

