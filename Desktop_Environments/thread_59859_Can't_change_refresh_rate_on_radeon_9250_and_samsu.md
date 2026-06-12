---
title: "Can't change refresh rate on radeon 9250 and samsung 900ift"
date: 2005-08-25
forum: Desktop Environments
---

### Post by ianikeev on 2005-08-25
Hi!

I have recently installed ubuntu and have installed ATi drivers by apt.  However, I'd like to change the default refresh rate (which is 60 now) to something like 85Hz (Windows allows this).  Is there an easy way to do this?

Bye,
Igor

---

### Post by KingBahamut on 2005-08-25
Check your xorg.conf file in 
/etc/X11 

Look and see which drive you are running. If your Running the stock ATI driver, aptly named ati, then your pretty much stuck, Unless you install ATI proprietary driver. They have released a new .run file that compiles an Ubuntu package for you to install, and thats a good thing.

If you have problems doing that, check back here. I have, and some others here have, compiled the propreitary driver and can give you some aid.

---

