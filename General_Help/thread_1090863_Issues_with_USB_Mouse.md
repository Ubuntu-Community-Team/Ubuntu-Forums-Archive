---
title: "Issues with USB Mouse"
date: 2009-03-08
forum: General Help
---

### Post by Archimedes0212 on 2009-03-08
Hey All -

I have a USB wireless mouse (Microsoft brand).  I've used it with previous versions of ubuntu perfectly fine.  However, recently it just doesn't want to work.  I've tried resetting the mouse and restarting my laptop.  When restarting my laptop, the mouse has decided that it will work for maybe five minutes before it becomes unresponsive again.  When I use it in Windows I have absolutely no problems.  Any ideas as to why it has stopped working for me in ubuntu.  (By the way, I am running Intrepid Ibex).

Thanks in advance

---

### Post by dcstar on 2009-03-08
> **Archimedes0212 said:**
> Hey All -

I have a USB wireless mouse (Microsoft brand).  I've used it with previous versions of ubuntu perfectly fine.  However, recently it just doesn't want to work.  I've tried resetting the mouse and restarting my laptop.  When restarting my laptop, the mouse has decided that it will work for maybe five minutes before it becomes unresponsive again.  When I use it in Windows I have absolutely no problems.  Any ideas as to why it has stopped working for me in ubuntu.  (By the way, I am running Intrepid Ibex).

Thanks in advance

If just the buttons stop working, then that is a know issue that is in Lauchpad, if everything stops working then that is something else.

---

### Post by Archimedes0212 on 2009-03-08
Yeah, everything stops working.  clicking doesn't work (right left or middle), the scroll wheel doesn't work, and when I move the mouse it doesn't move at all.

---

### Post by Archimedes0212 on 2009-03-09
bump

---

### Post by okamishadow on 2009-03-09
I have a similar issue... I was running the Ubuntu 8.04, then I upgrade to 8.10 and everything was normal... until I reboot. At the login screen I noticed I has no mouse... also no keyboard [only the leds works and the ctrl+alt+del to reboot]... I have that problem every I use my PC. I must enter to the boot options and use the recovery mode, choose fix the broken packages and boot as normal after that... The problem fixes but not permanently :(... Someone and idea [I'm already tryibg to update all the packs... again] :confused:

---

### Post by _hyphen on 2009-03-09
I have the same problem with my MX Revolution (as well as the previous wireless usb mouse I had). It makes me pretty sad, I haven't been able to run Ubuntu in either 8.04 or 8.10 because of this.

Mouse works fine in windows - but in linux (have tried ubuntu, fedora core 10 and openSUSE) the mouse becomes unresponsive after 5-10 minutes, and nothing but a reboot changes it, and even that is only temporary.

I have seen reports of this problem in  various places, but no definitive answers except for a few xorg changes that didn't stop it from happening, and a suggestion to disable legacy usb support which a)kills my keyboard at grub and b)didn't work anyhow(best I got directly in response on these forums was 'change your batteries', sheesh)

So, I am sadly stuck in XP until this wireless usb mouse issue is solved. I suspect it may be tied to specific motherboard models, as other people do have MX revolutions working fine - but whose to say for sure.

---

### Post by xdarkness2 on 2009-07-30
this issue appeared to me to, i have switched to kubuntu and found i had the same problem, due to the switch i now only know how to 'get the mouse back' in kde. Ive found a file called .gtkrc-2.0-kde4 in my home directory, which is also autostarted. If i start a session without this file everything runs smooth, but this file keeps returning after every logout, so somehow it is intergrated, but it seems also the cause of this mouse problem.
It must have come in with later updates or packages, i dont know which package it is so please if you do find out, bug report it for me, since i probably dont!

---

### Post by moss718 on 2009-08-01
I have also had this problem with both a wireless and usb wired setup in 9.04 on an asus board desktop. my previous computer worked fine with both kb/mouse setups (it had an intel board). Any moderate CPU usage freezes the mouse, but not the keyboard. I will look into the relative file in ubuntu. thanks.

---

