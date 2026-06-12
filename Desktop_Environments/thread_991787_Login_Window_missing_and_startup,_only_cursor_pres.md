---
title: "Login Window missing and startup, only cursor present"
date: 2008-11-24
forum: Desktop Environments
---

### Post by parry_mathur on 2008-11-24
Hi. I'm using Ubuntu 8.10 using Wubi. I recently installed the Mac4Lin package on my system, to make it look like OSX, and changed my GDM login window to the one supplied by the mac4lin package. I was using Compiz and Emerald. When I rebooted, this is what I saw:

An X shaped cursor, then the *waiting* cursor.... and no login screen. Just a blank screen with the *Waiting* cursor spinning. 

I tried doing ctrl+alt+F1 and sudo /etc/init.d/gdm stop and then startx. When I do startx, I am able to see my fancy mac cursor arrow, but there's nothing else. Just a black background. Interestingly, when I swipe my finger across the laptop's touchpad's scroll area, a small icon pops up, indicating that it's switching to another GNOME *multiple desktop*, also known as *spaces* in mac, but noting else happens.

I have tried doing the dpkg reconfigure xorg.conf thing. I have tried doing sudo apt-get install ubuntu-desktop or gdm-desktop, but the problem is, I'm behind a proxy and don't know how to get an update through the command line.

I have tried fixing the X server thorugh the recovery mode, but nothing happens. 

Can somebody please help me out, as I have a lot of applications installed for **important** work, and reinstalling ubuntu now would mean certain madness for me.

I'd be very grateful.

Thanks

---

