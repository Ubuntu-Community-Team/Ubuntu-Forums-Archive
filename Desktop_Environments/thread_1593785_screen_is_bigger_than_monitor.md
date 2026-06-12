---
title: "screen is bigger than monitor"
date: 2010-10-11
forum: Desktop Environments
---

### Post by navy2008 on 2010-10-11
Hi.  I am new to ubuntu.  I just install the desktop 10.04 version.
I have a viewsonic 27" monitor.  What I get is the screen size is 
bigger than the actual monitor.  I can't find a way to fix this.  In
other words, when max-size a window, I can't see the edges.  It goes
beyond the monitor size.  My monitor don't have any way to fix the
vertical or horizontal size.

How can I fix this?

---

### Post by bobcollard on 2010-10-12
In /System/Settings/Display change Resolution.

---

### Post by navy2008 on 2010-10-12
> **bobcollard said:**
> In /System/Settings/Display change Resolution.

Sorry, but I can't find this directory.

---

### Post by bobcollard on 2010-10-12
Miscommunication, you didn't say what desktop you are using, I'm using XFCE.  Tell me about your system and hardware.  Desktop or laptop? Gnome or KDE? Sounds like a nice monitor.  I run a 21 1/2 " external with a Laptop and had the same sort of problem.  I can probably plug in a Live disk and get the right settings if I know what I'm dealing with.  Next time tell what you have tried and as much info about your system as possible.  If it's gnome: system/preferences/display.  BTW it's not a directory it is the location in your Panel.

---

### Post by navy2008 on 2010-10-12
> **bobcollard said:**
> Miscommunication, you didn't say what desktop you are using, I'm using XFCE.  Tell me about your system and hardware.  Desktop or laptop? Gnome or KDE? Sounds like a nice monitor.  I run a 21 1/2 " external with a Laptop and had the same sort of problem.  I can probably plug in a Live disk and get the right settings if I know what I'm dealing with.  Next time tell what you have tried and as much info about your system as possible.  If it's gnome: system/preferences/display.  BTW it's not a directory it is the location in your Panel.

It is the default windows manager that comes with ubuntu.  I think it is GNOME.  I did a default install of it and didn't change or modified anything.  I have a desktop.

---

### Post by bobcollard on 2010-10-12
> **navy2008 said:**
> It is the default windows manager that comes with ubuntu.  I think it is GNOME.  I did a default install of it and didn't change or modified anything.  I have a desktop.
Try this link:
[http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)

---

### Post by navy2008 on 2010-10-13
> **bobcollard said:**
> Try this link:
[http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-screen-resolution-in-ubuntu.html)

Yes, I did that.  But it is still doing the same thing.
Is there a config file where I can go an make the changes manually?
Or how do I change to a different display manager other than gnome?

---

### Post by bobcollard on 2010-10-13
> **navy2008 said:**
> Yes, I did that.  But it is still doing the same thing.
Is there a config file where I can go an make the changes manually?
Or how do I change to a different display manager other than gnome?
Try:
```
sudo dpkg-reconfigure gdm
```

---

### Post by navy2008 on 2010-10-13
> **bobcollard said:**
> Try:
```
sudo dpkg-reconfigure gdm
```

The same thing after the update.  

Here is a screen capture of what I am talking about.  I am not seeing the frame or the edges.  I can only see center.  So it goes beyond the physical screen or the monitor.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172247&stc=1&d=1287027418[/IMG]

---

### Post by bobcollard on 2010-10-14
Right click on your desktop and use Desktop Settings  Either try Auto or Zoom to see which fills your screen.

---

### Post by tsg1zzn on 2010-10-14
Do you have nvidia or ati and what driver do you use? I had variations of this problem with both closed and open source nvidia driver. It seems basically random, and you just have to fool around a bit to set it right.

Some things to try:
1. Disconnect and reconnect your monitor.

2. Set the resolution to something low (like 800x600), then press Ctrl+Alt+F1 to go to a virtual console, press Ctrl+Alt+F7 to go back to your normal screen, then set the resolution to the correct value.

3. Log out and log back in.

4. Close all programs except the monitors dialog, check "same image in all monitors", set and accept a wrong (smaller) resolution, click "make default", then set the correct resolution, click make default again. Finally close this dialog, and open the logout dialog. Place the mouse over the entry "log out". Then disconnect your monitor, and while the monitor is disconnected, click on "log out". Wait a few seconds and plug your monitor in again.

---

