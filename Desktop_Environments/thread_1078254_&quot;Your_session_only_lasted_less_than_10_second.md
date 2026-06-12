---
title: "&quot;Your session only lasted less than 10 seconds&quot;"
date: 2009-02-23
forum: Desktop Environments
---

### Post by d4nnyt on 2009-02-23
Hi

Not sure if I got this in the right forum or not. Sorry if I haven't.

When I started up my computer and logged in this morning the session failed and put me back to the log in screen. When I log back in I get the message;

> Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

Clicking 'OK' takes me back to the log in screen. I can run programs still if I do not click 'OK'.

When this happened compiz didn't load on startup but I was able to start it by Alt+F2 "compiz --replace", which allowed me to open firefox and still see the window.

Content of .xsession-errors
> 
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 29: [[: not found
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-OHmCXJ9996/agent.9996
Checking for Xgl: not present. 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Checking for Xgl: present. 
Checking for non power of two support: not present. 
present. 
Checking for Composite extension: present. 
Checking for Xgl: not present. 

** (nm-applet:10175): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10175): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (update-notifier:10147): WARNING **: already running?


** (update-notifier:10181): WARNING **: already running?

Detected PCI ID for VGA: 
Checking for texture_from_pixmap: 
** (update-notifier:10218): WARNING **: already running?

present. 
Checking for non power of two support: 
** (nm-applet:10213): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10213): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
present. 
Checking for Composite extension: Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for Xgl: present. 
Checking for Composite extension: present. 
not present. 
present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Checking for Xgl: Not present. 
Checking for nVidia: not present. 
present. 
Checking for Xgl: present. 
Checking for FBConfig: not present. 

** (update-notifier:10350): WARNING **: already running?

present. 
Checking for Xgl: Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Detected PCI ID for VGA: 
Checking for texture_from_pixmap: 
** (nm-applet:10373): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:10373): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Not present. 
Checking for nVidia: present. 
Checking for non power of two support: present. 
Checking for FBConfig: present. 
Checking for Composite extension: present. 
Checking for Xgl: not present. 
present. 

** (update-notifier:10375): WARNING **: already running?

not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: 
(xfce4-panel:10082): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:10082): libxfcegui4-WARNING **: Disconnected from session manager.
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: IO error occured doing Protocol Setup on connection

(xfdesktop:10076): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:10076): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault


Thanks for Looking

---

