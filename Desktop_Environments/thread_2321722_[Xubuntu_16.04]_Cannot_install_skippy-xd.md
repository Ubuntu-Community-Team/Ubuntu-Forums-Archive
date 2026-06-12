---
title: "[Xubuntu 16.04] Cannot install skippy-xd"
date: 2016-04-24
forum: Desktop Environments
---

### Post by kevin_tee on 2016-04-24
When I run the code

sudo add-apt-repository ppa:landronimirc/skippy-xd-daily

sudo apt-get update

sudo apt-get install skippy-xd

It says that there are no such package. How do I install skippy? Thanks

---

### Post by slickymaster on 2016-04-24
> **kevin_tee said:**
> When I run the code

sudo add-apt-repository ppa:landronimirc/skippy-xd-daily

sudo apt-get update

sudo apt-get install skippy-xd

It says that there are no such package. How do I install skippy? Thanks

Hi kevin_tee, welcome to the forums.

The last supported version for skippy-xd, by Xubuntu, is Trusty. The Xubuntu team has it in their Xubuntu Extras PPA, here: [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras)

Since the packages in that PPA are considered for inclusion in the Ubuntu repositories and/or Xubuntu at a later time can't say how long it will be there.

---

### Post by kevin_tee on 2016-04-24
> **slickymaster said:**
> Hi kevin_tee, welcome to the forums.

The last supported version for skippy-xd, by Xubuntu, is Trusty. The Xubuntu team has it in their Xubuntu Extras PPA, here: [https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras](https://launchpad.net/~xubuntu-dev/+archive/ubuntu/extras)

Since the packages in that PPA are considered for inclusion in the Ubuntu repositories and/or Xubuntu at a later time can't say how long it will be there.

Thanks you. I manage to install it. However...

Terminal

1 skippy-xd

2 WARNING: Couldn't load config file '/home/xubuntu/.config/skippy-xd/skippy-xd.rc'.
  running once then quitting...

3 *download skippy-xd.rc and put in the folder*

4 skippy-xd

5 running once then quitting...

What is wrong? Running once and quitting?

---

### Post by kevin_tee on 2016-04-24
OK, lets just for get skippy-xd I can install it but it won't run, it is also quite old. I simply want expo function that you can find in compiz but I don't want to install compiz just for the expo. Are there alternative?

---

### Post by slickymaster on 2016-04-26
> **kevin_tee said:**
> OK, lets just for get skippy-xd I can install it but it won't run, it is also quite old. I simply want expo function that you can find in compiz but I don't want to install compiz just for the expo. Are there alternative?

See if this thread can somehow provide you with any help: [http://ubuntuforums.org/archive/index.php/t-2098019.html](http://ubuntuforums.org/archive/index.php/t-2098019.html)

---

### Post by vasa1 on 2016-04-26
Given that skippy-xd hasn't been made available for 16.04 even as a ppa, there doesn't seem to be a way to spread windows other than by using Compiz unless the KDE guys have something but even that won't be light-weight if that's a pre-requisite.

I probably am off the track here, but there's something called PyTile.py. It's supposed to provide a Compiz Grid effect: [http://askubuntu.com/questions/15198/is-there-a-way-to-make-openbox-behave-like-the-compiz-grid-plugin](http://askubuntu.com/questions/15198/is-there-a-way-to-make-openbox-behave-like-the-compiz-grid-plugin)

It doesn't work for me:```
04:27 PM ~ $ /home/vasa1/bin/PyTile.py
Traceback (most recent call last):
  File "/home/vasa1/bin/PyTile.py", line 2, in <module>
    import os, subprocess, gtk, pygtk, sys, time, threading,wnck
ImportError: No module named wnck
04:32 PM ~ $ 
```And because I know nothing about Python, I don't know what to fix assuming that PyTile.py could provide a semblance of what OP wants.

---

