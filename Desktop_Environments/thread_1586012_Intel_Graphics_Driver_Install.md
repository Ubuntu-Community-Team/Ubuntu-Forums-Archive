---
title: "Intel Graphics Driver Install"
date: 2010-10-01
forum: Desktop Environments
---

### Post by unconvention on 2010-10-01
Hi All

I have installed xubuntu 10.04 on a HP Pavilion dv1049ea and am having trouble installing the drivers for the graphics card. When installing i had to use the boot option -xforcevesa in order to get the screen working. Now that it is installed there is constant screen flicker but apart from that all other aspects of the system are working fine. In the display menu i am unable to change the refresh rate. How do i change the running driver from vesa to the correct intel driver?

The graphics card is an Intel Graphics 82852/82855.

Thanks for any help you can give me.

Rob

---

### Post by TBABill on 2010-10-01
Do you possibly have an Intel Core i3/5/7 chip AND using the on-chip GPU? From your post it sounds like you have the original 10.04 release and not the 10.04.1 if you have that chip combination above. Mine would do that too on Ubuntu and Mint. 
 
If that's your problem can you run it via the vesa and do an update? Once you update the system to current and reboot you should have a new kernel update that fixes the video issue.
 
Disregard if I'm way off base on my assumptions :)

---

### Post by unconvention on 2010-10-01
Unfortunately its actually an old Pentium M not an i series processor. I have installed all the updates and the still the problem remains.

It is running in vesa at the moment and i was hoping to change it to the relavent drivers instead. 

Many thanks

Rob

---

