---
title: "Installing KDE in Ubuntu."
date: 2007-05-27
forum: Desktop Environments
---

### Post by loathsome on 2007-05-27
Hi there,

I'm going to set up KDE at my Ubuntu box, but what's the preferred way? Should I grab the «kubuntu-desktop» package, or just the «kdebase» and set up each application manually?

I've read various places that it might be a bit «buggy» running KDE on Ubuntu, anybody have any input on this?

Thanks!

---

### Post by Bachstelze on 2007-05-27
Your best bet is to install *kde-core* and then add extra packages to your liking.

---

### Post by Kobalt on 2007-05-27
+1 for KDE-core. [Here]("http://www.psychocats.net/ubuntu/kde-core") is why.

---

### Post by loathsome on 2007-05-27
Great, I'll go with kde-core then ;)

---

### Post by PatrickMay16 on 2007-05-27
> **HymnToLife said:**
> Your best bet is to install *kde-core* and then add extra packages to your liking.

I would second this. I tell you, I tried this on my laptop and it worked great.

---

### Post by Happy_Man on 2007-05-27
KDE-core. Easy, heck no. Streamlined and slick, hell yes.

---

### Post by loathsome on 2007-05-27
Easy? I sat kde-core up in two minutes, and now I'm «dualenvironmenting» :lolflag:
Kde-core wins. I hated the kubuntu-desktop package, with lots and lots of unnecessary things.

Oh, I miss *one thing*, though :P anybody knows which package to grab for the volume control in the taskbar? Thaks!

---

### Post by Happy_Man on 2007-05-27
I think it's Kmix, could be wrong, though.... :lolflag:

---

### Post by loathsome on 2007-05-27
Grrreat, thanks a lot! Was kmix :D Grabbed it and created a symlink in ~/.kde/Autostart

---

### Post by 13thMonkey on 2007-05-27
Don't forget that you can install kde-desktop and then uninstall stuff you really don't want afterwards. (It's a while since I've done it so you may or may not get warnings about uninstalling kde-desktop, but it's safe to do so as long as you just stick to applications).

---

### Post by Happy_Man on 2007-05-27
> **13thMonkey said:**
> Don't forget that you can install kde-desktop and then uninstall stuff you really don't want afterwards. (It's a while since I've done it so you may or may not get warnings about uninstalling kde-desktop, but it's safe to do so as long as you just stick to applications).
Actually, there was this one guy on the forums this morning, tried to uninstall Kopete, and took the entire damn install down with him. Just to check, I typed it in, and it really did want to get rid of the entire package. Twas kinda scary.... I used apt-get, btw.

---

### Post by 13thMonkey on 2007-05-27
For kde-desktop (no such thing), read kubuntu-desktop. #-o - my bad!

Kubuntu-desktop is a meta-package of all the various libraries and apps that make up KDE/Kubuntu. It's perfectly safe to uninstall applications you don't need.

From the description/info in synaptic/adept
> 
This package depends on all of the packages in the Kubuntu desktop system
It is safe to remove this package if some of the desktop system packages are not desired.

---

### Post by Obed on 2007-05-28
I just installed KDE in Ubuntu but I don't like it. I do not how to go back to the Gnome desktop. What can I do to reinstall the Gnome desktop. Anyone can help me?:confused:

---

### Post by Happy_Man on 2007-05-28
In the login screen, in the bottom left, there is Options --> Sessions. Choose GNOME and log back in. Ta-da!

---

### Post by loathsome on 2007-05-28
> **Obed said:**
> I just installed KDE in Ubuntu but I don't like it. I do not how to go back to the Gnome desktop. What can I do to reinstall the Gnome desktop. Anyone can help me?:confused:
```
sudo aptitude remove <thepackageyouinstalled>
```

---

