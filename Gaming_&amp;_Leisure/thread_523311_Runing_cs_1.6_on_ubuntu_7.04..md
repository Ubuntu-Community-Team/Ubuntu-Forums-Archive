---
title: "Runing cs 1.6 on ubuntu 7.04."
date: 2007-08-11
forum: Gaming &amp; Leisure
---

### Post by dimitars on 2007-08-11
I want to run cs 1.6 in ubuntu. I have winodws on same PC and i have instaled cs on windows. i want just to start it, not instal it. I'll be very happy if i can.

i have wine on linux

---

### Post by nille on 2007-08-12
I don't know if it's possible, but you can always try this:

Mount your Windows-partition (if it's an NTFS-partition, you will probably have to install **ntfs-3g** too) and locate your Steam-installation.

I'll assume that your windows-partition is mounted on /media/windows and that Steam is installed in the directory C:\Program Files\Steam, but just change it so that it fits your mountpoint and installation.

Then go to your Steam-directory via the terminal:
**cd /media/windows/Program\ Files/Steam**

And run Steam using wine:
**wine Steam.exe**

If that works you can probably just make a shortcut (i.e. on your Desktop) that runs the following command:
**wine "/media/windows/Program Files/Steam/Steam.exe"**

Or just locate your Steam.exe via Nautilus, right-click and make sure that the file is to be run by wine.

Good luck!

---

