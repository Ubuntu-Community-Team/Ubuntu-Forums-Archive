---
title: "how to copy a device input driver to a different directory"
date: 2009-05-04
forum: General Help
---

### Post by dragon99 on 2009-05-04
I d/l and installed game software. The game runs ok but has difficulty setting up a usb controller. I can see in the terminal window that the game s/w is looking for js0 in /dev, but the js0 file is sitting in /dev/input.

In trying to move or copy the js0 file to /dev, I am not permitted. I figured as root owns the file, I could log in as root and copy the file. This does seem to work only for the current session, as the changes are lost the next time I boot the pc. Any ideas how to make the js0 file permanently reside within /dev rather than /dev/input? TIA

dragon

---

