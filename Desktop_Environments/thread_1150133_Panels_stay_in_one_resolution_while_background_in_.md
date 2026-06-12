---
title: "Panels stay in one resolution while background in another."
date: 2009-05-05
forum: Desktop Environments
---

### Post by Mechphisto on 2009-05-05
A few days ago, on my 8.10 install, I connected up my TV through s-video as a mirrored screen. Had to set to 640x480.

Now, with the s-video unplugged, I have it back on 1280x768, and whenever I reboot it comes back to that resolution...except the top and bottom panels/status bar (whatever they're called) are shifted up-left and about 640x480 until I go into screen resolution and simply hit "apply" on the resolution of 1280x768 that it's already still set to...then the bars refresh at the appropriate sizes.

What can I do to fix this to stop happening?
Thanks for any suggestions,
Liam

---

### Post by gamblor01 on 2009-05-06
It's likely caused by a nagging entry in /etc/X11/xorg.conf (i.e. it was placed there when you attached the s-video cable, and should have been deleted when you disconnected it but was not).  Are you running an nvidia card with the proprietary nvidia driver?  If so, try running "nvidia-settings" from the terminal (or go to System -> Administration -> NVIDIA X Server Settings) and look at the "X Server Display Configuration".  You may need to re-detect your displays and/or delete the second display.

If you still can't get that resolved, post your /etc/X11/xorg.conf file here (please, inside of code tags to make it more readable).

---

