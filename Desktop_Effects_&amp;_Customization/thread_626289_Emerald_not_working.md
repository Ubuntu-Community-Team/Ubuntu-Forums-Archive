---
title: "Emerald not working"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by radioactivity on 2007-11-28
Tried my best to get emerald to run with compiz, but failed.
Checked around the forums but found nothing, been googling for a while aswell.

I have an ATI graphics card and have got the restricted driver installed.
Compiz works with the gtk-window-decorator, but if I try anything else the title bars disappear.

I ended up removing all compiz/emerald/beryl packages and reinstalling (when i install emerald it automatically downloads beryl, is that normal?) and reinstalling, and now I've lost CCSM, which is annoying.

I tried using emerald --replace in terminal to see what it returned and it was this line over and over

(emerald:9540): Wnck-WARNING **: Unhandled action type (nil)

anyone know what that means?

Someone help, I just want to use emerald themes :(

---

### Post by radioactivity on 2007-11-28
well, got it working
ran this script [http://forum.compiz-fusion.org/showthread.php?t=5019](http://forum.compiz-fusion.org/showthread.php?t=5019) which said it would install, but it didn't fully install (not sure what went wrong). So I then installed from the synaptic package manager, and emerald was working.

Though I still can't get CCSM to run.

when i type ccsm into terminal this is what i get

Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

---

### Post by PatrickFisher on 2007-11-29
> **radioactivity said:**
> well, got it working
ran this script [http://forum.compiz-fusion.org/showthread.php?t=5019](http://forum.compiz-fusion.org/showthread.php?t=5019) which said it would install, but it didn't fully install (not sure what went wrong). So I then installed from the synaptic package manager, and emerald was working.

Though I still can't get CCSM to run.

when i type ccsm into terminal this is what i get

Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in <module>
    import compizconfig
ImportError: No module named compizconfig

Try this:

```
 sudo apt-get install compizconfig-settings-manager

```

---

### Post by radioactivity on 2007-11-29
tried it a couple of times.
keep getting this, but I don't know why it can't find it.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compizconfig-settings-manager has no installation candidate

---

### Post by PatrickFisher on 2007-11-29
> **radioactivity said:**
> tried it a couple of times.
keep getting this, but I don't know why it can't find it.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package compizconfig-settings-manager has no installation candidate

Make sure the universe is enabled. If it still doesn't work, try the multiverse.

---

### Post by radioactivity on 2007-11-29
they both seem to be enabled,

I added 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

to my source.list file then ran it again, downloaded this time and installed fine, thought I'm on gutsy, so I dunno where it was.

---

### Post by PatrickFisher on 2007-11-29
> **radioactivity said:**
> they both seem to be enabled,

I added 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

to my source.list file then ran it again, downloaded this time and installed fine, thought I'm on gutsy, so I dunno where it was.


Weird. Well, I'm glad it worked.

---

### Post by 5735guy on 2008-01-03
emerald --replace worked great for me:):)

---

