---
title: "Upgrade Ubuntu studio 7.04 to 7.10 with nvidia gnome hangs at startup"
date: 2007-10-30
forum: Desktop Environments
---

### Post by Belyel on 2007-10-30
I know that ubuntu studio may not be "officially" supported... but since it is basically just a bunch of metapackages on top of ubuntu vanilla, here's my question.
I had installed fresh Ubuntu studio 7.04, had done some upgrading and customization, but not a lot.  Install was a couple months old.  I had installed the nvidia drivers through envy.  I upgraded to 7.10.  In the process, it killed my wireless and hence upgrade was broken.  I reconnected with lan tonight, finished installing packages, reinstalled envy and my nvidia driver, etc.

When I start ubuntu, I get the ubuntu studio new login screen. Great.  When I log in, though, gnome haaaaaaaaaaaaangs then finally everything starts up normally...  It works fine after the ridiculously long hang, but who really wants to wait for 2-3 mins for their gui to load?

Here's the output from .xsession-errors:
> 
(process:13979): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:13983): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/pipeline-lx:/tmp/.ICE-unix/13976
Checking for Xgl: not present. 
Initializing gnome-mount extension
Initializing nautilus-image-converter extension
Detected PCI ID for VGA: 07:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2464x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: 
** (nautilus:14041): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:14041): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:14041): WARNING **: Can not get _NET_WORKAREA

** (nautilus:14041): WARNING **: Can not determine workarea, guessing at layout
present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/start_conky.sh: 1: !#: not found
** Message: Not starting remote desktop server

(gnome-panel:14035): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

the rest of it is conky errors.  I did remove conky from my startup list, but it did not improve performance.

---

