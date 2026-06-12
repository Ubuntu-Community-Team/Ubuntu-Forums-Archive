---
title: "KDE3 and KDE4 nightly neon together"
date: 2009-03-03
forum: Desktop Environments
---

### Post by zevans on 2009-03-03
From the "HowTo install KDE 3 into Intrepid (repost)" thread... 
[http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695)

> 
**Do you still want KDE 4?**

Add the following lines at the end of source.list
```

###Amarok2 & KDE4 Nightly Neon!!
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main

```
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install kde-nightly

```Reboot the machine. Now you can choose 3 WM at the login window:
    * KDE 3
    * KDE 4 (Nightly)
    * Gnome


So far so good - I've pulled the software down and installed, and I do seem to have a full set of binaries, configs, etc in the various kde4 subdirectories and under /opt/kde-nightly.

However when I choose the Nightly option in kdm greeter, it stops at the "could not start kstartupconfig4" that seems to be all over the Web. But I think I might know why this is.

THe kdm config file /etc/kde3/kdm/kdmrc tells kdm where to find all the other config files and so on, and it exclusively refers to kde3 stuff. So whilst kde4 might appear in the menu, all the path and so on will stay on kde3 entries.

So the question is, how do you make the kdm-kde3 or the kdm-kde4 change all the prefixes when you choose it from the menu, or alternatively can I run the kde3 greeter on :0 and the kde4 greeter on :1?

I thought I'd make this a separate thread because I'm sure there aren't many of us foolhardy enough to try and have retro-fitted KDE3 AND a nightly KDE4 on Intrepid, so I didn't want to distract madscientist too much...

---

