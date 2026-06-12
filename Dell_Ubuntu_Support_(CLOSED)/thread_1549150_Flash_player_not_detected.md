---
title: "Flash player not detected"
date: 2010-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jocando on 2010-08-09
Hi

I have a Dell Inspiron 910 notebook with Ubuntu 8.04 installed.

Recently there were some upgrades, and now I can't see Flash on websites.  I get the message 'You need to install Flash player'. But Flash player is installed and it worked fine before the upgrades.

When I go to 'Add/Remove programs', Flash player (Adobe Flash Plugin 10) is listed as installed, and it won't let me remove it.

Has anyone else had this problem?  Is there a fix that doesn't involve upgrading to Ubuntu 10.4?  (I'm an Ubuntu beginner, but learning fast.)

Thanks!

---

### Post by tcopeland on 2010-08-09
Add/Remove Programs is in Windows. You need to also install it in Ubuntu. It doesn't work across platforms. However, I never used 8.04 so there might be something called Add/Remove Programs in it.

---

### Post by jocando on 2010-08-09
In Ubuntu 8.04 there's a menu option called 'Add/Remove' which is short for 'Add/Remove Applications'.  Apologies if my writing 'Add/Remove programs' was confusing.

Flash has always worked fine on Firefox on my notebook.  (I bought it in Feb 09), and as I said, Flash player is already installed. This is a new problem that has only started since installing the upgrades.

Hope someone can help.

Thanks

---

### Post by tcopeland on 2010-08-10
Are you running 32 bit or 64 bit?
If you're running 64 bit, Adobe has dropped support for 64 bit flash. However just download [[COLOR="Blue"]this file[/COLOR]]("68.33.147.239/flash/libflashplayer.so") (it will be in "Downloads", of course), then go to your home folder. Then, reveal hidden files (Ctrl+H), and go to the folder ".mozilla". Right click, and make a folder called "plugins". Deposit the attached file in the plugins folder. It doesn't matter what browser you're running, it just needs to be in the Mozilla folder even if you don't use Firefox. If you're on 32 bit, your best bet at the moment is a reinstall. On the note of you not being able to remove your current version, I don't know if Add/Remove Progs. is part of nautilus. Once again, I never used Hardy Heron, so I don't know much about it. I moved away from Ubuntu a while ago because my tablet didn't have good hardware support. If you could show me the process of just going into the add/remove programs, I could understand better. Go into a terminal, and type:```
sudo apt-get install gtk-recordmydesktop
```
then enter your password. If it asks for yes or no, type y+enter. Then, when it's done, go to apps. -> sound and video -> gtk-recordmydesktop. Don't worry about quality settings, just hit save as and type what you want it to save as. Keep it as .ogv. Hit record. You'll see an icon in your top panel. When your done recording going into add/remove, click the icon in the panel and hit stop. Let it encode. Send me the file. I'll take a look and we'll go from there. This looks like a lot to do but I just feel the need to really type out really long stuff :D. Also, I have a feeling Add/Remove is the same as the Software Center in Lucid and up. In addition, you should upgrade to lucid. Back up all of your stuff and upgrade. It's LTS, so don't worry about that. It also has way better hardware support.

---

### Post by linux18 on 2010-08-11
get the flash aid extension for firefox

---

### Post by colintivy on 2010-08-11
8.04 automatic update just put Flashplayer 10 on this laptop and it seems to work fine!

:D

---

### Post by jocando on 2010-08-11
Thanks for all the tips.

I've just run Flash Aid Extension and it's worked!  Everything's back to normal - Flash working fine. Thanks linux18.

Jo

---

### Post by linux18 on 2010-08-11
your welcome, if there's one thing I'm good in at linux it's multimedia and freeing disk space

---

