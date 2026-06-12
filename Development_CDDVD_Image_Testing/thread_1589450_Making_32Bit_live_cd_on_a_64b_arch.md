---
title: "Making 32Bit live cd on a 64b arch"
date: 2010-10-06
forum: Development CD/DVD Image Testing
---

### Post by hammerjack on 2010-10-06
I have 64b architecture hardware w/ lucid (10.2.x) 32 bit desktop.  How can I make a live cd w/ a copy of my current system in 32 bit from a 64 bit arch?

The new hardware is all 64bit and the old hardware is 32 bit, so I need to be able to make a 32 bit live cd copy of the system.  The 32 bit will run fine on the 64 bit hardware, but not the other way around.

---

### Post by sikander3786 on 2010-10-06
You can make a live cd using remastersys.

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

I actually couldn't understand the "arch" part of your post. Please explain what you really want to achieve?

---

### Post by Crazedpsyc on 2010-10-06
I believe he means Arch Linux. 
Another good one is Brasero which comes default in ubuntu. The .iso decides the architecture, not the Operating system you burn it from.
Hope this helps!

---

### Post by sikander3786 on 2010-10-06
After reading Crazedpsyc's post above, I think I couldn't understand you correctly.

If you just want to burn an Ubuntu iso image to disc, you can use any disc burning software, as Brasero mentioned above or K3B or Gnome-Baker etc. 64-bit install won't stop you from burning a 32-bit disc from it.

If you want to create a custom image of your installed Ubuntu with all the packages and configuration, you can use remastersys or clonezilla etc.

---

### Post by hammerjack on 2010-10-06
Sorry for the confusion on the terminology here, and I think that I need to add a little more explanation.

arch is architecture -- I am using an amd Atholon 64 bit processor which is reported as i686 ( uname -a).

I loaded the 32 bit desktop, because I need wine and it is the recommended desktop.  When I followed the procedures found in these forums including remastersys ([www.geekconnection.org/remastersys/](www.geekconnection.org/remastersys/)) it completed making an iso, with some errors.  When I tried to run the iso, it either bombed immediately or hung.  Seemed to be a bad disk.  After a few attempts, I borrowed a 32 bit computer and made a live cd on the first try using remastersys.  Worked perfectly, but the 32 bit computer is not always available to me.  New computers are all 64 bit so I need to be able to support both 32 and 64 bit

---

