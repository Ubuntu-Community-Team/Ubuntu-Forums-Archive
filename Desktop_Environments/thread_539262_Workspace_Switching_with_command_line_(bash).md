---
title: "Workspace Switching with command line (bash)"
date: 2007-08-31
forum: Desktop Environments
---

### Post by tobaccoman on 2007-08-31
Hi!

I have several terminal windows showing running processes and I normally move them onto anoher workspace (to the right for instance)

Is there a way to include this in a bash script?

I wouldlike to do it automatically when starting the application.

Thank you!

---

### Post by kidders on 2007-09-01
Hi there,

I'm not so sure if Gnome is easily able to do this sort of thing yet (I'm more of a KDE baby), but with KDE it's trivial. I don't know enough about other environments (eg Xfce) to comment one way or another, I'm afraid.

Kdesktop will let you switch desktops with a dcop call to "kdesktop -> KDesktopIface -> switchDesktops", but if you're not using it, that's no help.

---

### Post by 23meg on 2007-09-01
You can use *Devil's Pie* to position them in different workspaces, and *wmctrl* to perform various windowing operations in a script.

---

### Post by kidders on 2007-09-01
I second that suggestion. :-) If you need windows to open in particular places/ways, devilspie is really handy.

---

### Post by 23meg on 2007-09-01
I've moved this to the relevant support forum, since it doesn't pertain to Gutsy development.

---

