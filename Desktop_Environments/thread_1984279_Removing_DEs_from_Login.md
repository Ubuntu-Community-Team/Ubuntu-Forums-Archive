---
title: "Removing DEs from Login"
date: 2012-05-21
forum: Desktop Environments
---

### Post by meijin3 on 2012-05-21
Hi there everyone, this is my inaugural post here on Ubuntu forums and I am certain it won't be my last.

I am a fairly new user of Ubuntu (~2 weeks) and have experimented with a couple desktop environments, namely Gnome 3 and Xfce. I much preferred the Unity interface over the other two and would now like to completely remove them. I've uninstalled them but there are still lingering effects of their installation including:
-the option to select them at login
-a very noticable slow down in login time
-Xubuntu shut down and boot up animation as opposed to an Ubuntu one

If anyone could walk me through their complete and thorough uninstallation, I would much appreciate it. Thanks! :D

---

### Post by wilee-nilee on 2012-05-21
Take a look at this link in the playing around section, there are full removal lists for DE, if you have poked at them already you may or may not have problems, read carefully.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by flemur13013 on 2012-05-21
To completely delete them, you might need to re-install and then remove them with a "purge" rather than just "remove".  You can see which files they use with:
   synaptic/select-package/rt-click: properties

Although this isn't uninstalling, I'm pretty sure they're defined by the .desktop files in /usr/share/xsessions:

$ ls /usr/share/xsessions  
cinnamon.desktop  fluxbox.desktop  gnome-classic.desktop  gnome.desktop  gnome-fallback.desktop  gnome-shell.desktop  ubuntu-2d.desktop  ubuntu.desktop

Try renaming/deleting one you don't want and see if it's gone from the login screen.

---

### Post by wilee-nilee on 2012-05-21
> **flemur13013 said:**
> To completely delete them, you might need to re-install and then remove them with a "purge" rather than just "remove".  You can see which files they use with:
   synaptic/select-package/rt-click: properties

Although this isn't uninstalling, I'm pretty sure they're defined by the .desktop files in /usr/share/xsessions:

$ ls /usr/share/xsessions  
cinnamon.desktop  fluxbox.desktop  gnome-classic.desktop  gnome.desktop  gnome-fallback.desktop  gnome-shell.desktop  ubuntu-2d.desktop  ubuntu.desktop

Try renaming/deleting one you don't want and see if it's gone from the login screen.

Not quite right you can do a dpkg search and find every package and where they are, a purge will only remove a few packages.

dpkg -L <package> for where all the package is
To find which package a particular file belongs to you can do:
dpkg -S <filename>

Easiest though to have a full list as on the psychocats website at the least run it and see if it clears out the whole DE.

---

### Post by meijin3 on 2012-05-21
Thanks everyone for all the responses! I'm now happily able to log in without being bothered :)

---

