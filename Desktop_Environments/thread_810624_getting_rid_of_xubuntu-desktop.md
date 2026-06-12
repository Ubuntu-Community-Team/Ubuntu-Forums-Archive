---
title: "getting rid of xubuntu-desktop"
date: 2008-05-28
forum: Desktop Environments
---

### Post by kman16 on 2008-05-28
hey.

I have a Thinkpad R50e running Ubuntu8.04.
I wanted to try out some alternatives to GNOME so I installed xubuntu-desktop to see how XFCE is. It wasn't such a difference so I removed it.

The problem is that I still have XFCE on my machine, xubuntu login screen and some programs from the xubuntu installation.

does anybody knows how to remove it completely? and also what went wrong (so I could learn...). thanks.

---

### Post by aysiu on 2008-05-28
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) should help.

---

### Post by kman16 on 2008-05-28
thanks man, that was quick.
there is still something I don't get.

```
sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

what does "&&" stand for? can i run this in the terminal at once? or should I run first the remove <tons of programs>  and then the install ubuntu-desktop?

---

### Post by aysiu on 2008-05-28
Yes, you can run the whole command at once. Just paste it right in.

*&&* means *After you've finished running the command before this, run the command after this*.

So first you're removing completely all the Xfce components. Then you're making sure you have all the proper Gnome components installed.

---

