---
title: "Gnome vs KDE"
date: 2008-05-07
forum: Desktop Environments
---

### Post by PaoloRicardo on 2008-05-07
I'm new to Ubuntu and have just installed 8.04 with Gnome. I see a lot about KDE and was wondering how the 2 compare i.e. ease of use, flexibility, stability.

Can I install KDE for a trial as well as having Gnome in place? If so, how do I choose between the two?

Does the 8.04 release come with any KDE packages or do I have to install them through the Synaptic Package Manager?

Thanks

---

### Post by smartboyathome on 2008-05-07
It is really about what you like. You can install KDE and gnome on the same machine, though I wouldn't recommend it until KDE4.1 is released, as KDE4.0 is still in development and KDE3.5 is getting old. To install KDE3, install kde from synaptic. To install KDE4, install kde4 from the package manager.

---

### Post by sub2007 on 2008-05-07
Ease of use wise it's probably as easy to use as GNOME, if you're used to Windows it may feel more familiar than GNOME. It does give you more configuration options but everything is organised nicely into a control panel. It's all personal preference, I have used it both on Ubuntu and other distros and it does the job well, it's just I personally liked XFCE better.

If you want to try it you can install it by installing the kubuntu-desktop package. That will install KDE 3.5 rather than KDE 4. Don't worry about that as KDE 3.5 is rock solid and has been around for years and is worth sticking with (so I've heard) until KDE 4 becomes more usable. That will take care of everything. It's several hundred megabytes so if you have a slow connection it will take a while to download. To boot it you just click "Options" on the log on screen (where you enter your username and password) > Select Session > KDE. Then enter your username and password as usual and you will be in KDE! To go back to GNOME you just need to log out and reselect GNOME.

---

### Post by CP` on 2008-05-07
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)
That page talks about the very thing you want and also includes other really useful ubuntu tips.

---

### Post by NightwishFan on 2008-05-07
You can download Kubuntu live cd and do a fresh install or install the package on your existing Ubuntu:
```
sudo aptitude install kubuntu-desktop
```
You can easily switch between de's and wm's. Then after that is done reboot and choose "kde" from the login screen sessions menu. Also install fluxbox while your at it and try that out.
```
sudo apt-get install fluxbox
```
I highly recommend kde over gnome. Kde4.1 will be out around July and it is a good release.

To remove if you dont like it:
```
sudo aptitude remove kubuntu-desktop
```

If you want to try kde4.03 (its ok but kind of incomplete)
```
sudo aptitude install kubuntu-kde4-desktop
```

---

### Post by smartboyathome on 2008-05-07
I would recommend installing KDE4/KDE rather than kubuntu/kubuntu-kde4. It is lighter (Kubuntu KDE4 especially feels heavier than plain KDE4). Also, unlike the poster above, I still recommend you try out each and see what you like. I personally like GNOME, but you might like KDE4 better.

---

### Post by PaoloRicardo on 2008-05-07
Thanks to all who responded and so quickly. I'll certainly be giving KDE a try.

Thanks again

---

