---
title: "cannot start gnome2"
date: 2010-06-28
forum: Desktop Environments
---

### Post by oradano on 2010-06-28
hi gurus,

I have a desktop install with 2 accounts.  When I startup the login screen (I'm assuming part of gnome) starts up and displays both users for login.  I can select one of them and login no problem, but with the other one it hangs and I have to restart.  I took a look at the home directory of this account and I see that file .xsession-errors is being touch'd, probably recreated, every time I try to login as this account.

One issue with this is that I normally connect wired, but the last week or so I've been travelling and have connected to more than one wireless network, probably not configured the same.

Below I've included some of the contents of .xsession-errors that got my attention.  Let me know and I can post the entire contents, basically this is the first warning / error recorded.
thanks in advance for any help with this, Dan
--------------------------------------------------------------------------------------------------------------------------

[B](polkit-gnome-authentication-agent-1:1880): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1880): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1878): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8d4be88'
** (nm-applet:1891): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1891): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug![/B]

---

