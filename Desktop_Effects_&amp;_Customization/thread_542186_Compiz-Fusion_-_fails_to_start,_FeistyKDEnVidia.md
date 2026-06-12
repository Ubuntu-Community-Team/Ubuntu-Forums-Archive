---
title: "Compiz-Fusion - fails to start, Feisty/KDE/nVidia"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by UrbanSlayer on 2007-09-03
I've been trying to get compiz-fusion working for the past couple of days, but whatever I do, I can not get past this point - 

```

lain@eclair-ubuntu:~$ compiz --replace &
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking for nVidia: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

I have enabled AIGLX - 

```

lain@eclair-ubuntu:~$ grep AIGLX /var/log/Xorg.*.log
/var/log/Xorg.0.log:(**) Option "AIGLX" "True"

```

```

lain@eclair-ubuntu:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GS/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.11
OpenGL extensions:

```

I have made sure Compositing is enabled in the Xorg config, removed all other compiz packages and followed this howto - [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

Killing kwin before running compiz  --replace doesnt help either.  At the moment, I am at a loss and do not know where to proceed.

Can anyone help?  Many thanks.

---

### Post by UrbanSlayer on 2007-09-04
As an update, I have tried it with Gnome, and it works fine, so I'm guessing this is a KDE problem.

Can anyone help?

---

### Post by UrbanSlayer on 2007-09-04
Ok, solved, looks like it doesnt like it if you disable desktop icons in KDE.  A bit odd, but nevermind!

---

### Post by dLux on 2008-01-04
> **UrbanSlayer said:**
> Ok, solved, looks like it doesnt like it if you disable desktop icons in KDE.  A bit odd, but nevermind!

the importance of these findings should not be overlooked!

i was happily going about my business on my fresh fedora 8 x86_64 install w/ kde, full of joy that nvidia aiglx accelerated compiz-fusion was all setup and working, and after a reboot compiz would not start! it was throwing errors described above, slightly different in fedora terms but these bits indicated the same error:

Error: Another window manager is already running on screen: 0
Fatal: No manageable screens found on display :0.0

i remembed i had turned my desktop icons off and sure enuff re-enabling them and rebooting again let compiz start it's window manager sucessfuly.

this seemed a familiar error with all what i've recently been thru with xorg.conf edits n whatnot, but in the end completely unrelated (afaik).

thx u google, UrbanSlayer, Ubuntu Forums =D

---

