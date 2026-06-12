---
title: "Hoary auto update not working"
date: 2005-04-30
forum: Desktop Environments
---

### Post by joplass on 2005-04-30
I am having a lot of troubles automatically updating Hoary.  When I click apply I get this error:

It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.
The following packages are not update:

libavcodeccvs
libpostproc0
libxvidcore4

Of course I tried Synaptic and the terminal.  No can do!  Meanwhile I don't know if this is the right place for this post.

---

### Post by defkewl on 2005-04-30
Try adding more repo

---

### Post by joplass on 2005-05-01
[QUOTE=defkewl]Try adding more repo[/QUOTE]
Which one for example.  I don't know any other repo besides the ones included in the guide.

---

### Post by Leif on 2005-05-01
I'm getting this too (for gstreamer0.8-faad libpostproc0 libxvidcore4 mplayer-386), but I wasn't too worried about it. I've got marillat and backports.

---

