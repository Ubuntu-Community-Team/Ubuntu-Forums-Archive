---
title: "Xorg.conf help please"
date: 2005-04-23
forum: Desktop Environments
---

### Post by audaz on 2005-04-23
Maybe I just need better forum skills, but I can't seem to find what I need here or on the wiki.

I am trying to get my video card (ATI, last time I buy one of those) and my intellimouse side buttons working. I am following the instructions from the howto section, and they both say I need to edit xorg.conf. 

Here's the problem: xorg.conf is read-only, and I can't even make a backup file of it. I try to save as xorg.conf.save, but I just get a generic error saying that it can't save.

After I make my backup xorg.conf file, I will want to edit a couple lines in the original to make my video card and mouse work properly, but I can't edit it. Please let me know how to edit this read-only file.

Thanks for your help.

---

### Post by soce_32 on 2005-04-23
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save
sudo vi /etc/X11/xorg.conf (substitute gedit or nano for vi if you so desire)

You will need to use sudo before your commands when working with files in /etc.

---

### Post by audaz on 2005-04-23
Thanks. I somehow didn't see that i wasn't using sudo. Now it's working.

---

