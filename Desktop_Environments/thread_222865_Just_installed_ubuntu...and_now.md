---
title: "Just installed ubuntu...and now"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Kl0wN on 2006-07-25
I cant change the screen res..its stuck at 640 when I need it to be at 1024x768 ..and also, how do I update my ubuntu?

---

### Post by bulldog on 2006-07-25
Install the drivers for your videocard.
That should help.
You can look at Automatix or EasyBuntu to help you to install these for you and a lot more if you want.

Update should be done automaticly but you can type in console:
sudo aptitude update
sudo aptitude upgrade

---

### Post by Kl0wN on 2006-07-25
How do I get in console?

---

### Post by ndyguy on 2006-07-25
> **Kl0wN said:**
> How do I get in console?

Applications>Accessories>Terminal

---

### Post by endfx on 2006-07-25
You can change your screen resolution in a couple of ways:

1. System -> Preferences -> screen resolution


or 

2. edit /etc/X11/xorg.conf
Step 2 requires some linux experience and is not very intuitive.

---

### Post by bulldog on 2006-07-25
If you decide to take step 2 make sure to backup your original xorg.conf!
sudo cp etc/X11/xorg.conf /etc/X11/xorg.conf_backup
If you make a mess you can put the backup back.
But if you are unsure what to do,don't go messing with xorg.conf or you're end up with a console and no graphic's.

When you're new to Linux,read a lot off stuff to learn how it works.
Try to understand the basic's.
But if you can't change your resolution try to install the drivers for your card.

---

