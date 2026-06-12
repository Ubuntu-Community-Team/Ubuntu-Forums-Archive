---
title: "New artwork =&gt; artifacts on radeon mobility u1"
date: 2006-06-01
forum: Desktop Environments
---

### Post by ]TheNose[ on 2006-06-01
I've been experiencing artifacts on buttons ever since the introduction of the new artwork on my hp pavilion ze4500 laptop (radeon mobility u1-chipset). They disappear with a mouseover.

This person seems to have the same problem. 
[http://www.ubuntuforums.org/showthread.php?t=146960]("http://www.ubuntuforums.org/showthread.php?t=146960")

Might there be something wrong with the Xorg-radeon driver because he's using that one too, I presume?

---

### Post by xpmaniac4ever on 2006-06-01
/me has got artefacts on buttons too :(

---

### Post by xpmaniac4ever on 2006-06-01
I got a ATi Radeon 7000 btw.

---

### Post by Casey on 2006-06-01
Does it only happen with the default theme?

I've heard of this only happening with Human during the beta time-frame.

Edit:
Also it wouldn't hurt to file a bug...
[https://launchpad.net/distros/ubuntu/+filebug/]("https://launchpad.net/distros/ubuntu/+filebug/")

---

### Post by ]TheNose[ on 2006-06-01
Yes, it only happens with the default Human-theme. I'll see if I can file a bugreport.

[EDIT]
Bugreport:
[https://launchpad.net/distros/ubuntu/+bug/47879]("https://launchpad.net/distros/ubuntu/+bug/47879")

---

### Post by Hezekiah on 2006-06-01
There are existing bugs for this, and sadly they have been around for a long while - the problem stems from some combinations of ati + the xorg driver + cairo.  So the artifacts show up on any Cairo-based gtk theme (clearlooks-cairo, rezlooks, ubuntulooks).  Switching to a non-cairo-based theme engine (original Clearlooks as included in Dapper by default, any smooth-engine based themes) should get rid of the problem.  But it also gets rid of the exceptionally nice looking new Human theme...

Hopefully some fix will be released, as this is a pretty horrendous oversight.

---

### Post by moitio on 2006-06-01
[QUOTE=xpmaniac4ever]I got a ATi Radeon 7000 btw.[/QUOTE]
Have you got all the drivers running for it? Have you followed these instructions:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

---

### Post by ]TheNose[ on 2006-06-01
[QUOTE=moitio]Have you got all the drivers running for it? Have you followed these instructions:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)[/QUOTE]

The ATI binary-driver is not compatible with the Radeon 7X00-series ;)

---

### Post by bswilson on 2006-06-01
I also have this problem on Dapper, with my Radeon RV100 QY [Radeon 7000/VE] card...  Just adding to the information already here.

---

### Post by art on 2006-06-01
I have a Mobility Radeon 7000 IGP, and I also get artifacts on buttons, which dissapear when I change the icon set to let's say nuove.

---

### Post by Jingo on 2006-06-02
This is the bug:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/38198)

Mark Shuttleworth subscribes it, so he knows about the bug.
Please contribute to the comments in there!

---

### Post by kingkookie on 2007-05-08
In my case, I have also have an HP Pavilion ze4500 laptop.  But, I have chosen KDE over gnome and have not had any display issues.  Plus I feel that KDE is a much more of a complete Windows Manager that is well polished in comparison to gnome.  KDE 4 (which is slated to be out later this year) looks to be the best thing that ever hit the open source world.  For now, though I've found KDE 3.x to be more than capable of meeting my needs.

---

