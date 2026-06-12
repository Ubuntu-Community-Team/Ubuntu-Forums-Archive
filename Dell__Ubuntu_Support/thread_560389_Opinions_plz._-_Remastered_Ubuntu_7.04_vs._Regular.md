---
title: "Opinions plz. - Remastered Ubuntu 7.04 vs. Regular on 1420n"
date: 2007-09-26
forum: Dell  Ubuntu Support
---

### Post by Exile29 on 2007-09-26
I just got my new 1420n and I'm really enjoying it.
There are a few minor issues that are bothering me, mostly related to either X, Gnome, or maybe even the touchpad. Hard to tell. 

Anyhow, I was wondering if someone could contrast and compare the two.

---

### Post by notwen on 2007-09-26
I'm still using the original install on my 1420n, majority of the fixes applied.  I'm very satisfied, I have yet to install the new Dell Feisty image, was aiming to try and hold out for Gutsy, looks like the majority of the Dellbuntu issues were fixed there. Just curious as to what problems you may be having w/ X and/or GNOME?

---

### Post by Exile29 on 2007-09-26
Just odd things like when I logon, it tries to link up to my wireless network. The Keyring password box comes up and then immediately minimizes. It won't come back up if I left-click on it; I have to right click and select restore.
Odd issues like that. 
The really annoying ones seem to lock up my screen. An example would be when I was prompted to install Adobe Flash when I went to check my email. I clicked the install bar in my browser, it started to download and install. I click through the license stuff, then it pops up a box; I didn't get a chance to see it or click on it before it hid beneath my browser. Since it was the active window, I couldn't minimize the browser, move any windows to get at it, etc... I had to power down my laptop and load Adobe Flash from Synaptic.

---

### Post by notwen on 2007-09-26
The keyring issue is a GNOME issue and should be fixed in GNOME 2.20(which is to be included in Gutsy).  As for the lockups, that could be caused by many different things.  I'm glad your issues aren't necessarily related to Dell's hardware.  I am anxious to see the thoughts of anyone who may have re-installed using the new Dell Feisty image though.=]

---

### Post by deserthowler on 2007-09-26
> **Exile29 said:**
> Just odd things like when I logon, it tries to link up to my wireless network. 

I didn't like this feature of connecting up automatically either, especially since it automatically connected to a neighbor's network instead of mine.  

After getting tired of working from the command line, I downloaded wicd from their website and installed it.  It's a group of python scripts.  It works great.  It lists all of the available WiFi networks and gives a choice in an EXTREMELY simple interface.

Earl

---

### Post by Exile29 on 2007-09-26
> **notwen said:**
> The keyring issue is a GNOME issue and should be fixed in GNOME 2.20(which is to be included in Gutsy).  As for the lockups, that could be caused by many different things.  I'm glad your issues aren't necessarily related to Dell's hardware.  I am anxious to see the thoughts of anyone who may have re-installed using the new Dell Feisty image though.=]

I'm going to drop XP on a small ntfs partition this weekend; I think instead of reloading Grub, I'll just reinstall with the remastered version and see what happens.

---

### Post by deserthowler on 2007-09-28
> **Exile29 said:**
> Just odd things like when I logon, it tries to link up to my wireless network. 

I installed wicd to solve a similar problem.  Mine was hooking to a neighbor's unsecured network.  

After installing wicd, it doesn't hook up until I tell it too.  Google them and check it out.  It's a group of Python scripts.  It hasn't done any damage that I can tell.  It removed the old WiFi manager.  It is easier than working from the command line or writing Bash scripts.

:guitar:

Earl

OOPS, sorry I posted again on the same thread.

---

