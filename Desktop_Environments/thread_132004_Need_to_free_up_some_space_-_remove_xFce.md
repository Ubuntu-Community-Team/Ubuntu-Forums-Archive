---
title: "Need to free up some space - remove xFce"
date: 2006-02-17
forum: Desktop Environments
---

### Post by alfonz on 2006-02-17
Alright, I'm running out of space here and untill I get a second HD in here I'll have to deal with what I got. I installed xubuntu-desktop because I wanted to try out xFce, however Gnome is my primary Desktop and I would like to remove xFce.

I tired ```
sudo apt-get remove xubuntu-desktop
``` but that didn't do anything. I am at a loss of ideas

Can anyone point to the right direction to get rid of xfce for now and use only gnome for the time being?

Thanks in advance

Cheers!

---

### Post by kaamos on 2006-02-17
xubuntu-desktop is only a metapackage that pulls down the actual packages. Look here: [http://ubuntuforums.org/showthread.php?t=129517](http://ubuntuforums.org/showthread.php?t=129517)

---

### Post by bored2k on 2006-02-17
Install deborphan. Then, go to synaptic and set up a filter that shows ONLY orphan packages. It'll show you the packages that the system "thinks" that are orphans or in other words, not used or required by any other package. XFCE libraries should be there.

---

