---
title: "Amarok and GNOME?"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Imek on 2005-09-01
Hi,

I've been using Amarok successfully in other window managers and distributions for quite a while, but this is the first time I've tried it in GNOME and Ubuntu. The problem is, I can never seem to get Amarok's system tray icon to appear in gnome-panel's notification area. Is there something I need to do to get Amarok to be compatible with GNOME in this way? 

At first, I thought I just needed to use kdetrayproxy. I've tried installing it, but it gives me some baffling depedency error about needing to remove kdelibs4 and refusing to install because kdelibs4 wasn't going to be installed (or something like that). I've tried compiling it from source and force installing the deb file by hand, but it neither actually give me a binary I can run.

Any ideas at all would be appreciated.

---

### Post by xerosis on 2005-09-01
sorry to be completely useless, but i've apt-get-ed amarok a few times on systems and it always works.

---

### Post by Imek on 2005-09-01
Actually, that gave me an idea. I've tried installing amarok on my laptop (which is a much cleaner install of Ubuntu), and the icon comes up just fine. I've decided that this must be a problem with the notification area itself, because update-notifier is running but I don't have an icon for it. I must have messed something up myself..

---

### Post by junior aspirin on 2005-09-01
may be a silly question, but this could be overlooked. have you removed the notifcation area applet?

---

### Post by Imek on 2005-09-01
No, I did something even stupider: at some point I must have changed the ownership of my user directory to root, which was apparently what was causing the problem. It's all fixed now.. *feels stupid*

---

### Post by Imek on 2005-09-01
Okay, never mind.. Now for some reason the amarok icon works, but is one pixel in width. The only time it will work is if I remove the notification area, run amarok and create the notification area again, but if I run amarok with the notification area on the panel I get the single pixel icon.

---

### Post by Imek on 2005-09-02
EDIT: Sorry about the triple post.

I've found out what was causing that last problem, and I thought I'd put it here in case anyone else had a similar problem and found this thread. Apparently, the problem lies somewhere between xfwm4, gnome-panel and amaroK, because when I got rid of xfwm4 and replaced it with standard Metacity the tray icon started working properly again. This is a pity; I much prefer to use xfwm4 over metacity for a lot of reasons, but I suppose I'll have to wait to see if it's fixed in an update. Now I'm not sure whether my bug report should go to the amaroK, gnome or xfce devs..

---

