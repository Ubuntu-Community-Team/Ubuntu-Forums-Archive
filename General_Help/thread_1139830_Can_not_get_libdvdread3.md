---
title: "Can not get libdvdread3"
date: 2009-04-27
forum: General Help
---

### Post by yeehi on 2009-04-27
I would like to install libdvdread3 to help with encrypted DVDs. 
I try the following command but receive an error message. What can I do?

Jaunty Jackalope 64 alternate


> sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate

---

### Post by cwbar_1 on 2009-04-27
Go ahead and install the others.  Missing libdvdread3 had no effect on the performance of my install.  DVD play perfectly without it. (libdvdread3 is showing to not be available)

---

### Post by mc4man on 2009-04-27
That's because 9.04 uses libdvdread4

this takes care of vlc and libdvdcss2
```
sudo apt-get install libdvdread4 vlc && sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by yeehi on 2009-04-27
cool, mc4man!:guitar:

---

### Post by mc4man on 2009-04-27
IF the lack of the 'embedded' video in jaunty's vlc 0.9.9a is a problem then at the bottom of this post are 2 links for ppa's (one for 1.0 pre, the other for 0.9.9a with embedded enabled.

[http://ubuntuforums.org/showthread.php?p=7090561#post7090561](http://ubuntuforums.org/showthread.php?p=7090561#post7090561)

Totem-xine is also good to have for a second choice

```
sudo apt-get install totem-xine libxine1-ffmpeg
```

---

### Post by Slothbert on 2009-11-26
Thanks!!!

---

