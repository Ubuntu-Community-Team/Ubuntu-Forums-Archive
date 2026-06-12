---
title: "Updated and Unity no Longer Loads"
date: 2013-06-21
forum: Desktop Environments
---

### Post by Kodeine on 2013-06-21
So yesterday just before turning the computer off for the night update manager popped up requesting to update some packages. I did so but from what I remember (goldfish memory) the desktop just froze. I was unable to switch to a different tty to issue a shutdown command. So I was forced to 'force shutdown'. Upon booting the computer the window manager loads so I can close, minimise and maximise windows but unity does not. I tried to bring unity back to life via

dconf reset -f /org/compiz/
setsid unity

Which resets it's configuration but it appears not to be a problem with that. I've tried running unity via terminal and after loading the different plugins and saying something like 'unity-panel-service: no process found' it just froze again (been getting lots of error reports concerning unity-panel-service before this). Unable to switch tty I had to once again force shutdown. I've ran synaptic and there's no complaining of broken packages or more updates so I presume update manager installed them correctly.

What might be causing unity's woes?

**I've just noticed in ccsm that the unity plugin is unchecked? Ticking it removes the window borders and doesn't bring unity back.
***I cannot logout to see if any other environmental loads due to an bug. Which at some stage I need to report.

---

### Post by TheFu on 2013-06-21
Sounds like your patching failed mid-stream. Have you tried to finish that process?

From a terminal, 
* sudo apt-get update
* sudo apt-get dist-upgrade
that should get all the packages current and - more importantly - if there are any issues, you can copy/paste them here for more help.

Don't fear "dist-upgrade" - it just installs new kernels from the Ubuntu repos for your specific distro - IT WILL NEVER UPGRADE from 1 distro to another.

---

### Post by Kodeine on 2013-06-21
I've just done dist-upgrade but it says there was zero packages updated/installed.

In update managers log it appears everything went okay. I note that we updated some gnome packages. Perhaps there's defect?
```
(Reading database ... 217883 files and directories currently installed.)Preparing to replace gnome-desktop3-data 3.8.1-0ubuntu1~raring1 (using .../gnome-desktop3-data_3.8.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-desktop3-data ...
Preparing to replace libgnome-desktop-3-7 3.8.1-0ubuntu1~raring1 (using .../libgnome-desktop-3-7_3.8.2-0ubuntu1~raring1_i386.deb) ...
Unpacking replacement libgnome-desktop-3-7 ...
Preparing to replace gir1.2-gnomedesktop-3.0 3.8.1-0ubuntu1~raring1 (using .../gir1.2-gnomedesktop-3.0_3.8.2-0ubuntu1~raring1_i386.deb) ...
Unpacking replacement gir1.2-gnomedesktop-3.0 ...
Preparing to replace gnome-icon-theme 3.7.3+git20121224.2af6b37d-0ubuntu1~13.04~ricotz0 (using .../gnome-icon-theme_3.8.2-0ubuntu1~ubuntu13.04.1_all.deb) ...
Unpacking replacement gnome-icon-theme ...
Preparing to replace gnome-icon-theme-symbolic 3.7.4.1+git20130201.0beb4ffd-0ubuntu1~13.04~ricotz0 (using .../gnome-icon-theme-symbolic_3.8.2.2-0ubuntu1~raring1_all.deb) ...
Unpacking replacement gnome-icon-theme-symbolic ...
Preparing to replace gnome-shell-common 3.9.2+git20130530.63e6d118-0ubuntu1~13.04~ricotz0 (using .../gnome-shell-common_3.9.2+git20130601.bd6e0ceb-0ubuntu1~13.04~ricotz0_all.deb) ...
Unpacking replacement gnome-shell-common ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Setting up gnome-desktop3-data (3.8.2-0ubuntu1~raring1) ...
Setting up libgnome-desktop-3-7 (3.8.2-0ubuntu1~raring1) ...
Setting up gir1.2-gnomedesktop-3.0 (3.8.2-0ubuntu1~raring1) ...
Setting up gnome-icon-theme (3.8.2-0ubuntu1~ubuntu13.04.1) ...
Setting up gnome-icon-theme-symbolic (3.8.2.2-0ubuntu1~raring1) ...
Setting up gnome-shell-common (3.9.2+git20130601.bd6e0ceb-0ubuntu1~13.04~ricotz0) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2013-06-02  12:06:50
```

---

### Post by TheFu on 2013-06-21
well, it appears that something was mid-install, otherwise the triggers and setting up {X, y, z} wouldn't happen.
If you reboot, is all well again?

---

### Post by Kodeine on 2013-06-21
I've rebooted several times but to no avail.

---

### Post by TheFu on 2013-06-21
> **Kodeine said:**
> I've rebooted several times but to no avail.

What do the logs show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

What does the boot log show?

Any issues?

Does any other DE work instead of Unity? XFCE? LXDE? any pure window manager?  There is probably a window manager installed already, but you'll need to spend the 60 seconds to install LXDE or XFCE yourself.

It could be a GPU driver issue too - perhaps forcing a reinstall would fix it?

Sorry - I'm shooting blind without log data.

---

