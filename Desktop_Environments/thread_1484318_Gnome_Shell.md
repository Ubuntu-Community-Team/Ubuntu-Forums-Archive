---
title: "Gnome Shell"
date: 2010-05-15
forum: Desktop Environments
---

### Post by mmesantos1 on 2010-05-15
Hello,
I have installed gnome-shell from PPA and ran the command gnome-shell -replace and I am unable to get gnome shell to run. Any helpw ould be appreciated. 

I am running Ubuntu 10.04 and I have disabled compiz. I have installed all updates available for 10.04 final. 

The error I get when I try to run gnome shell: 

ems@ems-desktop:~$ gnome-shell -replace
Usage: gnome-shell [options]

gnome-shell: error: no such option: -e

---

### Post by psychokilla on 2010-05-15
The Gnome website suggests running gnome-shell --replace (which you can either do in Terminal or by pressing Alt+F2) however I find that it is generally quite buggy so I suggest setting it as the default window manager. To do this press Alt+F2 and enter:

> gconf-editor

And navigate to /desktop/gnome/session/required_components and change windowmanager to gnome-shell. Make note of what it was originally in case you want to set it back. Restart Ubuntu and Gnome Shell should appear.

---

### Post by mmesantos1 on 2010-05-15
Thank you, works great.

---

