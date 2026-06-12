---
title: "Uninstall X11 and XFCE"
date: 2007-09-18
forum: Desktop Environments
---

### Post by marco.giordano on 2007-09-18
Hi,
I started with a 7.04 Server installation, with no graphic interface at all. Then I installed XFCE (and therefore X11 too), but now I would like to rollback to a pure text shell installation.

How do I uninstall all XFCE AND X11 stuff?

Any help is appreciated

Marco

---

### Post by mojoman on 2007-09-18
Well, I'd probably try to boot up in console mode, fire up aptitude with
```

sudo aptitude
```
and then simply unistall everything under X11. That should, I think, do it but I've never done it myself so I can't be sure.

To remove xfce you could also do this

```
sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce gxine hal-cups-utils libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 mousepad mozilla-thunderbird orage python-cups python-exo scim-anthy scim-chewing scim-hangul scim-pinyin system-config-printer thunar thunar-archive-plugin thunar-doc thunar-media-tags-plugin thunar-volman-plugin vim-runtime xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```

It's from one of the adminstrators' _[sites]("http://www.psychocats.net/ubuntu/puregnome")_ and it's the 'remove xubuntu' tip (minus 'installing gnome'. Some of the stuff might not be installed but whatever you have installed with xfce is in that list (xfce comes as a metapackage so I think it can be a bother to remove it without knowing what it consists of). This doesn't remove x11 though.

hope it helps.

---

### Post by maybeway36 on 2007-09-18
Then try:
```
sudo apt-get autoremove
```

---

### Post by marco.giordano on 2007-09-19
Many thanks maybeway36 and mojoman!

I used apt-get for installing Xfce, but uninstalling worked even with aptitude.

Ciao

Marco

---

