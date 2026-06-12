---
title: "[SOLVED] No Panels Visible in gnome"
date: 2008-08-28
forum: Desktop Environments
---

### Post by stevemid on 2008-08-28
I've just installed Hardy and am having trouble logging in and finding my desktop. I do get presented with the login and password dialogue. If I log in normally I get presented the heron screen with no icons, panels or windows  This displays for about 10 seconds and then drops back to another login window asking me to log in again. 

If I select the options button in the lower left corner at log in time I am able to log in to console mode or gnome safe mode.  Gnome Safe Mode  presents the log in password dialogue and then the heron screen  I am able to do only two things. 1: I can press F1 and get the Ubuntu help centre.  This has links which I can click on and get Firefox started. This is how I can post this.  2: I can right click and get presented options to create folder create launcher or create document. But there are no Places, no System Administration, etc.  

I had this same problem running Ubuntu off the live CD.

This feels like a display size problem; maybe the panels are there, somewhere but I can't see them??  Any ideas?

---

### Post by EnGorDiaz on 2008-08-28
> **stevemid@iinet.net.au said:**
> I've just installed Hardy and am having trouble logging in and finding my desktop. I do get presented with the login and password dialogue. If I log in normally I get presented the heron screen with no icons, panels or windows  This displays for about 10 seconds and then drops back to another login window asking me to log in again. 

If I select the options button in the lower left corner at log in time I am able to log in to console mode or gnome safe mode.  Gnome Safe Mode  presents the log in password dialogue and then the heron screen  I am able to do only two things. 1: I can press F1 and get the Ubuntu help centre.  This has links which I can click on and get Firefox started. This is how I can post this.  2: I can right click and get presented options to create folder create launcher or create document. But there are no Places, no System Administration, etc.  

I had this same problem running Ubuntu off the live CD.

This feels like a display size problem; maybe the panels are there, somewhere but I can't see them??  Any ideas?

computer specs please?

---

### Post by stevemid on 2008-08-28
This is an HP/Compaq DC 5750, AMD 64 Athelon (3500) CPU 1GB memory

---

### Post by stevemid on 2008-08-29
Problem Solved!
I reinstalled ubuntu (wanted a /home partion) and still had to login to failsafe gnome to get my login accepted. HOWEVER this time the updater/installer or whatever said that the ATI Radeon video card needed a proprietary driver.  I downloaded this and when I rebooted everything worked fine. Next step will be to test opensource driver for Radeon.  See :[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

