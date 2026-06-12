---
title: "Boot Directly into CLI in 11.10?"
date: 2011-10-26
forum: Desktop Environments
---

### Post by geudrik on 2011-10-26
What I've been trying to do, and have been unsuccessful at after upgrading to 11.10 is booting directly into Single User Mode - EG: no GUI.  

What was working previously was the normal grub.conf file edit.. once I upgraded from 11.04 to 11.10 that no longer works. So I then tried to edit the GDM conf file to stop at run level 3... which had no affect.  

Can someone shed some light on this mystery for me?

---

### Post by gsmanners on 2011-10-26
I think everything is in lightdm.conf at this point, though I'm not sure about that if you upgrade. Then again, if you don't want a graphical interface to come up, why not just remove lightdm (and gdm or kdm as well)?

---

### Post by geudrik on 2011-10-27
> **gsmanners said:**
> I think everything is in lightdm.conf at this point, though I'm not sure about that if you upgrade. Then again, if you don't want a graphical interface to come up, why not just remove lightdm (and gdm or kdm as well)?

Using a GUI from time to time makes certain tasks much easier - like dealing with samba shares... But I have no desire to boot directly into a GUI.

Where is that file located?  Find and Locate don't return anything...

Edit:  Having dug through /etc/init... there's really nothing to be changed... :s

---

