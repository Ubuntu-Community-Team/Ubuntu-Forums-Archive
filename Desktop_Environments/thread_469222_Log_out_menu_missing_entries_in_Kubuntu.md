---
title: "Log out menu missing entries in Kubuntu"
date: 2007-06-09
forum: Desktop Environments
---

### Post by quazi on 2007-06-09
I'm not really sure how this happened (I'm sure it was something I did because no one else has this problem), but the logout menu opened by the clicking on the KDE icon at the bottom left only has one option: log out.  

This isn't a huge deal as I can easily just use the console to shutdown or reboot, but it would be nice not to have any quirks with my OS.  There's never really one big thing that drives me away from linux, but a host of small issues that I never have with Windows.

---

### Post by SoggyCornflake on 2007-06-09
> **quazi said:**
> I'm not really sure how this happened (I'm sure it was something I did because no one else has this problem), but the logout menu opened by the clicking on the KDE icon at the bottom left only has one option: log out.  
.

I saw that too.  After a couple weeks and some system updates, I started seeing the other options again.

Have you done a system update recently?  If not, try it and see if that doesn't fix your problem.

---

### Post by Nythain on 2007-06-10
you didnt install kde-desktop within ubuntu did you??? sounds like you are using GDM still instead of KDM for your login... in terminal type 
sudo /etc/init.d/gdm stop
if gdm stops then use kdm to log into kde
sudo /etc/init.d/kdm start

---

