---
title: "Disable automount for specific device?"
date: 2011-10-29
forum: Desktop Environments
---

### Post by cmdln on 2011-10-29
I have a udev rule that fires a script when the memory card from my camera is inserted. The script takes care of mounting the card, and importing the photos just fine but then the file manager pops up for the memory card. I like that behaviour for some devices, but I would like to disable it for specific devices.

Can anyone point me in the right direction?

Running 11.10

---

### Post by cmdln on 2011-10-29
Got it, use blkid to get the uuid of the partition that I want to exclude and stick an entry in /etc/fstab with noauto.

it would be nice to still see the device when connected in nautilus, but not have it automount. Oh well for the excluded devices I should rarely even be accessing it manually.

---

### Post by gsmanners on 2011-10-29
If your script takes care of mounting it, I'm not sure I see how Nautilus would have trouble accessing it. I mean, you just want Nautilus to not mount it for you.

---

