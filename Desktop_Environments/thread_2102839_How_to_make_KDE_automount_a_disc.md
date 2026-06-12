---
title: "How to make KDE automount a disc?"
date: 2013-01-08
forum: Desktop Environments
---

### Post by Another Monkey on 2013-01-08
Over the w/end I decided to try KDE.  Quite nice.

One problem I have is that CDs do not get automatically mount to "/mnt/cdrom" (or some other sensible location).  When I insert the disc, I get the device notification but there is no "Mount" option.  I don't even want to click on that, I want it to automount.

Dolphin seems to be using some rather odd path ("audiocd:/?device=/dev/sr0") under "Devices" for a CD.  When I try to play the CD, I can see KDE copy from "audiocd:/?device=/dev/sr0" to a temp location before attempting to play anything (I then get a notification for each track that the copy worked, which is annoying).

How do I tell KDE to just mount the disc and be done with it?  I've gone into "K/System Settings/Removable Media" and enabled "automount" (location: "/dev/cdrom") and with only the last option ticked as that seemed to be the sensible one.  That had no effect.  I even ticked "automount" for the specific CD; no effect.

I check in "Device Notifier" as well, the settings are the same.

I know how to do it from the CLI, but it would be nice if the DE just automounted the disc and save me opening a terminal every time.

There are no exception message or other problems I can see, the drive is fine as CDs etc automount perfectly well in other DEs (eg. Cinnamon and Unity).

I am using kubuntu-desktop (KDE 4.9) installed on Ubuntu 12.10.

---

### Post by Another Monkey on 2013-01-08
<deleted>

---

