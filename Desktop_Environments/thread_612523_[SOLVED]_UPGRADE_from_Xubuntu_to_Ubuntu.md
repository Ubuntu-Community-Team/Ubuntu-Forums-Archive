---
title: "[SOLVED] UPGRADE from Xubuntu to Ubuntu"
date: 2007-11-14
forum: Desktop Environments
---

### Post by frayalejandro on 2007-11-14
I'm trying to upgrade from Xubuntu 7.04 to Ubuntu, at least I prefer to have the Ubuntu desktop. I can´t install Ubuntu from my CD.

Reading some similar posts, I already did this from the synaptic manager:
- I installed Gnome.
- I installed de Ubuntu desktop.
- I unmarked "allow Xfce to manage your desktop" from the desktop manager.

WHAT ELSE SHOULD I DO....????
 I´M STILL GETTING THE SAME DESKTOP, WITHOUT THE PLACES, SYSTEM, ETC...

---

### Post by rsambuca on 2007-11-14
Follow these [instructions.]("http://www.psychocats.net/ubuntu/puregnomefeisty")

---

### Post by frayalejandro on 2007-11-14
Thanks for your fast answer. I will first upgrade to 7.10

39 and retired?

---

### Post by rsambuca on 2007-11-14
If you upgrade to Gutsy, you will have to use different [instructions.]("http://www.psychocats.net/ubuntu/puregnome") (There are different packages for Gutsy than Feisty).

And yup.  Just lucky I guess.

---

### Post by K.Mandla on 2007-11-14
Moved to Desktop Environments.

---

### Post by frayalejandro on 2007-11-15
Well, I followed those instructions, and all is now a mess. For some reason, Ubuntu desktop didn´t get installed, and now I deleted the Xfce desktop!

I believe now I have to reinstall Xubuntu, right? :(

---

### Post by rsambuca on 2007-11-15
What happens when you try

sudo apt-get install ubuntu-desktop

---

### Post by frayalejandro on 2007-11-15
> **rsambuca said:**
> What happens when you try

sudo apt-get install ubuntu-desktop

I´m kind of new in Linux and Ubuntu. So, this is what I did: 
From the synaptic manager, I checked "Ubuntu desktop" for installation. When it finished, I supposed it had allready installed the new desktop ( I didn´t type the above command from the terminal window). Then, I removed Xfce, and now I  have no menus. I can only access Firefox.

I´m really not mad at all. It´s OK for me to learn from my own mistakes. :)

Anyway, should I reinstall Xubunt back again or is there a shortcut to open the synaptic mannager or the terminal window?

---

### Post by rsambuca on 2007-11-15
> **frayalejandro said:**
> I´m kind of new in Linux and Ubuntu. So, this is what I did: 
From the synaptic manager, I checked "Ubuntu desktop" for installation. When it finished, I supposed it had allready installed the new desktop ( I didn´t type the above command from the terminal window). Then, I removed Xfce, and now I  have no menus. I can only access Firefox.

I´m really not mad at all. It´s OK for me to learn from my own mistakes. :)

Anyway, should I reinstall Xubunt back again or is there a shortcut to open the synaptic mannager or the terminal window?

You need to reboot

---

### Post by frayalejandro on 2007-11-15
Well, I allready did that several times.

---

### Post by rsambuca on 2007-11-16
Do you get a login screen?

---

### Post by frayalejandro on 2007-11-20
Yup! And, reading the instructions you sent me, I realized I have to change my session to Gnome in the login screen.

It works perfectly!! Thank you very much! :)  :)  :)

---

