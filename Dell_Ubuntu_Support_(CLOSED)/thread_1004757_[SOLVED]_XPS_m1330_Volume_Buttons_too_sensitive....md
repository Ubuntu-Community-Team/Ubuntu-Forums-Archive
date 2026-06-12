---
title: "[SOLVED] XPS m1330 Volume Buttons too sensitive..."
date: 2008-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by x C0MMAND0 x on 2008-12-07
The volume control buttons work just fine; that is not the issue.  The problem is that the volume controls are waaaay to sensitive.  No audio is heard until the volume is about 60% up, and then after that each "step" up makes the volume significantly louder until it is too loud.

---

### Post by x C0MMAND0 x on 2008-12-08
Anybody?  I have tried searching around, but I can't figure it out at all.

---

### Post by cisoprogressivo on 2008-12-08
If you want, you can blacklist the "video" module, and this will solve the problem.

---

### Post by Technoviking on 2008-12-08
**Do not** blacklist the video module in Intrepid, it cause other problems.

---

### Post by x C0MMAND0 x on 2008-12-08
Okay, thanks, but where does that leave me now?

---

### Post by haveblue on 2008-12-09
I have the exact same problem, and I stumbled across a solution while looking for something else..

Open up gconf-editor, and go to apps > gnome-settings-daemon, and change volume_step as needed. Changing from 6 down to 4 seemed to work well for me.

---

### Post by x C0MMAND0 x on 2008-12-09
> **haveblue said:**
> I have the exact same problem, and I stumbled across a solution while looking for something else..

Open up gconf-editor, and go to apps > gnome-settings-daemon, and change volume_step as needed. Changing from 6 down to 4 seemed to work well for me.

Thank you SO much, that is EXACTLY what I was looking for.  I changed it to 2, but I guess I just like to be able to really finely tweak the volume.  Thanks again.

---

### Post by mbeach on 2008-12-11
same issue on a dell studio 17.  thank you for the setting adjustment.

---

### Post by Gooler on 2008-12-11
As a tip, I've also noticed this on Kubuntu Intrepid with the same laptop.

To solve it, go to System Settings, Keyboard & Mouse, and play with Delay values. I've set mine to 600 and I'm glad with it.

---

### Post by undoIT on 2009-12-25
> **Gooler said:**
> As a tip, I've also noticed this on Kubuntu Intrepid with the same laptop.

To solve it, go to System Settings, Keyboard & Mouse, and play with Delay values. I've set mine to 600 and I'm glad with it.

Thanks. 600 works well for me.

---

### Post by log0 on 2010-06-30
Didn't work for me :(. 
Changing this setting do nothing. I've got an external usb soundcard if it can help.
It was working fine before Lucid lynx...

---

### Post by Graeme Jackson on 2011-01-24
Thank you guys so much - this has been one of my "favourite" bugbears with linux.

---

### Post by albannach1 on 2011-04-16
Solved! This was my biggest annoyance with the sound on ubuntu 10.10

---

