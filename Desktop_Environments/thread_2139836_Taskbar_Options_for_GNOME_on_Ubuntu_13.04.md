---
title: "Taskbar Options for GNOME on Ubuntu 13.04"
date: 2013-04-28
forum: Desktop Environments
---

### Post by damien_d on 2013-04-28
Dear all,

I have just performed a clean install of Ubuntu 13.04, and installed gnome-shell.

What are my taskbar options for this version?  In 12.04 and 12.10, I have been happy with tint2, but it now longer appears to work,  It does not appear on the desktop and lists the following when manually run in a terminal:

```

damien@damien-desktop:~$ tint2 
real transparency on... depth: 32
xRandr: Found crtc's: 6
xRandr: Linking output DFP1 with crtc 0
xRandr: Linking output DFP5 with crtc 1
xRandr: Linking output DFP6 with crtc 2
tint2 : another systray is running pid=2932
tint2 : nb monitor 4, nb monitor used 4, nb desktop 2

^C
(process:4391): GLib-CRITICAL **: g_hash_table_foreach: assertion `version == hash_table->version' failed

```

For information pid=2932 is gnome-shell itself:

```

damien@damien-desktop:~$ ps aux | grep 2932
damien    2932  6.4  0.6 1677032 108188 ?      Sl   13:57   0:37 /usr/bin/gnome-shell
damien    4396  0.0  0.0  13632   916 pts/2    R+   14:07   0:00 grep --color=auto 2932

```

So, I am looking for another taskbar or, equally, a way of fixing tint2.  Are there any official shell extenstions for gnome that are useful?

  -- Damien

EDIT:

By the way, if it makes any difference, I am running AMD catalyst proprietary drivers (fglrd-updates) from the Ubuntu repositories:

```

damien@damien-desktop:~$ fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7700 Series 
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.01

```

---

### Post by Tux De Triana on 2013-04-28
Hi,

you can try Frippery bootom panel extension for gnome 3.6

[https://extensions.gnome.org/extension/3/bottom-panel/](https://extensions.gnome.org/extension/3/bottom-panel/)

Edit:

In gnome 3.8 exits a official extension "window list"

[https://extensions.gnome.org/extension/602/window-list/](https://extensions.gnome.org/extension/602/window-list/)

---

### Post by damien_d on 2013-04-28
> **Tux De Triana said:**
> 
you can try Frippery bootom panel extension for gnome 3.6

[https://extensions.gnome.org/extension/3/bottom-panel/](https://extensions.gnome.org/extension/3/bottom-panel/)


It ain't pretty but it works.... thanks!

  -- Damien

---

