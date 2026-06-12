---
title: "Desktop Problems - Can't click on anything"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by Stuart_99 on 2007-08-03
Hi everyone,

I am running Ubuntu 7.04 on my Dell XPS M1210.  It is running with the NVIDIA Graphics Acceleration Driver, and ndiswrapper to run the wireless device.  It was working well, until one boot, I was unable to click on any of my icons, menus, or anything.  If I attempted a right click, I zoomed in on my desktop background.  This is a big problem...because my Ubuntu install is mostly useless at the moment. I can't click/select anything with my touchpad or mouse.  I am typing up this post from the Windows partition of this laptop.  

Can anyone help me with this?  I didn't make any changes before this started, but out of the blue this became a problem.  Any suggestions would be greatly appreciated.  Thanks for your time.

Stuart

EDIT:  I have run into the same problem running the Failsafe session of GNOME...

---

### Post by sciurus on 2007-08-04
Try switching to another virtual console (ctrl-alt-f1), use the adduser command to create a new user, then switch back to X (ctrl-alt-f7) and see if the new user has the same problem in GNOME.

---

### Post by Stuart_99 on 2007-08-04
Thanks for the information!  I was able to log in as a secondary user, however the user did not have sudo abilities.  This proved as a major problem for me.  I decided that the only way to restore my system was to do a reinstall.  I had to download GParted to get my disk set right, and was able to successfully reinstall. 

Thanks for the information - I'll keep it in mind for next time I  run into a user account problem. :)

Stuart

---

