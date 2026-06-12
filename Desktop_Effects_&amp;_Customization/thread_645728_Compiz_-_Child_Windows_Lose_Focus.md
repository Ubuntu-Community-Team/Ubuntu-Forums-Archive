---
title: "Compiz - Child Windows Lose Focus"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by carney1979 on 2007-12-20
Running a fresh i386 install of Gutsy on a desktop box with Compiz/Emerald running and CCSM installed.

With some applications, notably Firefox, when a child window appears, such as a download dialog, it quickly disappears behind the main (parent) window.

How do I stop this from happening?

David

---

### Post by Nano Geek on 2007-12-20
Could you take a screenshot of the **Focus & Raise Behavior** tab under **General Options** in ccsm?

---

### Post by carney1979 on 2007-12-21
Here's the screenshot.

David

---

### Post by Nano Geek on 2007-12-21
The only thing different on mine is that **Click To Focus** is checked, and **Auto-Raise Delay** is set to 1000.

You could try those settings, but I'm not sure they would help.

---

### Post by omegamike3 on 2007-12-21
> **asjdfwejqrfjcvm msz34rq33 said:**
> The only thing different on mine is that **Click To Focus** is checked, and **Auto-Raise Delay** is set to 1000.

You could try those settings, but I'm not sure they would help.

I have the same settings, as they are the defaults, and am experiencing the same problem. I've noticed it in Firefox and Evolution mostly, however it's not terribly consistent.

---

### Post by battlesound on 2008-01-08
Same problem here.  I've tried using the GL desktop thing... I think now it's called "compiz-gnome," and that worked on my laptop, but not on a desktop with an Nvidia GeForce 8600 GT.  

You guys can try that package it may fix this problem... if you have problems with window borders, that will do it... lose window borders during a session and click on the installed "gl desktop" from that package (system>preferences>gl desktop) will bring them back.

Has anyone solved this problem... it must be an option line in the xorg.conf file.

I'm going to try using the latest nvidia driver from their website to see if that does it.

---

### Post by battlesound on 2008-01-08
Ohh... I have the same problem with it always doing the auto raise thing all the time.  It won't switch off!

Plus I can't use the ccsm effects... they seem to not respond well at all just like this change in the general portion of ccsm.

I'm confused a bit on this one.

---

### Post by battlesound on 2008-01-09
Well, I solved my problem.  It's a bit different, but it's still similar enough.  So take a look at my solution if you want.  See if that works for you guys!

thread:
[http://ubuntuforums.org/showthread.php?t=613156&highlight=compiz+focus]("http://ubuntuforums.org/showthread.php?t=613156&highlight=compiz+focus")

---

