---
title: "Changing brightness o various other n latitude D600 makes the system almost unusable"
date: 2009-02-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cannotcompute on 2009-02-11
I posted yesterday that the Ubuntu main menu and various other things randomly stopped working, but all at the same time. Well, it's not doing it randomly anymore, but it still does whenever I adjust the brightness.

Whenever I adjust the brightness (with the Fn-Up and Fn-Down hotkeys) it adjusts the brightness just fine, but the brightness adjustment box on the screen never disappears, and the Ubuntu main menu tabs don't open when I click them (however they highlight as if clicked if you even hover over them.)
.
This also seems to affect the menus in some applications, such as the terminal. Another thing that happens at the same time is that the keyboard stops responding.

Between these two problems, me accidentally adjusting the brightness can cost me all the work I've done since last saving (I have a bad habit of not saving often.)

And last but not least, it hasn't happened since yesterday, but sometimes after waking up from hibernation this problem will trigger on its own, without me even touching the brightness.

My specs:
Dell Latitude D600
Ubuntu Intrepid
768MB RAM (checked for errors, all good :\)

---

### Post by Cannotcompute on 2009-02-11
Damn my randomly clicking touchpad! The title is supposed to say "Changing brightness or various other things make the system almost unusable"

---

### Post by superm1 on 2009-02-11
Please make sure you perform ALL updates.  This is supposed to be addressed in the intrepid-updates.

---

### Post by Cannotcompute on 2009-02-12
All updates were installed right after I installed Ubuntu (~3 days ago)

---

### Post by superm1 on 2009-02-12
Then can you post your dmidecode output?  Lets see if your system needed a different quirk.

---

### Post by Cannotcompute on 2009-02-12
Here you go, I had to use an attachment because it's really long.

---

### Post by superm1 on 2009-02-12
Ah yup.  Your BIOS reports it as "Dell Computer Corporation" not "Dell Inc."

This means that bug [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721?comments=all)

is what's affecting you.  At some point it should land in intrepid-updates hopefully, but for sure it's fixed in jaunty already.

---

### Post by Cannotcompute on 2009-02-12
All right thanks for your help. I can wait for a fix. In the mean time, I've learned to stay away from the brightness adjustment keys.

---

### Post by stealinglight on 2009-02-17
... I have the same issue with my d600 its annoying cause I always use my laptop in low light so it hurts after awhile....

so is the bug going to be fixed in the next batch of updates for 8.10 or we just have to wait till 9.x ????

---

### Post by superm1 on 2009-02-18
> **stealinglight said:**
> ... I have the same issue with my d600 its annoying cause I always use my laptop in low light so it hurts after awhile....

so is the bug going to be fixed in the next batch of updates for 8.10 or we just have to wait till 9.x ????
It should be fixed in the next batch of updates.  Turn on -proposed and you will be getting them, until they get added to -updates

---

