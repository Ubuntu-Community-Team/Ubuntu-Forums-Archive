---
title: "Removing some of all the bloat in gnome!"
date: 2009-02-03
forum: General Help
---

### Post by kbutcher5 on 2009-02-03
Well I was getting tired of all the bloat, and all the missing features in ubuntu off of a clean install, so on my latest install, I noted everything down.

It ended out in these three short command lines, to set the system up with a fully functional firefox, removing the bloat, and removing some of all of the "subpar" programs that comes bundled per default.
This also removes the segregated version of openoffice, which has been savagely beating into several bits and pieces.

Enjoy:
```

apt-get purge -y gnome-games openoffice.org-writer openoffice.org-impress openoffice.org-calc openoffice.org-draw evolution ekiga pidgin xsane f-spot totem-common
apt-get install -y ntp vim-full vlc audacious audacious-plugins audacious-plugins-extra flashplugin-nonfree sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java5-jre sun-java5-jdk sun-java5-plugin mplayer mozilla-mplayer
apt-get autoremove gnome-themes-extras gdm-themes gnome-humility-icon-theme

```

---

