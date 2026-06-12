---
title: "Some users can't change appearance"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by skamarla on 2007-12-02
Hi, everybody:

I just installed ubuntu 7.10 from kubuntu 7.10 (by installing the ubuntu-desktop package). The computer has been through several test-installations of compiz, beryl, and the like. The graphics card is an Nvidia and I'm running the restricted module. Compiz runs just fine for all users.

My problem is that a few users (3 out of 5) can't change their desktop appearance.The "appearance preferences" windows pops up, but they can't change tabs; and if they click something in the tab (like the Add button in the Background tab), you just get a blank window. The system doesn't hang; you can close down the preferences window again; it's just impossible to change anything.

I'm pretty sure it's not a permissions problem. It's probably some old config file that these users have, but I don't know which. I have taken a look at the .xsession-errors file, and there is a difference:

Users that don't have the problem:

[FONT="Courier New"]Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/fix-linux:/tmp/.ICE-unix/5315
Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Initializing gnome-mount extension
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator[/FONT]

Users that do have the problem:

[FONT="Courier New"]Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/fix-linux:/tmp/.ICE-unix/14033
Checking for Xgl: Initializing gnome-mount extension
not present.
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier
Detected PCI ID for VGA: 02:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: /usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic
 color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier
present.
Checking for non power of two support: present.
Checking for Composite extension: present.
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier

** (nautilus:14097): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:14097): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:14097): WARNING **: Can not get _NET_WORKAREA

** (nautilus:14097): WARNING **: Can not determine workarea, guessing at layout
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier

(gtk-window-decorator:14260): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window !
= NULL' failed

(gtk-window-decorator:14260): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to
a drawable with depth 32

(gtk-window-decorator:14260): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window !
= NULL' failed

(gtk-window-decorator:14260): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to
a drawable with depth 32

(gtk-window-decorator:14260): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window !
= NULL' failed

(gtk-window-decorator:14260): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to
a drawable with depth 32
** Message: Not starting remote desktop server

** (update-notifier:14269): WARNING **: not starting because user is not in admin group

/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: invalid identifier `fg_color', expected val
id identifier
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: Invalid symbolic color 'fg_color'
...
...
(gtk-window-decorator:14260): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to
a drawable with depth 32

(gtk-window-decorator:14260): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window !
= NULL' failed

(gtk-window-decorator:14260): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to
a drawable with depth 32

(gtk-window-decorator:14260): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window !
= NULL' failed

... (repeated again and again)[/FONT]

Any ideas, or clues? Any help will be appreciated.

---

### Post by skamarla on 2007-12-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/138726](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/138726) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem was gtk-qt-engine. Removing it solved the problem. I still wonder why some users were not affected, though.

This is the [bug]("https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/138726") discussion

and the [thread]("http://ubuntuforums.org/showthread.php?t=519283") where I found it

---

