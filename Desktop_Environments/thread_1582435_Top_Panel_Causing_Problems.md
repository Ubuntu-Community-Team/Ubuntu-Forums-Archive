---
title: "Top Panel Causing Problems"
date: 2010-09-26
forum: Desktop Environments
---

### Post by aisajib on 2010-09-26
Hi!

I just reinstalled Ubuntu Lucid Lynx and an old problem has come back. For some reason I couldn't fix it even in my previous installation. The problem is the top gnome panel. See the photo below:

[IMG]http://img715.imageshack.us/img715/8250/screenshotmn.png[/IMG]

As you can see, the network icon is not shown properly while the Me menu is being shown twice. I can't even restart or log out or shut down at this situation without pressing the keystroke to turn the power off.

How do I fix this?

---

### Post by 0N3 on 2010-09-26
killall gnome-panel

---

### Post by 0N3 on 2010-09-26
in a terminal type killall gnome-panel is the me-indicator added twice??

---

### Post by bshosey on 2010-09-26
I have had this problem sens 9.04 I am using 10.10 and this still happens. Not always but about 50/50 percent of the time. I would like to know what is causing this so it can be fixed. I know the killall gnome-panel is the work around but any one know the fix?

---

### Post by aisajib on 2010-09-27
I want to know about it too. It's a pain.

---

### Post by heavy metal on 2010-09-27
I tought it was only me having this issue:)

---

### Post by bshosey on 2010-09-28
No you are not. There has been several post about this sense 9.04. All I have gathered was the work around the killall gnome-panel command.

---

### Post by aisajib on 2010-10-01
Maybe we have to be happy with that only. :(

---

### Post by wojox on 2010-10-01
> **aisajib said:**
> Maybe we have to be happy with that only. :(

Does resetting do anything?

```
rm -rf .gconf/apps/panel 
```

Log out and back in.

---

### Post by xzinkx on 2010-10-01
This started happening to me after a recent update within this week. 50% chance of it happening if I turn the laptop on. I just restart the computer again and hope it's normal. I've had updates break so many things in Ubuntu now i'm just considering disabling updates because it's not really worth the hassle of constant terminalling just to fix things that shouldn't have been broken in the first place. :/ . Running 10.04 btw.

---

### Post by aisajib on 2010-10-03
So, you don't download or install system updates? That leaves your computer vulnerable to security threats, I guess.

---

### Post by bshosey on 2010-10-15
Bump

---

### Post by bshosey on 2010-10-24
bump

---

### Post by bshosey on 2010-10-30
bump

---

### Post by bshosey on 2010-11-08
Bump

---

### Post by Jerommel on 2010-11-18
I'll give it a BUMP then.

This kind of problems should be solved !

---

### Post by bshosey on 2010-11-29
I have on 2 systems with proposed updates, 1 system with just the regular updates. And 1 fresh install with no updates. All 4 systems have this problem. I also have 2 desktops that do not have this problem. The two systems with proposed updates have Intel video and Intel wireless. The 1 system that just have the regular updates has an ATI video and Broadcom wireless. The only thing in common with these three that they share are they are Dells and they are laptops. 2 are Latitudes D630s and 1 Inspiron 1720. This happens even when wireless is off. What I think it is causing this is the Network Manager but only with systems that have a wireless card.

So I am bumping again with more info. I really would like this resolved. At first I was thinking not a big deal. But I am to the point I am very annoyed with this. This problem has been from 9.10 and up.

---

### Post by nuwave on 2011-01-14
I've been having this issue also since 9.10 and now it seems to have gotten worse because my panels completely change themes! I keep the regular default theme but at start up it changes to something else like "dust-theme" or something random and it wont change back until I restart or log-off and log-in. I've tried all the above commands and still the problem persists. I am certain an update broke something but I am not sure what's casing the problem and I'm not fully trained to be able to investigate such a thing. So basically I am just at the mercy of a future fix for this issue...

---

### Post by nuwave on 2011-01-14
posting error, my fault sorry...

---

### Post by nuwave on 2011-01-14
posting error, my fault sorry...

---

### Post by nuwave on 2011-01-14
posting error, my fault sorry...

---

