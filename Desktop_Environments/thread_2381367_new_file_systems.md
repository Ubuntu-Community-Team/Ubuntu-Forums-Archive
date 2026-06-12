---
title: "new file systems"
date: 2017-12-30
forum: Desktop Environments
---

### Post by okkadiroglu on 2017-12-30
Hi,

I have a SSD and a HD in my computer. Few days ago when I used System Monitor and checked the File Systems I found two more file systems appeared without my knowledge. They are 100% full and their type is squash ( What ever that is). One is /dev/loop1/snap/gnome/calendar 106.4MB and the other is /dev/loop(/snap/core/3604 87.9MB. What are they and why did they appeared? When I enter /dev directory I can not see loop1 or loop( directories. Are they necessary, if not how do I get rid of them?

Best Regards and happy new year.

---

### Post by QIII on 2017-12-30
Have you installed any Snap packages?  Snap uses SquashFS.  They also use loop devices, which are more or less expected to be 100% full.  A loop device simply makes a file available as a block device for mounting.

That was probably as clear as mud.

Short version:  If you have installed Snaps, that's why you see that and it's OK.

---

### Post by okkadiroglu on 2017-12-31
Thank you very much for your prompt reply. I have no idea about any snap packages and how did they get into my computer. Can I get rid of those devices and if so how?

Happy new year and best regards

---

### Post by flocculant on 2017-12-31
> **okkadiroglu said:**
> ... I have no idea about any snap packages and how did they get into my computer...

Open a terminal.

```
snap list
```

```
sudo snap remove <package>
```

[https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)

---

### Post by deadflowr on 2017-12-31
> I have no idea about any snap packages and how did they get into my computer.
You're not alone.
The software center, or Ubuntu Software, allows you to install snaps, and unless you have a keen eye for detail, would not have noticed anything different from the normal Debian software packages Ubuntu has historically used.
The one thing you might have noticed would have been duplicate entries for some packages, such as LibreOffice as there is both a snap and Debian package for that and both are listed in the software center.

---

