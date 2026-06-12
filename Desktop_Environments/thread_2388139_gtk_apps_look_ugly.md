---
title: "gtk apps look ugly"
date: 2018-03-29
forum: Desktop Environments
---

### Post by manmath on 2018-03-29
Hi, all the gtk apps (such as bleachbit, artha, synaptic) look really ugly. Please have a look at the attached screenshot. Suggest me what I'm missing or what I can do so that all the apps look consistent. Here's the list of packs related to theme that's installed on my system:

```
manmath@manmath-H61M-DS2:~$ dpkg -l | grep theme
ii  adium-theme-ubuntu                    0.3.4-0ubuntu4                      all          Adium message style for Ubuntu
ii  adwaita-icon-theme                    3.27.90-1ubuntu1                    all          default icon theme of GNOME (small subset)
ii  darkcold-gtk-theme                    1.0-2                               all          dark GTK2/GTK3/Metacity theme
ii  dmz-cursor-theme                      0.4.5ubuntu1                        all          Style neutral, scalable cursor theme
ii  gtk-update-icon-cache                 3.22.29-2ubuntu1                    amd64        icon theme caching utility
ii  gtk2-engines-murrine:amd64            0.98.2-2ubuntu1                     amd64        cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf:amd64             2.24.32-1ubuntu1                    amd64        pixbuf-based theme for GTK+ 2.x
ii  hicolor-icon-theme                    0.17-2                              all          default fallback theme for FreeDesktop.org icon themes
ii  humanity-icon-theme                   0.6.15                              all          Humanity Icon theme
ii  light-themes                          16.10+18.04.20180322.4-0ubuntu1     all          Light Themes (Ambiance and Radiance)
ii  plymouth-theme-ubuntu-logo            0.9.3-1ubuntu2                      amd64        boot animation, logger and I/O multiplexer - ubuntu theme
ii  sound-theme-freedesktop               0.8-2ubuntu1                        all          freedesktop.org sound theme
ii  ubuntu-artwork                        1:16.10+18.04.20180322.4-0ubuntu1   all          Ubuntu themes and artwork
ii  ubuntu-mono                           16.10+18.04.20180322.4-0ubuntu1     all          Ubuntu Mono Icon theme
ii  ubuntu-sounds                         0.13                                all          Ubuntu's GNOME audio theme
```

[ATTACH=CONFIG]279121[/ATTACH]

---

### Post by flocculant on 2018-03-29
try qt5-style-plugin

---

### Post by manmath on 2018-03-30
Solved. Actually there was some problem with gnome-settings-daemon. I reinstalled all the gnome bits and now everything looks elegant.

---

