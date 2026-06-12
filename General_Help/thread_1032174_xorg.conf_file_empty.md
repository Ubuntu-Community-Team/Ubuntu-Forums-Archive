---
title: "xorg.conf file empty"
date: 2009-01-06
forum: General Help
---

### Post by pianodreamer on 2009-01-06
I need to make some edits to my xorg.conf file, but whenever I open it I just get an empty file.

```
$ sudo gedit /etc/X11/xorg.conf
```

I tried searching for it to see if it got moved elsewhere, but all I was able to find was the empty file:

```
$ sudo find / -name xorg.conf
/etc/X11/xorg.conf
```


I'm not sure exactly whats going on. if I restart x, everything comes up fine. I'm thinking that it must have been renamed and moved, and I have no idea how I would go about searching for it. whats odd, is that I had been making edits to it earlier today.


I installed a command line system of ubuntu, then installed xorg, fluxbox, and SLiM seperately. gnome, kde, nor xfce were never installed.

---

### Post by morbid_bean on 2009-01-06
Try dong this see what happens:

```
sudo dpkg-reconfigure xserver-xorg 
```

---

