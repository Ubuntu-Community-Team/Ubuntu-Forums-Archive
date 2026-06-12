---
title: "GDM Presession script help"
date: 2008-12-16
forum: Desktop Environments
---

### Post by tossable001 on 2008-12-16
I'm building a number of kiosk stations for my school. The intent is to build a system with basic kiosk function, mainly home dir restoration on log-in. I'm having some trouble though, the scripts I'm using work fine when run from the terminal with sudo but bugger something up when run from the presession script.

This is the script I'm using to restore the student profile

```
#! /bin/sh
echo restoring user profile /home/student;
rm -fR /home/student ;
tar -xpPf /home/.default/clean_student.tar ;
```

The tarred image is created with

```
#! /bin/sh
echo backing up user profile /home/student ;
rm -f /home/.default/clean_student.tar ;
tar -cpPf /home/.default/clean_student.tar /home/student;
```

The results are the same when the script is added directly to Presession script 

```
...
#
PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

echo restoring user profile /home/student;
rm -fR /home/student ;
tar -xpPf /home/.default/clean_student.tar ;

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
...
```

or called as a script in it's own right. When calling the script I insert

```
...
#
PATH="/usr/bin/X11:/usr/X11R6/bin:/opt/X11R6/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

/usr/local/bin/restore_image.sh;

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
...
```


The following is .xsession-error resulting from the failed log-in attempt after adding the above restore script to /etc/gdm/Presession/Default .

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[19171]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
x-session-manager[19171]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:19399): WARNING **: Unable to add monitor: Not supported
x-session-manager[19171]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...

** (nm-applet:19443): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
  Message: 'Connection ":1.681" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'


(nm-applet:19443): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
starting HAL detection for ac adaptors...none found
evolution-alarm-notify-Message: Setting timeout for 8783 1229472000 1229463217
evolution-alarm-notify-Message:  Tue Dec 16 16:00:00 2008

evolution-alarm-notify-Message:  Tue Dec 16 13:33:37 2008

Throttle level is 0
system-config-printer-applet: failed to start NewPrinterNotification service
Connection failure: Connection refused

(gnome-keyring-daemon-wrapper:19318): EggSMClient-WARNING **: Received XSMP SaveYourself message in state save-yourself-done: client or server error
```

All of this is on a fully updated 8.10 system with gdm 2.20.8

Any idea's and or advice would be helpful.

Thank You

Gabriel

---

