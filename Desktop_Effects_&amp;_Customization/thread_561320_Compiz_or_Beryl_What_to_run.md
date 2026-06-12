---
title: "Compiz or Beryl? What to run?"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by cudds on 2007-09-27
Hey gents,

I used to run xubuntu off my old laptop and could just get beryl to run. I was very happy :)

Now I just got hold of a Dell Vostro 1700 for work. I ran the guides on this forum and got my Nvidia GForce 8x card running ace! sweet.

I really like gnome so I'm glad I can run compiz straight from there.

The problem I have with it is that it's a lil too lightweight.

I used to love tinkering with berylmanager playing about with all the plugins and animations.

I have installed gnome-compiz-manager but it's really lacking in GUI features. 

For example I install via synaptics the compiz plugins but I can't see a way of enabling these. I've read that compiz is the future of Beryl and I can't wait to get all of those 3d/reflections going on - but right now I can't see an easy way of administering it. 

Am I being dumb or is Beryl the lazy man's joy?

---

### Post by PmDematagoda on 2007-09-27
The answer for me was to run, Compiz-Fusion, the fusion of Beryl and Compiz:).

---

### Post by FuturePilot on 2007-09-27
Check the blue link in my sig for a nice Compiz manager. Just note that the Compiz that comes with Ubuntu Feisty is not Compiz Fusion but the old Compiz.

---

### Post by cudds on 2007-09-27
thanks guys - so all the cool vids I've seen are compiz-FUSION!

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) is a good looking tutorial for removing the plain compiz and putting all the jazz on

---

### Post by Rupertronco on 2007-09-27
Forlong's guide has been successful for many people, I highly recommend it. He's also around here pretty frequently to help people out. 

In case you were wondering, the original project was called Compiz (that's what you currently have) It then forked into a project called beryl (second iteration of the compiz project) and now it has reunited to become compiz-fusion. Compiz-fusion will come with a configuration settings manager (ccsm) that will allow you to easily change all of the features compiz provides. When you have compiz installed, just type [code[ccsm[/code] in a terminal or the run box to bring up the settings manager.

---

### Post by cudds on 2007-09-27
Thanks for the info - I remember reading about forking or something but I didn't understand what it meant 

Ok - so I followed the guide to a tea and I've got a wee problem. When I run ```
compiz --replace
``` I get

```
dan@dan-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7597): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

ekkkk - ok what have I got

well I've got a vostro 1700. Graphics wise -256mb NVIDIA GeDorce 8600M GT. Got the driver from their site - got my resolution up to 1440x900 by tweaking the xorg.

So what could be the problem. My xubuntu is mocking my big fancy laptop now! lol

---

### Post by cudds on 2007-09-27
Started a new thread as this was just talking about compiz-manager

---

### Post by davedumas0 on 2007-09-27
try to follow this thread [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)
but skip part 1

---

### Post by Rupertronco on 2007-09-27
I don't think the driver from the Nvidia site has 3-d acceleration. Try using Envy to get your newest driver.

Type glxgears in a terminal and see what happens.

---

### Post by FuturePilot on 2007-09-27
> **Rupertronco said:**
> I don't think the driver from the Nvidia site has 3-d acceleration. Try using Envy to get your newest driver.

Type glxgears in a terminal and see what happens.

Where do you think Envy gets the driver from?;)

---

### Post by Rupertronco on 2007-09-28
I really have no idea what Envy does, I've never used it. I always do my own driver installation. The recommendation came from the success I've heard people have with it.

---

