---
title: "Safely removing Beryl"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Flaringo on 2006-10-07
I want to remove Beryl without having to format the whole drive. I followed [this](http://forum.beryl-project.org/topic-4861-howto-install-beryl-dapper-nvidia-using) guide when I was installing it, but now I want to remove it as safely as possible, so everything is like it was when I had the normal GDM.

So how do I remove Beryl as safely as possible?

---

### Post by Fass on 2006-10-07
First remove the changes you made to your /etc/gdm/gdm.conf-custom, go into System &#8211;> Preferences &#8211;> Sessions &#8211;> Startup Programs and remove xmodmap /usr/share/xmodmap/xmodmap.us and beryl-manager, then run ```
sudo aptitude remove xserver-xgl beryl beryl-manager beryl-core beryl-dev beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes
``` You can add --purge to that if you want to remove all the config files of those packages as well. Also, if you no longer want them, remove the beryl repos from your /etc/apt/sources.list.

In the future, I recommend that you not use "apt-get" when installing packages, but "aptitude" instead. It keeps better track of dependencies when packages are to be removed.

---

### Post by Flaringo on 2006-10-07
Thank you very much for your help! :)

---

### Post by marx2k on 2006-11-14
Id like to know if this has actually worked or if problems were encountered with this?

Im about to remove Beryl too but Id like to know if there are other config files that need to be changed?

---

