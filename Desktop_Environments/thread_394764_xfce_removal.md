---
title: "xfce removal"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Weaseal on 2007-03-27
Hi all,

I installed the xubuntu-desktop package, and now I've decided I don't want it.  If I remove xubuntu-desktop, that will just remove the meta-package and not all the dependencies it installed, right?  If so, how do I remove all of its dependencies that are no longer needed?

Thanks.

---

### Post by sisco311 on 2007-03-27
```
sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce gxine libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgsf-gnome-1-114 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxcomposite1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 mousepad mozilla-thunderbird orage python-cups python-exo scim-anthy scim-chewing scim-hangul scim-pinyin system-config-printer thunar thunar-archive-plugin thunar-media-tags-plugin vim-runtime xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```

---

### Post by Weaseal on 2007-03-27
Multumesc! Cum ati gasit informatia aceasta?  Ma scuzati, nu vorbesc limba romana foarte bine ;)

That is assuming the fact that you reside in Romanian means that you speak the language too...

Incase you don't, what did you do to get that information?  I'd like to know so I can recreate that command myself later on.

---

### Post by sisco311 on 2007-03-27
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by Weaseal on 2007-03-28
I've given that page a shot, but every time I try to remove the packages, it wants to upgrade a bunch of random ones, and install some others!  What's going on??

---

