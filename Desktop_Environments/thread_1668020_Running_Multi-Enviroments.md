---
title: "Running Multi-Enviroments"
date: 2011-01-15
forum: Desktop Environments
---

### Post by lekidos on 2011-01-15
Hi everyone, almost new Ubuntu user here, returning from a big gap in use, from 8.04. Was a newbie then, and only slightly less of a newbie now. 

Just a small question- Is there any harm with installing the three desktop enviroments- GNOME/Ubuntu, KDE/Kubuntu, and XFCE/Xubuntu on the same machine?

I wanted to try them all out, and installed each with the sudo apt-get install name-desktop   command, on top of my ubuntu netbook edition (which is actually on my desktop).

I noticed some of them, for example, I did XFCE last, and it was removing packages as well as adding new ones. 

Can that be a problem sometime later?
I mean, I guess it all depends on which one I'll end up keeping but what if I want to keep them all?
Or would it just be better to do a separate OS/partition install for, say, Xubuntu/etc

Thanks

---

### Post by r.stiltskin on 2011-01-15
No problem having them side by side.  You just choose which one you want to use when you log in.

Obviously I don't know what apt was removing but it wouldn't remove anything that would break your system.  You can take a look in /var/log/apt/history.log to see what was installed and uninstalled.

---

### Post by lekidos on 2011-01-15
Thanks!

For some reason it removed pulseaudio, which explains the sound issues I was having afterwards (which I "fixed" by re-installing the ubuntu-desktop), which prompted me to make this post in the first place.

Thanks again!

---

