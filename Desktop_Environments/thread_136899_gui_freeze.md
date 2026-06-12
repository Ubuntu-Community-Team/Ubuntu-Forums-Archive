---
title: "gui freeze"
date: 2006-02-26
forum: Desktop Environments
---

### Post by muni on 2006-02-26
I recently installed ubuntu breezy, and really enjoy the desktop, except for one fact. my desktop freezes from time to time for a very short period (about a second), but it happens continuously when launching any application or when a window object is created or when I scroll or move to another page in firefox. I noticed that the Xorg process shoots up to more than 50% cpu util and this is when this issue happens. but it comes back to normal immediately sometimes in less than a second. This is happenning repeatedly and it's quiet annoying to work. I tried all sorts of tweaks but nothing worked. I have Fedora Core 4 installed on the same machine, where this problem doesn't happen. I copied the entire /usr/X11R6 directory from Fedora installation to the ubuntu one, and booted it up, but still i'm facing the same issue. I disabled update-notifier, installed new ati drivers, reconfigured xorg package, changed xorg nice value, and literally nothing worked. In fact the same issue happens with drapper too. I can't agree that this is a h/w limitation (I hv a PIII 750 MHz 256 MB ATI Rage Mobility M1 8M VRAM) because the same FC4 is running on the same h/w and i'm not facing this issue there. Can someone pls help me in resolving this issue and allow me to enjoy the ubuntu desktop experience?

---

### Post by art on 2006-02-26
Well, I had experienced Firefox loading too long and being very unresponsive when changing to another page, and it was because of the beagle extension for firefox. I don't know if that is the case with you, I just thought I'll throw this in in any case. Also you might wanna install a nice program called treeps, it will show you the tree of all processes and might possibly show which process makes Xorg to shoot up...

---

