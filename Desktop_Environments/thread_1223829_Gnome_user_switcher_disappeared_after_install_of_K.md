---
title: "Gnome user switcher disappeared after install of KDE 4"
date: 2009-07-26
forum: Desktop Environments
---

### Post by idris83 on 2009-07-26
Hello,

I recently installed KDE 4 in my Ubuntu 9.04 x86 system by typing

```
*sudo apt-get install kubuntu-desktop*
```Since then, the user-switcher menu (the one with all the power-off options, and the pidgin status changer that sits in the top-right corner of the gnome desktop) has vanished!

Has this happened to anyone else? Is there a config file I can delete or tweak to put things back like they were back in the good old days?

Also, I tried uninstalling kubuntu-desktop by running the above procedure in reverse, but it merely removed a pseudo-package which was 50kb big and left all the other KDE 4 junk the way it was! Lame!

Thanks,
Idris

---

### Post by wojox on 2009-07-26
Try here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by idris83 on 2009-07-26
> **wojox said:**
> Try here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Hmmm yes, I had seen that... the thing is I do actually use some KDE apps from time to time, just not the KDE desktop. I was a bit worried that by uninstalling all of that stuff, I wouldn't be able to run any KDE apps. So I just left them all there... but curiously, the gnome user switcher stopped working after I installed KDE 4.

Any idea how I can track down its problem? Where do gnome desktop error messages go?

---

### Post by Chronon on 2009-07-27
Maybe installing KDE changed your display manager.  Try this:
```
sudo dpkg-reconfigure gdm
```

Select GDM and see if it changes this.  I use KDM but have both Gnome and KDE on my desktop system.  Gnome won't let me switch users because of this.  (However, I get warned that I need to use GDM to switch users in Gnome, so I'm not totally sure this is the same problem.)

---

### Post by idris83 on 2009-07-28
> sudo dpkg-reconfigure gdmFixed.

Another thing I did was remove the broken user switcher from the panel and re-add it. Obvious I know, but it was only about 1 pixel wide so easily overlooked.

---

