---
title: "Increasing fonts"
date: 2005-09-01
forum: Desktop Environments
---

### Post by GrootBrak on 2005-09-01
I am using Gnome most often, but Kubuntu "feels" nicer. Problem is that my fonts is very small. This is true for all programs listed under the Kubuntu icon (left bottom, eq. to Windoos "start") I tried a lot of things, but i can't increase it. The help files have nothing, but in the help files, the left hand side fonts is very small, while the right hand side, containing the help, can be adjusted at will.

Regards

---

### Post by chandra on 2005-09-01
Go to 

[http://kudos.berlios.de/kf/kf1.html#fixes](http://kudos.berlios.de/kf/kf1.html#fixes)

search for

font size

and follow the instructions.

---

### Post by Rory on 2005-09-04
I'll second that.  The  simpler way on this site did the trick for me:

Easy way:
   1. Download setxdpi (right-click, then "Save Link As...")
   2. In terminal, from the folder that 'setxdpi' is in:
chmod +x setxdpi
sudo cp setxdpi /usr/bin/X11
sudo setxdpi

   3. Follow the lead.  Type: 100 to begin with.  If it's too big, begin to scale down until you get the size you want.  But, 100 is require less resources.  FYI, Windows uses 96 DPI.

By the way, this is one of the best tweaks for Linux I know, as the standard 75 DPI is ridiculously small.  KDE could really stand to increase the default, plus make it easy to change it, as Gnome has.  But, for now, this is the best method.

---

