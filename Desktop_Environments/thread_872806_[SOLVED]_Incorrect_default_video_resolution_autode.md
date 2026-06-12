---
title: "[SOLVED] Incorrect default video resolution autodetect"
date: 2008-07-28
forum: Desktop Environments
---

### Post by secdroid on 2008-07-28
I'm a Dapper user looking to migrate to Hardy 8.04.1.  I'm confused by the Hardy screen resolution autodetect & how to work around it.

Symptom: Desktop is larger than physical screen.  Can't see top or bottom bars.  Can't figure out how to scroll or drag desktop to see top or bottom (in order to run screen tool).  Editing xorg.conf and restarting X does not help.  Tried sudo dpkg-reconfigure -phigh xserver-xorg and it didn't help.

Question: How do I cope in a livecd/liveusb environment?  How do I work around the new hardware autodetect permanently for an install?

Background: I've always had difficulty with Ubuntu autodetect because I use a Belken PS/2 KVM switch.  Works fine with most Linux scrren autodetect, but has always confused Ubuntu.  I run Dapper with hand-edited xorg.conf.

Monitor works fine with xorg.conf HorizSync 28-51, VertRefresh 43-60, Display (SubSection) Depth 1 and Modes "1024x768" "800x600" "640x480"

Monitor is Amphion CM1722PF, bought at a Circuit City loss leader sale.  Circuit City gave specs on (now defunct) web page as: "Recommended resolution 1280 x 1024," "Horizontal scanning frequency 30-72KHz," "Vertical scanning frequency 50-135Hz."  Running sudo ddcprobe | grep monitorrange gives 30-70 and 50-135.

I've googled and browsed, so I hope that this isn't too obvious...

---

### Post by secdroid on 2008-07-28
Well, I figured out how to get control when the desktop is far too large for the physical screen.

Procedure --
[LIST]
[*]Press ALT-F2 [gets a "Run Application" box]
[*]sudo displayconfig-gtk [gets a config application]
[/LIST]

For some reason, selecting the Generic 1024x768 monitor resulted in a demand for a driver file.  Not logical!  However, selecting the Plug and Play monitor and setting a proper resolution allowed me to get the desktop set for the proper resolution.

I had hoped the new Xorg in Hardy would be an improvement.  Reading about xorg and RandR in phoronix.com made me optimistic, but I think that Ubuntu's video monitor detection continues to be inferior to that found in many other distros.  I continue to think that this is a weakness given that KVM switches are becoming more common in home computing setups.  A newbie would not have been able to get this to work.

---

