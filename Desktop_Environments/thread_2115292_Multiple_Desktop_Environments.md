---
title: "Multiple Desktop Environments"
date: 2013-02-12
forum: Desktop Environments
---

### Post by ooleyguy on 2013-02-12
I have 8 TB of space on my computer and have a fast processor, lots of RAM, etc. Is there any significant drawback to installing multiple desktop environments? Before I install more than just Unity, are there any tips on how to make the process smooth?

---

### Post by sudodus on 2013-02-12
It costs storage space on the HDDs, but that is no problem for you. It might also add doublets to some of the menu, but that is no big problems. Either you live with it, or you tweak the menus to remove, what you don't want.

I have Ubuntu 12.04 LTS plus the desktop environments of Kubuntu, Lubuntu and Xubuntu. It is easy to install:

```
sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```

You select which desktop environment to run at the log in screen.

If you want to clear out all but one, you can find how to do it at the following link

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by ooleyguy on 2013-02-12
Thanks, dude. I was worried about the fact that KDE use QT libraries and Gnome and the others use GTK+ libraries.

---

### Post by unheeding on 2013-02-12
> **ooleyguy said:**
> Thanks, dude. I was worried about the fact that KDE use QT libraries and Gnome and the others use GTK+ libraries.

It shouldn't matter unless you are running KDE application in GNOME and vice versa.  The only issue with that is that you'll be pulling in extra libraries and using up more system resources.  Sounds like your computer is more than capable though.

---

### Post by sudodus on 2013-02-13
> **unheeding said:**
> It shouldn't matter unless you are running KDE application in GNOME and vice versa.  The only issue with that is that you'll be pulling in extra libraries and using up more system resources.  Sounds like your computer is more than capable though.
Even that is possible :-) It is perfectly OK to run KDE applications in Gnome, XFCE or LXDE and vice versa. The GUI style will be different, but it works. I do it all the time. For example I use DigiKam and k3b from KDE in Lubuntu Desktop with LXDE.

But there will be some extra libraries and applications that are more or less doublets, that fill disk space.

---

### Post by Frogs Hair on 2013-02-13
You will end up few duplicate applications. With The XFCE session I  now have two image viewers, screen shot tools,file managers, terminals,archive mounters and so on. The session has far fewer applications than Xubuntu desktop though.

---

