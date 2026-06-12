---
title: "Trouble booting to xwin"
date: 2009-03-13
forum: General Help
---

### Post by LittleCory on 2009-03-13
I am having an issue with my machine booting to a terminal rather than starting the gui.  When it boots it appears that it is looking for an image, meaning that it thinks that it was suspended to disk.  Then it tells me that no image was found, and it is resuming normal boot, then goes to a login and then to the command line.  I can then start xwin manually just fine.  The only issue in xwin is that the shutdown/restart commands are gone.

At the prompt a sudo poweroff works, and upon reboot seems to solve the problem.  The machine will boot normally.  I have poked around the bios settings for power management, but nothing seems to make any difference.  Is it something simple that I am overlooking?

---

### Post by Peter09 on 2009-03-13
might be worth re-installing ubuntu-desktop. Note that the image thing is just the fact that there is no resume image because you did not hibernate the machine - its normal.

---

### Post by LittleCory on 2009-03-13
Ah, so it always checks for a disk image when it boots.  The odd thing is that this is a fresh install on a brand new machine, and it booted normally for the first few times, and then this.  I will reinstall the desktop package.

---

