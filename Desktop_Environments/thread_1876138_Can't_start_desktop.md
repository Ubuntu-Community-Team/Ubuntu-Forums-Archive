---
title: "Can't start desktop"
date: 2011-11-05
forum: Desktop Environments
---

### Post by calelettus on 2011-11-05
I broke: usr/share/X11/xorg.conf.d/50-synaptics.conf and now I can't login. The screen just stays black.

How can I fix this? (I have little experience working command line and I can't seem to edit that file to undo what I did. Nor can I delete it.)

I tried sudo dpkg-reconfigure xserver-xorg-input-synaptics but that didn't work.

---

### Post by Rodney9 on 2011-11-05
I'm no expert, but I couldn't leave a fellow Lubuntu user stranded.

This post maybe of help [http://ubuntuforums.org/showthread.php?t=1150319&page=2](http://ubuntuforums.org/showthread.php?t=1150319&page=2)

worth trying, thanks to Pastalavista, -

```
sudo apt-get remove --purge xserver-xorg
```

```
sudo apt-get install xserver-xorg

```
```
sudo dpkg-reconfigure xserver-xorg
```


Rodney

---

