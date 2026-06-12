---
title: "X server fails to start after Nvidia driver update"
date: 2013-09-11
forum: Desktop Environments
---

### Post by Ender Shadow on 2013-09-11
After updating to the latest kernel (3.2.0-53) last night, I noticed that the Gnome Display Manager wasn't working. I then tried updating my Nvidia driver to version 319, thinking that would fix the problem, but after rebooting, I saw this message: 

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly.
 Would you like to view the X server output to diagnose the problem?"

My first thought was, "Oh well, that kernel is screwed. I'll just load the previous one." Which I did. But, the same problem occured with that one, too. I'm assuming that all of the kernels that I have are affected by this (which is odd).
I have narrowed down this problem to the new Nvidia driver, but the issue with MDM must have something to do with the new kernel. I think.
I would greatly appreciate somebody's help, as my main computer is now GUI-less. 
I am using Linux Mint 13 64-bit, so most solutions that work for Ubuntu should work for Mint.

EDIT: Seeing as I need my computer for other things (eg. school) I may just reinstall Mint, although I might still run into the same problem...
EDIT: Additional information: It appears the X server is unable to find any screens, and I ran into this error message:

"Nvidia: API mismatch: the Nvidia kernel module has version 304.88, but this Nvidia driver component has version 319.32. Please make sure that the kernel module and all Nvidia driver components have the same version."

Seems the driver never updated properly. How I'm supposed to fix this is still a mystery to me...but I'm not giving up yet.

---

### Post by grahammechanical on 2013-09-11
There is something that you can try. Select Recovery Mode>Resume. That will get you to a desktop without using a proprietary video driver. You will be on Nouveau. Does Mint have a Recovery Mode?

Regards.

---

### Post by Ender Shadow on 2013-09-11
> **grahammechanical said:**
> There is something that you can try. Select Recovery Mode>Resume. That will get you to a desktop without using a proprietary video driver. You will be on Nouveau. Does Mint have a Recovery Mode?

Regards.

Yes, Mint has a recovery mode, and I already tried booting from it, but the X server still crashed.
There is some good news, though. I purged the Nvidia driver that I updated to, and everything seems to be back to normal. MDM is working, too. I guess I'll just stick with this driver version.
And while I will consider this problem solved, I do wonder why it happened...
One more thing, how do I enable/switch to the Nouveau driver? I would like to compare it to the proprietary Nvidia driver.

---

### Post by Mephisto Pheles on 2013-09-12
I ran into this on Mint 12.04 also, i finally managed to wiggle myself out of it via recovery > root shell > aptitude. I selected something nvidia in there and it installed and configured some stuff... et voila. 
That was surely a Lucky shot. I didn't have the slightest clue what I was doing to be honest.
Or even what exactly had happened.
I assume those nvidia drivers weren't installed properly when we upgraded the kernel.
 I tried kernel 3.10.2, obviously my nvidia drivers were not compatible yet.
I'll stick with 3.8.4 for now. Lesson learned.

---

### Post by buzzingrobot on 2013-09-12
Mint 13 has, I think, Ubuntu's "Additional Drivers", or the same functionality wrapped in new clothes.  That should offer Nouveu. Look in the setting tool.

A number of Nvidia cards were  problematic with kernels in the 3.2 series.

---

### Post by Mephisto Pheles on 2013-09-13
nouveau doesn't work for me on my box. I can't even install ubuntu regular because of that, install disk bombs out with a kernel panic.
My xubuntu wubi had the same issue, so I installed nvidia drivers, problem solved.
And I migrated the wubi xubuntu to a seperate partition by now.

---

