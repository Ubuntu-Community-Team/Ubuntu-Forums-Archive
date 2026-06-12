---
title: "Screen Alignment Issue: Dual Boot"
date: 2006-08-17
forum: Desktop Environments
---

### Post by mtb on 2006-08-17
I have just finished installing and configuring Ubuntu Desktop 6.06 to dual-boot alongside my current Windows XP Home installation. I am impressed, it was flawless.

My only issue is that the position of the screen on my monitor is aligned slightly to the right. This can be fixed by manually adjusting the monitor. However when I boot back into Windows, the alignment here is now incorrect.

Any suggestions? Thanks in advance.

---

### Post by mtb on 2006-08-18
Installed the latest nVidia drivers and the issue has been resolved.

Thanks for your help... or not.

---

### Post by Pantuflo on 2006-08-19
Sorry, I also have this issue and I would like to know how did you installed your nvidia drivers (if you have followed some howto or special link with detailed instructions... ;) ).

I have tried to install the drivers by following the Ubuntu desktop manual (install some drivers by Synaptic), but I made a mistake and the graphical interface became un-bootable... Now I have re-installed Ubuntu (:) it was a clean install), and I would like to know a safer method.

Thanks.

---

### Post by Horatio on 2006-11-26
I was searching for the solution to this problem, but the answer has yet to be given. I have a nvidia Vanta for video, and I am using the nv driver currently. Isn't there a utility to adjust the screen? I remember doing this with SuSe years ago, but sax2 is not standard in Ubuntu.

---

### Post by CatKiller on 2006-11-26
It depends on how you definethe answer being given. For most people, using the **nvidia** driver makes the problem go away.

If you want to keep using the **nv** driver, I believe you can use **xvidtune** to work out what a custom modeline should be to have the alignment that you want, and then you can put that modeline in your xorg.conf. I've neither done it, nor looked for step-by-step instructions.

---

### Post by vtel57 on 2006-11-26
Installing the current Nvidia drivers will solve this problem. However, if the installation does not reconfigure your xorg.conf file properly to reflect the new driver usage (nvidia, NOT nv), then you'll have to edit the file manually using your favorite editor.

For newer users of Linux, the absolute easiest way to install the Nvidia drivers, and many other useful applications, is with [Automatix]("http://www.getautomatix.com/").

Luck!

~Eric

---

