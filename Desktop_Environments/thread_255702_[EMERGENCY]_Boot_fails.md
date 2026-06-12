---
title: "[EMERGENCY] Boot fails???"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Cris987 on 2006-09-11
I've been trying to make a pure KDE by executing the following command: 
```
sudo aptitude remove abiword abiword-common abiword-help abiword-plugins anthy dbus-1-utils desktop-file-utils evince-gtk firefox gaim gaim-data gconf2 gconf2-common gdebi gdm gimp gimp-data gimp-print gksu gnome-icon-theme gnome-keyring gnome-mime-data gnumeric-common gnumeric-gtk gqview gtk2-engines-clearlooks gtk2-engines-industrial gtk2-engines-mist gtk2-engines-smooth gtk2-engines-ubuntulooks gtk2-engines-xfce im-switch language-selector latex-xft-fonts launchpad-integration libaa1 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libatk1.0-0 libavahi-glib1 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libchewing-data libchewing2 libcroco3 libdjvulibre15 libenchant1c2a libexo-0.3-0 libgconf2-4 libgdome2-0 libgdome2-cpp-smart0c2a libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglib-perl libglib2.0-data libgnome-keyring0 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoffice-1-common libgoffice-gtk-1-2 libgsf-1-113 libgsf-1-common libgsf-gnome-1-113 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmathview0c2a libgtkspell0 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 libots0 libpango1.0-0 libpango1.0-common libpoppler1-glib librpm4 librsvg2-2 librsvg2-common libt1-5 libtagc0 libthunar-vfs-1 libvte-common libvte4 libwmf0.2-7 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 mousepad mozilla-thunderbird orage python-glade2 python-gnome2 python-gtk2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gobject python2.4-gtk2 rpm scim scim-anthy scim-chewing scim-gtk2-immodule scim-hangul scim-modules-socket scim-pinyin shared-mime-info synaptic system-tools-backends tango-icon-theme tango-icon-theme-common thunar thunar-media-tags-plugin ttf-arphic-ukai ubuntu-artwork ubuntu-sounds unattended-upgrades update-manager xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4 xfwm4 xfwm4-themes xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-system-tools zenity
```

Somehow, someway, I seemed to have removed something I should not have removed. When I rebooted, a black screen appears with a flashing underscore. I tried some commands but it would not respond. Ctrl-Alt-backspace failed and ctrl-alt-del restarted the computer. 

Can someone PLEAAAASSEEE help? ](*,)

---

### Post by Cris987 on 2006-09-11
Please help! :(

---

### Post by Najand on 2006-09-12
Hmm, strange  way  of installing KDE. Anyway, why don't you press ALT+Ctrl+F1 to start a text base session, login and then execute the following command:
```

sudo apt-get install kubuntu-desktop

```

---

### Post by Iarwain ben-adar on 2006-09-12
Hi,
@ Najand: i think he wanted a pure (read: only the DE) KDE.

Chris: can you try this: sudo aptitude install kdm kde-core kdelibs

EDIT:
[try this](http://www.ubuntuforums.org/showthread.php?t=169383),
it's someone who tried it aswell, maybe you can find something there


Iarwain

---

