---
title: "no GTK at all in KDE"
date: 2006-04-17
forum: Desktop Environments
---

### Post by niviche on 2006-04-17
Hello,

I've got a fresh Kubuntu Breezy install, updated to KDE 3.5.2, with all the repositories enabled.
For some reason, I can't access the "GTK Styles and Fonts" control window:

```

nicolas@ubuntu:~$ kcmshell kcmgtk
kcmshell (kdelibs): WARNING: Could not find module 'kcmgtk'.

```

But:

```

nicolas@ubuntu:~$ sudo apt-get install kcmgtk
E: Couldn't find package kcmgtk

```

Does anybody know where I can find this package, so that my GTK apps won't look so ugly on KDE?

---

### Post by niviche on 2006-04-17
I solved this, in seeing that the package had been renamed, but the link in the Control Settings had not.

To solve this:

```

sudo kate /usr/share/applications/kcmgtk-xdg.desktop
[code]

on line 4, replace

[code]
Exec=kcmshell kcmgtk

```

by

```

Exec=kcmshell kcmgtk-xdg

```

close and save. Now the link in the control setting should work.

---

