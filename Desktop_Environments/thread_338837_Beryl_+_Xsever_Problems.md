---
title: "Beryl + Xsever Problems"
date: 2007-01-15
forum: Desktop Environments
---

### Post by Eman64 on 2007-01-15
Hey guys,
I just installed 6.10 onto my new hard drive and I wanted to use beryl, so I followed [this]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto") and what I got was a xserver failure saying no screen could be found. So I do a quick "sudo dpkg-reconfigure xserver-xorg" and then reboot GDM. I then login on my account and launch firefox, but my window border is metacity, not beryl. I try to change and it won't work. 
Did I miss a step in the installation? Is there some kind of a xserver update that doesn't allow that driver anymore? 
Thanks for the help.

---

### Post by orb9220 on 2007-01-15
Did you?

> Code: sudo nvidia-xconfig --add-argb-glx-visuals

Should backup and update your xorg.conf with compositing.

and 

> sudo apt-get install beryl emerald-themes

What graphics driver did you install?

---

### Post by Eman64 on 2007-01-15
Yes, I did do that and I installed nvidia-glx

---

### Post by Eman64 on 2007-01-15
Update: I used envy to install my driver and it worked great, but when I launch beryl it says
```
person@computer:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```
Any clue how to fix this?

---

### Post by Eman64 on 2007-01-16
**B**utt
**U**p
**M**y
**P**lace

---

