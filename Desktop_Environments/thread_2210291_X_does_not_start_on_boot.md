---
title: "X does not start on boot"
date: 2014-03-10
forum: Desktop Environments
---

### Post by schekn on 2014-03-10
After system upgrade to 13.10 there is no GUI at startup. I can login successfully and startx or start lightdm, but it should be done automatically.
I tried following these instructions ([http://askubuntu.com/questions/302788/gui-does-not-start-on-boot](http://askubuntu.com/questions/302788/gui-does-not-start-on-boot)) and did:
 - cat /etc/X11/default-display-manager (return: /usr/sbin/lightdm)
 - sudo dpkg-reconfigure lightdm
 - gedit /etc/init/lightdm.conf and before command exec lightdm added sleep 5
Nothing seems to help the situation. Any help is greatly appreciated!

---

### Post by grahammechanical on 2014-03-10
Have you tried using a different video driver? In 13.10 we go to System Settings>Software and Updates>Additional Drivers tab.

You could also try getting to a desktop using Recovery mode>Resume. In 13.10 we find Recovery mode in the Grub Advanced Options for Ubuntu sub-menu. 

Regards.

---

### Post by schekn on 2014-03-11
Thank you for the suggestions.
The Additional Drivers tab just gives me "No additional drivers available". Is that normal?
Recovery mode is an interesting solution, haven't tried it yet. Should it fix my issue permanently?

---

### Post by Bucky Ball on 2014-03-11
You installed 13.10 what? Ubuntu?

---

### Post by Mark Phelps on 2014-03-12
> After system upgrade to 13.10 there is no GUI at startup. 

What Ubuntu version did you upgrade FROM?

Also, what is the make and model video card in use? If you don't know, do the following: open a terminal, enter "lspci" (without the quotes), look through the output for the line containing "VGA" -- post that information back here.  Could possibly be, if you are using one of the older AMD "legacy" video cards/chipsets, that their older drivers are incompatible with Ubuntu 13.10.

---

