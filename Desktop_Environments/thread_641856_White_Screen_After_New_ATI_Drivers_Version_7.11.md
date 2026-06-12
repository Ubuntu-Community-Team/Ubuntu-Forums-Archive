---
title: "White Screen After New ATI Drivers Version 7.11"
date: 2007-12-15
forum: Desktop Environments
---

### Post by Jay_Davis on 2007-12-15
I installed the newest ATI drivers (version 7.11) on a computer running Ubuntu 7.10 but when I rebooted I got my wallpaper and panels for just a moment, and then white screen. Failsafe Gnome works fine, but I can't login with the normal Gnome session. Any solution to this, other than just uninstalling the driver?

---

### Post by thecapuchin on 2007-12-16
You're not the only one.  I recently tried to upgrade an older desktop from Feisty to Gutsy and was rewarded with the same.  I can login, see the Ubuntu splash and the desktop for a second but then I get the blank white screen.

I can connect to the machine remotely and get a desktop no problem, but locally it's all hosed up.  I'm not liking AMD/ATI too much right now.  

Oddly, I have the same driver installed on my laptop and am using LinuxMint Daryna (Gutsy) and it works like a charm.  No clue wtf is going on.

---

### Post by bisbebri on 2007-12-23
I think its something with compiz... I have an Inspiron1501 and when i put the messed with Compiz and i rebooted..... i got white screen.... and when i have visual effects off It works perfect

---

### Post by 3xtreme on 2008-01-16
I am new to Ubuntu as well and this weekend has quite and experience!!!

What I found with the latest ATI driver 8.443.1 if you do not have XGL installed you will get the white screen after loggin in.

If you install XGL from the restricted mode it will boot up fine, however I am experience real poor performance with Desktop Effects enabled..

I serisouly may go get a nvidia card!!!

---

### Post by ugm6hr on 2008-01-16
I got the latest drivers via Envy, then followed this: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

I also found I had to uninstall xserver-xgl.

---

