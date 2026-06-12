---
title: "Gnome-Shell Nvidia problems"
date: 2011-04-16
forum: Desktop Environments
---

### Post by da_marius on 2011-04-16
Hello,

I've been using Gnome-Shell from git for a while now and I just love it. The problem is that desktop effects aren't as smooth as they should be and I believe it's because of my graphics driver.

I have a Quadro FX 880M on my laptop and I'm using the proprietary 270.41.03 Nvidia driver from the ubuntu-x-swat ppa. Also my Ubuntu version is 10.10.

Gnome-shell is usable but the effects are a bit choppy (especially when I activate the overview). The problem is noticeable especially when there are windows with complex content like firefox.

I have also tried the live cds from the gnome 3 official website and there the effects ran a lot smoother. After searching a bit I found out that the os on that cd has the Nouveau driver.

So, hoping to obtain the same neat experience, I tried installing the libgl1-mesa-dri-experimental package. The shell does behave better but the driver seemed too unstable to me - the entire desktop would freeze for a few seconds when I launch an application from the shell overview and also some occasional crashing would occur.

To sum up, could someone please tell me: is there a way to improve gnome-shell's usability ? I would like to avoid at all costs things like compiling experimental drivers or stuff like that.

Thank you.

---

### Post by Krytarik on 2011-04-16
You could try upgrading the "nouveau" driver through Xorg-Edgers' PPA. Note that this would upgrade quite a lot of other packages as well, including the proprietary driver.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```
If you need/want to remove those PPA and downgrade the concerning packages again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
```

Greetings.

---

### Post by da_marius on 2011-04-16
Thanks. Should I purge the ubuntu-x-swat first ?

---

### Post by Krytarik on 2011-04-16
> **da_marius said:**
> Should I purge the ubuntu-x-swat first ?
Not necessarily. I'd leave it activated. This way, if you purge the Xorg-Edgers' PPA, you wouldn't 'fall down' to the official repo version of the proprietary driver.

---

### Post by qx48 on 2011-06-20
Would this procedure also work in 11.04? I'm showing that I have the NVidia proprietary driver installed, and that it is activated but not currently in use. I'm running Gnome-Shell instead of Unity, and I think my system could really benefit from being able to utilize my GTX260.

---

### Post by wildmanne39 on 2011-06-20
> **qx48 said:**
> Would this procedure also work in 11.04? I'm showing that I have the NVidia proprietary driver installed, and that it is activated but not currently in use. I'm running Gnome-Shell instead of Unity, and I think my system could really benefit from being able to utilize my GTX260.Hi, you dont have to worry about the not in use it is a bug, if you activated it and you see the green light it is working.

---

