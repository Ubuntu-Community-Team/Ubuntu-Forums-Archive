---
title: "Which is better for linux... ATI or NVidia or Integrated..."
date: 2005-11-22
forum: Gaming &amp; Leisure
---

### Post by Optimal Aurora on 2005-11-22
I know in windows ATI and NVidia are just about equal, but in linux my ATI 9550 128MB AGP graphics card only spits out 10 to a max of 15 Frames per second... How can I improve this to more like 30 or higher? If that can't be improved then would it be wise to get a NVidia graphics card or go back to using the integrated UniChrome graphics system...

---

### Post by Pablo_Escobar on 2005-11-22
Heh, AFAIK NVidia has the better Linux drivers, in which the ATI always lacked.
But i do have the same card and I get really decent 3D performance - no 10-15 FPS.
Maybe Your fglrx setup is somewhat corrupted.
What fglrxinfo spits out ??

---

### Post by [Rui] on 2005-11-22
Neither is good. Both company's recent cards (and all for NVIDIA) only have decent "support" with proprietary crappy drivers. I hope you're not an AMD64 user... forget the drivers in that case. Or a PPC user... or ...

---

### Post by Optimal Aurora on 2005-11-22
[QUOTE='[Rui]']Neither is good. Both company's recent cards (and all for NVIDIA) only have decent "support" with proprietary crappy drivers. I hope you're not an AMD64 user... forget the drivers in that case. Or a PPC user... or ...[/QUOTE]
ATI and I do think NVidia has since the last time I visited about 3 or 4 months ago added 64 bit. ATI has it now in bin and rpm formats...

how do you show the fglrxinfo?

---

### Post by Optimal Aurora on 2005-11-22
I think I figured it out. 

By default it only installed xserver-xorg-driver-ati, it did not install any of the fglrx stuff (not even the control center)...

I'm going to install it and I'll be right back... Later...

---

### Post by gnutux on 2005-11-29
I have a NVIDIA card because I like NVIDIA, yet ATI is cheaper here in Canada because it's a Canadian company, but o well.

gnutux

---

### Post by WoodyDragon on 2005-12-06
go for nvidia. 
ati needs 5 years or so to come up with USEFUL drivers

---

### Post by teaker1s on 2005-12-06
personally nvidia has given me less problems and more satifaction than ati

---

### Post by metoo on 2005-12-12
You need linux-restricted-modules-yourkernel package.
This holds the modules for both nvidia and ati. I would 2nd that nvidia is better, as they have better openGL drivers, which is what you use with Linux.
And hey, Rui, my castrate Nvidia 6800gt AGP (cheap SDRAM, 128MB) is flying with ut2k4 on amd64 here ! :-)
Did it already with debian sid xx69/7174 over half a year ago and no problems now with ubuntu xx76 drivers, all amd64 native. (It's me who sucks, I'm just too slow :-) :-) )

---

### Post by iand675@gmail.com on 2006-01-01
ATi graphics for linux aren't supported well enough to decently run a lot of programs unfortunately. Granted, they can run, just not very well.

---

### Post by Omnios on 2006-01-01
I picked up a nvidia geforce mx4000 for about $80 in Canada a while ago, the 5000 should be faily affordable right now two.

 also glxgears is not realy a good benchmark other than comparing the frames with other posts on the glx thread.

[http://ubuntuforums.org/showthread.php?t=39349&highlight=glxgears]("http://ubuntuforums.org/showthread.php?t=39349&highlight=glxgears")

 YOu can compare it to others and if things don't jive you might have a config problem.

---

### Post by newuser111 on 2006-01-01
i recommend installing the ati drives as shown here [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) if you used a different method before
 
 but always use fglrxconfig to generate your xorg.conf file, rather than a different command, since it creates the best xorg.conf

---

### Post by exclipy on 2006-01-02
[QUOTE=newuser111]but always use fglrxconfig to generate your xorg.conf file, rather than a different command, since it creates the best xorg.conf[/QUOTE]

I don't see what's wrong with just editing xorg.conf to change the driver from "ati" to "fglrx".  Saves having to reconfigure the resolution, horizontal/vertcal sync, mouse, keyboard, joystick, touchpad and everything just to switch video drivers!

---

### Post by newuser111 on 2006-01-02
[QUOTE=exclipy]I don't see what's wrong with just editing xorg.conf to change the driver from "ati" to "fglrx".  Saves having to reconfigure the resolution, horizontal/vertcal sync, mouse, keyboard, joystick, touchpad and everything just to switch video drivers![/QUOTE]

i noticed that xv extensions didnt work in video playback, that was because the text enabling it wasnt in xorg.conf

but using fglrxconfig adds all this information specific to your ati card when it generates a new xorg.conf

---

### Post by gRiMgRaVy014 on 2006-01-07
What about integrated graphics cards?

---

### Post by iand675@gmail.com on 2006-01-07
integrated cards are hit and miss really. Definitely get an integrated nvidia if that's the route you must go. Just don't expect it to be a top performer.

---

### Post by leech on 2006-01-08
nVidia all the way.  The ATI drivers, as someone else pointed out, probably need a few more years before they're up to par with their Windows drivers.

I have two nvidia cards amongst my computers, one is a AGP 6800GT and the other is a PCI-E 6600 Go that is in my laptop.  Both run everything extremely fast and smooth.

The other video cards I have experience with in linux, are the Matrox G400 (very good open source card, if a bit on the old side....) and the crappy Sis 650 (I think that's what it is) that is an integrated solution.  No 3D for it.  I've also owned a Matrox Parhelia, and that had worse drivers than ATI....

If you play 3D games I would only suggest a nVidia card.  You won't regret it.

Leech

---

