---
title: "Fresh Kunbutu install... odd problem: !TWO! desktops"
date: 2008-09-20
forum: Desktop Environments
---

### Post by mithbuntu on 2008-09-20
All,

I finished installing the latest version of Kubuntu (with KDE 4.1) an hour or so ago.  After fixing grub to dual boot I finally got to load Kubuntu for the first time.

Once I loaded it I realized a couple bizarre things were going on and I need some help.  The main problem is that my desktop has, well, two desktop environments.  One is 1650*1080 and the other seems to be 1024&768.  The smaller one is laid on top of the larger one.  I think this might be because I have two video cards I run in SLI.  I haven't updated any drivers or run any commands yet.

Secondary problem is that I can not save screen resolution changes.   I can change them and disable the different screens I have available (DVI1, VGA0, VGA1 all disabled), but I have no way to save my changes.  THe second I go into the screen resolution option panel my resolution reverts to the default 1024*768 and I can't get back the 1680*1050 unless I reboot.

Any ideas?

---

### Post by TigerWolf on 2008-09-21
Would it be worth trying to install/update the drivers?

Are they NVIDIA cards?

---

### Post by mithbuntu on 2008-09-22
They're both Nvidia Geforce 8800s.

I'll try updating the drivers, but I thought this was very bizarre to see on load.

---

### Post by mithbuntu on 2008-10-03
Alright.  I installed the latest nvidia drivers and this fixed me not being able to change and keep my new resolutions, but I still have two desktops.

[Image of my Problem]("http://img89.imageshack.us/img89/3990/two1xe0.png")

As you can see from the image, it seems to think I have a <1> and <2> workspace sitting on top of each other at different dimensions.  I turned off all paging, but it didn't fix it. 

Anyone have any ideas how I can only have one of these desktops?  Two on top of each other is very annoying.

---

### Post by happyenduser on 2008-10-10
[SIZE="2"][FONT="Trebuchet MS"]o hai!
i am experiencing this very same issue with the overlapped desktops of different resolutions. no luck yet.
this is my setup & chain of events.
[FONT="System"][INDENT]**[ hardware:]**
[LIST]
[*]**NVidia GeForce 8600 GT** VBIOS Version:60.84.58.00.21 / PCI Express 16X
[*]**ASUS ACI VW222 LCD ** (DFP-0) -DVI & a **OMNITECH LCD PNP - VGA **(grunt side-kick monitor.)
[/LIST]
[/INDENT][/FONT]
latest drivers for Nvidia were installed, i used the instructions listed here: [URL="http://www.ubuntugeek.com/dual-monitors-with-nvidia.html"]  [FONT="Microsoft Sans Serif"]*[COLOR="Teal"] ubuntugeek.com/dual-monitors-with-nvidia.html[/COLOR]*[/FONT]
[/URL]

i was never able to get both monitors functioning as intended (both as a separate X screen; not as clones or twin view )
so i unplugged the power OMNI TECH LCD PNP and used the ASUS as the sole monitor.
this is when i noticed the overlapping desktops. 
to hardware troubleshoot i unplugged the OMNI TECH LCD PNP from the Nvidia Card (vga adapter on DVI port 1 (closest to the motherboard)
with just the ASUS DVI plugged in (DVI port 1) 
i rebooted in repair mode, and reset the X server.

And the issue occurred. d'oh!

i am still having fun adjusting and breaking all these new features, so i can just have it set-up perfect and let it be. 
just made the complete move to kubuntu from Microsoft this week, never going back. ever.

[/FONT][/SIZE]

---