### Post by Kodeine on 2013-06-21
I've just tried re-installing the AMD 13.4 blob driver but nothing has changed. With regards to changing the DE I've always had an issue with my new machine where I cannot log out. Doing so results in a console like screen where I can type anything in but it won't do anything. This is accompanied by screen tearing. I am able to switch the tty and issue a shutdown command at that point. Is it possible to start a different DE without logging out?

Here's the boot log```
fsck from util-linux 2.20.120GB_PsyDuck: clean, 228393/1221600 files, 1475458/4883448 blocks
 * Starting mDNS/DNS-SD daemon[154G[ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[154G[ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[154G[[31mfail[39;49m]
 * Starting network connection manager[154G[ OK ]
 * Stopping userspace bootsplash[154G[ OK ]
 * Stopping Flush boot log to disk[154G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [160G 
[154G[ OK ]
 * Setting sensors limits       [160G 
[154G[ OK ]
 * Stopping System V initialisation compatibility[154G[ OK ]
 * Starting System V runlevel compatibility[154G[ OK ]
 * Starting [154G[ OK ]
 * Starting [154G[ OK ]
 * Starting cups-browsed - Bonjour remote printer browsing daemon[154G[ OK ]
 * Starting [154G[ OK ]
 * Starting [154G[ OK ]
 * Starting save kernel messages[154G[ OK ]
 * Starting [154G[ OK ]
 * Starting [154G[ OK ]
 * Starting [154G[ OK ]
 * Starting anac(h)ronistic cron[154G[ OK ]
 * Starting ACPI daemon[154G[ OK ]
 [31m*[39;49m jetty is not installed
 * Starting regular background program processing daemon[154G[ OK ]
 * Starting automatic crash report generation[154G[ OK ]
 * Starting CUPS printing spooler/server[154G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting CPU interrupts balancing daemon[154G[ OK ]
 * Stopping save kernel messages[154G[ OK ]
 * Stopping [154G[ OK ]
```

---

### Post by sinbowden on 2013-06-21
have you tried booting to recovery mode and fixing missing/broken packages?

---

### Post by Kodeine on 2013-06-21
When attempting to fix broken packages in recovery mode it seemed to freeze after checking the first of my two drives. I have a file entitled 'xsession-errors.log' in my home folder. Here is it's contents.```
Script for cjkv started at run_im.Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.


(gnome-settings-daemon:1526): GnomeDesktop-WARNING **: GL_MAX_TEXTURE_SIZE helper quit unexpectedly
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/psyduck/.compiz/session/109765340d50789f7e137184580467910200000014510036"
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
ati_pplib_cmd: execute "get" failed!
** Message: using fallback from indicator to GtkStatusIcon


(nautilus:1886): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


(nautilus:1886): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Warn: Attempted to restack relative to 0x1e0018f which is not a child of the root window or a window compiz owns


(gnome-terminal:1977): GLib-GObject-WARNING **: g_object_get_valist: object class 'GtkSettings' has no property named 'gtk-show-input-method-menu'


(gnome-terminal:1977): GLib-GObject-WARNING **: g_object_get_valist: object class 'GtkSettings' has no property named 'gtk-show-input-method-menu'


(gnome-terminal:1977): GLib-GObject-WARNING **: g_object_get_valist: object class 'GtkSettings' has no property named 'gtk-show-input-method-menu'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

---

### Post by sinbowden on 2013-06-21
not sure if it gave you the answere: Please ask your system administrator to enable user sharing.

---

### Post by sinbowden on 2013-06-21
[http://handytutorial.com/enable-advanced-file-sharing-in-ubuntu-13-04-with-samba/](http://handytutorial.com/enable-advanced-file-sharing-in-ubuntu-13-04-with-samba/)  Enable Advanced File Sharing in Ubuntu 13.04 with Samba

---

### Post by Kodeine on 2013-06-21
I re-installed unity and unity-services and re-ran it. Here's it's output.```
psyduck@Skynet:~$ unitycompiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Stopping plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Stopping plugin: workarounds
compiz (core) - Info: Unloading plugin: workarounds
compiz (core) - Info: Stopping plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Stopping plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Stopping plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Stopping plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Unloading plugin: resize
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Unloading plugin: grid
compiz (core) - Info: Stopping plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Stopping plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Stopping plugin: session
compiz (core) - Info: Unloading plugin: session
compiz (core) - Info: Stopping plugin: mousepoll
compiz (core) - Info: Unloading plugin: mousepoll
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Unloading plugin: imgpng
compiz (core) - Info: Stopping plugin: regex
compiz (core) - Info: Unloading plugin: regex
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Unloading plugin: place
compiz (core) - Info: Stopping plugin: snap
compiz (core) - Info: Unloading plugin: snap
compiz (core) - Info: Stopping plugin: vpswitch
compiz (core) - Info: Unloading plugin: vpswitch
compiz (core) - Info: Stopping plugin: gnomecompat
compiz (core) - Info: Unloading plugin: gnomecompat
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Unloading plugin: move
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Unloading plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Stopping plugin: copytex
compiz (core) - Info: Unloading plugin: copytex
compiz (core) - Info: Stopping plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

```

***I installed GDM for my login manager which does not have any screen tearing or console problems. I've now switched to gnome fallback and everything works fine.

---

