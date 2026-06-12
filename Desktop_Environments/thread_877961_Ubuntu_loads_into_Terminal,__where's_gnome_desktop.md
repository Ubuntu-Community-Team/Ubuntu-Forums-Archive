---
title: "Ubuntu loads into Terminal,  where's gnome desktop enviornment?"
date: 2008-08-02
forum: Desktop Environments
---

### Post by HaulnAce600cc on 2008-08-02
Ubuntu was working just fine until I made two changes.  (V 8.04)  One recent change was I cleaned up the grub boot menu to get rid of all those extra Ubuntu selections.  The second change was I followed this website ( [ )]("https://help.ubuntu.com/community/SoundTroubleshooting?highlight=%28speakers%29%7C%284%29") to "purge" and "reinstall" the linux sound base.  I have never been able to get sound out of all 4 speakers which is really annoying and a topic for another discussion.


After I rebooted the startup process when as usual but after the loading graphic i get,
"kinit: name_to-dev_t(/dev/disk/by-uuid/bunch of #'s I won't type out)"
"kinit: trying to resume from /dev/disk/b-uuid/same bunch of numbers"
"kinit: No resume image, doing normal boot" 

Ubutu 8.04.1 mike-desktop tty1
mike-desktop login:

To me it appears as gnome has not loaded and I have no idea what I did or how to correct the problem.  As you may have guessed I'm not exactly command prompt savy.  I know just enough to get me in trouble and it seems it has.  

Please help.

---

### Post by sisco311 on 2008-08-02
log in and try to start gnome manually:
```
startx
```
or
```
sudo /etc/init.d/gdm start
```

if that doesn't work try to install the ubuntu-desktop package:
```
sudo aptitude install ubuntu-desktop
startx
```

---

### Post by HaulnAce600cc on 2008-08-02
Thank you for your quick response Sisco311.  

Startx did work and the desktop is back.

However, an error window was generated
"The panel encountered a problem while loading"
"OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete thie applet from your configuration?

Not sure what to do here.  It reminds me that I did recently add a user to the system, but I don't see why that would have caused this problem.

Any thoughts?

---

### Post by aysiu on 2008-08-02
Go to System > Administration > Synaptic Package Manager and make sure you have the *ubuntu-desktop* package installed.

---

