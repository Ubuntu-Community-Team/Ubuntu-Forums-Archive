---
title: "Need to adjust DPI, xorg.conf is being completely ignored"
date: 2009-01-05
forum: Desktop Environments
---

### Post by IkariKeiji on 2009-01-05
Hi,

After running Kubuntu 8.10 on a virtual machine and finding it a lot better than GNOME, I decided to install it on my linux box. This computer previously ran Ubuntu 8.04. Before, the DPI was messed up so I couldn't read anything in the textboxes on the login screen, but it fixed itself as soon as I logged in, so I ignored this problem. But on Kubuntu, it doesn't fix itself, and the main menu won't show up because it's apparently miles off the top of the screen. I know the DPI is the problem because I found out it was set ridiculously high a while ago, so I've been trying to fix it by following instructions I googled for. But apparently it's completely ignoring my xorg.conf file. I've tried both```
Option "DisplaySize" "338 270 # 96 DPI @ 1280x1024"
```and```
Option "USEdidDPI" "false"
Option "DPI" "96 x 96"
```in the Monitor section of /etc/X11/xorg.conf, but neither have done anything. I can't look around in whatever graphical settings programs Kubuntu might have because the problem makes the GUI literally unusable. How do I force the DPI to 96?

---

### Post by benny bronx on 2009-01-05
I have never used kubuntu, but have a kde distro on another partition.  In it's etc/x11 folder, look for a file named Xresources.  At the bottom of it should be a dpi setting that you can change to 96. Again, I don't even know if this exists in kubuntu but its worth a look, at least until someone who actually knows wanders by.

---

### Post by Nathan.Flow on 2010-08-28
The setting your looking for is in;
```
System->SystemSettings->Apperance->Fonts->"Force fonts DPI" 
``` It's a combo box in the middle, on the left hand side.:D

---

