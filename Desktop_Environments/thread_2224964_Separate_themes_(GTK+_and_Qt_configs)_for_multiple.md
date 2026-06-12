---
title: "Separate themes (GTK+ and Qt configs) for multiple desktop environments"
date: 2014-05-19
forum: Desktop Environments
---

### Post by sorab on 2014-05-19
Obviously it is possible to install several desktop environments (Unity, KDE, Gnome, etc...) alongside with each other, then select which one you want to use for this session upon login.

However, I observed that the theme configurations will conflict with each other, especially the gtk-themes. E.g. gtk theme is set to Ambiance (which looks best under Unity), there will also be Ambiance under Gnome (which does not look too nice). If I switch the theme to, lets say Adwaita, under Gnome, also Unity will be adwaitared (which does not look nice neither).
This even affects KDE and [insert gnome-fork of your choice]. Qt applications will look like KDE unless you choose GTK+ in qtconfig, which however will also GTK-ize Qt application under KDE. Even worse: I observed that if I properly configure a KDE-desktop that has been installed on top of a vanilla Ubuntu 14.04 install, then KDE color setting will cause menues back under Unity to be black fonts on brown menue background (i.e. hardly readable).

I think different DE should keep their separate GTK and Qt configs. Apparently they don't ;(
I suppose a workaround could probably be done by writing some scripts that will upon login to a specific DE create symlinks to separate DE-specific GTK and Qt config files (but maybe the problem runs deeper?)
I am quite surprized that I cant find anything on this issue on the Internet.

The only easy (but dirty) solution I have is creating separate user accounts for each DE. Obviously this is not really satisfactory.

Does anyone know a solution to this?

Or if not: Say I might want to create the shellscripts myself, can anyone post a list of all config files I have to include in symlinking to achieve the full separation of GTK+ and Qt themes?

---

### Post by sorab on 2014-05-20
Nobody?

Can someone at least confirm to have the same problems?

---

### Post by Frogs Hair on 2014-05-20
This is an old on going problem . Many comprehensive 3rd party themes will include variants for different window managers such as XFCE , LXDE , and Open Box with the exception of QT. Running multiple desktops is a messy proposition mainly due to duplication of similar applications used in each desktop environment. KDE and Gnome have never played well together in terms of theming and there have been various work-arounds and  even some applications that haven't been maintained.  [http://askubuntu.com/questions/87037/gtk-in-kubuntu-apps-look-bad](http://askubuntu.com/questions/87037/gtk-in-kubuntu-apps-look-bad)

---

