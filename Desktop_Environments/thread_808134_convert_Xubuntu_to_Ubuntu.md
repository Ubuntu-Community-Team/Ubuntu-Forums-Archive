---
title: "convert Xubuntu to Ubuntu"
date: 2008-05-26
forum: Desktop Environments
---

### Post by akahige on 2008-05-26
I've been running Xubuntu (Hardy) which was upgraded from multiple previous versions (the original or which was a clean Ubuntu install). XFCE has been temperamental since the Hardy upgrade, so I think I want to go back and try Gnome again.

I've been reading on how to do this, but I'm not sure what I need to do this safely...

[Psychocats](http://www.psychocats.net/ubuntu/purexfce) has a bunch of good info, but a lot of it is prefaced by "if you originally did X..." and it's been so long since I've messed with the system config that I honestly don't know what was done in the first place.

Is there a way to determine if aptitude was used to install XFCE in the first place, or should I just use this code ([from Psychocats](http://www.psychocats.net/ubuntu/puregnome)):
```
sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

Or should I even be worried about this...?

---

### Post by revolutio on 2008-05-26
I made the switch from Xubuntu to Ubuntu (same reason) and I think the command I used was this:

```
sudo apt-get remove xubuntu-desktop && sudo apt-get install ubuntu-desktop
```

After that I had to run do sudo apt-get autoremove, manually remove some redundant programs, reinstall ATI drivers, and tweak GRUB.  It wasn't as bad as I thought it was going to be going in.  Good luck.

---

### Post by MyR on 2008-05-26
that command from psychocats will work fine, unless you want to keep using some of the things it uninstalls like abiword (which is much faster), or thunderbird.

peace

---

