---
title: "Help!!"
date: 2005-09-16
forum: Desktop Environments
---

### Post by no.one on 2005-09-16
I have just installed Breezy and am unable to do anything.  My computer freezes at the splash screen.  My mouse appears, and I can use it for a second, then everything freezes.  I have to pull the power cord to shut it down, I'm glad that I decided to dualboot Ubuntu with Windows.
I had this same problem with Hoary.

---

### Post by mlomker on 2005-09-16
> own, I'm glad that I decided to dualboot Ubuntu with Windows.
I had this same problem with Hoary.

Did you fix it in Hoary or just decided to upgrade to Breezy to see if the problem would go away?

It could be the video card that was detected.

You can try selecting 'rescue' from the grub menu.  Once you get to a prompt type **dpkg-reconfigure xserver-xorg**.  It'll ask you a bunch of questions about your video card and monitor.  If you aren't sure about the answer then pick the more conservative option.  Once you get into the desktop you can select a higher resolution.

---

### Post by no.one on 2005-09-16
I never resolved it in Hoary.
I'll try the command in Grub.

---

### Post by no.one on 2005-09-17
Okay, sorry for the delay.
I tried the command, went through the setup, and rebooted.  Tried to boot Ubuntu normally and received endless "The failed 'Read Cd/Dvd Capacity' packet cammand was:" errors.  Any thoughts?

---

### Post by mlomker on 2005-09-17
[QUOTE=no.one]Okay, sorry for the delay.
I tried the command, went through the setup, and rebooted.  Tried to boot Ubuntu normally and received endless "The failed 'Read Cd/Dvd Capacity' packet cammand was:" errors.  Any thoughts?[/QUOTE]

Never heard of it.  My usual troubleshooting process is to write down the error message word for word and then search Google.

---

