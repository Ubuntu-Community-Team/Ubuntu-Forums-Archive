---
title: "Login Loop [KDE]"
date: 2010-07-12
forum: Desktop Environments
---

### Post by Sarteck on 2010-07-12
I have recently installed Kubuntu 10.04 Lucid Lynx on my boss' computer alongside a fresh Windows XP install.  The install went smoothly, but when I started it up, it kept looping on the login splash screen thingie.

I figured that maybe it's something that happened during install, and since it was a fresh install, I just ran the installer again in text mode.  It went to the login screen, but after I entered the password, it did the same thing--started to load, then blacked out and went back to the login screen.

After some searching, I found this can happen for several reasons:
-- The home directory permissions are ****ed up
-- There is a problem with the video driver
-- The language pack might have to be re-installed
-- There is not enough free space on the drive

There's plenty of space on my drive, and the file permissions must be fine (it's a fresh install), so I figured it must be the language pack or the video driver.  I removed language-pack-kde-en and language-pack-kde-en-base by the failsafe console, purged them, and then re-installed them.  The problem persisted.

I have NOT tried anything with the video driver, because I really don't know where to start.



I did try to use the Console Login (Alt + N at login screen), but it kept turning on and off my monitor and NOTHING else (no login prompt or anything).  I was able to get to a console login by using Failsafe Mode and going to root, then typing "exit."  I WAS able to log in via the console then, but when I tried to sudo startx, it went all buggy again.


At a loss, I installed **ubuntu-desktop** and **gdm**, and I AM able to log in just fine to a GNOME session now.  However, I really think my boss will be more comfortable with KDE, so I'd like to fix the problem if at all possible.





To sum it up, I can log into a GNOME session, but not a KDE session; I have tried re-installing the language pack, the home directory permissions are fine, and I have more than enough free space.  I don't think it's a video driver problem, since I can log into GNOME just fine.  I CAN reach a console through Failsafe Mode.  





If anyone could point me in the right direction, I'd appreciate it.

---

### Post by lexxonnet on 2010-07-13
Hi There,

Since you have both GDM and KDE installed, have you tried logging into a KDE session using GDM instead of KDM?

---

### Post by Sarteck on 2010-07-13
> **lexxonnet said:**
> Hi There,

Since you have both GDM and KDE installed, have you tried logging into a KDE session using GDM instead of KDM?

No, I'm not quite sure how to go about that...  KDM still comes up by default; I have used it to log into a GNOME session, that's it.

I'll try to look into how to switch that on my own (short of removing KDM, that is), but if you would like to give me a nudge in the right direction before I do it (and post the results), that would be cool. :3

---

### Post by lexxonnet on 2010-07-13
> **Sarteck said:**
> No, I'm not quite sure how to go about that...  KDM still comes up by default; I have used it to log into a GNOME session, that's it.

I'll try to look into how to switch that on my own (short of removing KDM, that is), but if you would like to give me a nudge in the right direction before I do it (and post the results), that would be cool. :3

Ah, right... try getting into a console and type in 
```

sudo dpkg-reconfigure gdm

```

That *should* theoretically ask you to set a default desktop manager, at which point you should be able to select gdm :)

---

