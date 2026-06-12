---
title: "Ubuntu Live CD No Display"
date: 2006-08-18
forum: Desktop Environments
---

### Post by leetcharmer on 2006-08-18
I have an [HP m7330n Media Center PC]("http://www.amazon.com/gp/product/B000E1D9BW/002-6465805-5923204?v=glance&n=541966") that I've been trying to install Dapper on.  The problem I am receiving is that after the LiveCD boots (6.06.1), I get the wrong graphical output.  The screen looks completely garbled.

The machine came with an onboard ATI card which is disabled for the PCI-E nVidia GeForce 6800 GS card.  Any ideas on how to fix the screen output so I can install dapper on this machine? Thanks!

---

### Post by taurus on 2006-08-18
If you want to install Dapper and don't care about testing it out first with the LiveCD, then perhaps you should use the alternate CD.  It is a base installer and should install everything that you need.  Hopefully, it configures your graphic card for you and if not, you can configure by hand with one command (after installing it on your machine).

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by canadianwriterman on 2006-08-18
I had a similar problem on my machine. This is what I did. When you get to the install/live CD screen after inserting the disk, look at the bottom. There's a key for VGA (F4?). Hit it and choose a low resolution -- maybe very low, test it a few times. That got rid of the garble. After you do an install on the hard drive, the resolution should be normal.

---

### Post by leetcharmer on 2006-08-22
I was able to boot the CD up in VGA mode (1024x768x32), but after the LiveCD loads -- the mouse does not show the pointer.  The mouse works, I can still click and drag to see the box on the desktop, I can open applications as if the mouse works.  There is just no pointer.  Ideas?

---

### Post by leetcharmer on 2006-08-23
After booting the LiveCD with visual accessability mode: 1024x768x32; the mouse appears to be invisible.  I am still able to click, and see things .. but the mouse cannot be seen normally.  How can I fix this?  I have already tried going to System->Preferences->Mouse; but, this has not fixed the issue.  The mouse appears when rolling over links after choosing another mouse picture, but it does not appear during a 'normal' position.

---

