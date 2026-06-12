---
title: "Administratvie User Can't log in."
date: 2005-12-30
forum: Desktop Environments
---

### Post by encompass on 2005-12-30
After my computer runs for a while.  I get issues with my main user... encompass... being able to log in.  It gets to the brown ubuntu color screen and waits with the mouse that I can move around.  It is the standard, not busy mouse.  I can drop to console and other what not.
I can login from the console.
I can login with other accounts.
I can restart the Xserver, but that doesn't fix it.
The only solution I have had so far is rebooting the computer.  And it works again.
Perhaps if I wait enough like my error that I posts just before this one.  It would solve itself.
I have also trys moving everything from my home dir to /old_filed/ and seeing if it would load a default acount... but noppers.  same error.
Any Ideas?

---

### Post by Ampersand on 2005-12-31
Do you still get  menu if you right click on the desktop?

If you go to another console (Ctrl, Alt + F1) and type
```
killall gnome-panel
```
then go back to the Gnome desktop (Ctrl, Alt + F7), do you get any further?

---

### Post by encompass on 2005-12-31
No nothing... I don't think the process exists when I run the command.  I have noticed that sometimes if I wait a REALY long time it will start.  But many times, I may not have waited long enough... 20 minutes once.
As another note... 
The other accounts seem to be doing that now too.
Do you think there is a log file I can look for errors in?

---

### Post by encompass on 2006-01-04
This is the ouput of my xsession when I can't login

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "encompass"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/brower:/tmp/.ICE-unix/7605

nothing unussual concidering this is a successful login...
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "encompass"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/brower:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/brower:/tmp/.ICE-unix/6316

** (gnome-session:6316): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 0
manager.c/562: setting[1]: bool: autoburn = 0
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command = 
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 0
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 1
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:6432): WARNING **: IPP request failed with status 1280

** (gnome-cups-icon:6432): WARNING **: IPP request failed with status 1280

(gnome-panel:6420): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `icon_name != NULL' failed

(nautilus:6422): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

(totem:6466): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:6466): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
ERROR: Could not determine network interfaces, you must use a interfaces config line

(gnome-terminal:6490): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:6490): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

ideas anyone?

---

### Post by karderio on 2006-01-04
From here I can only realy put you onto some paths.

Try to start a login, then switch virtual terminal, login in text mode, and type "ps aux". Use shift+PageUp to scroll through output (if this does not let you scroll, type "ps aux | less" insted). You may notice some suspicious process, such as a high CPU usage...

Try "sudo dmesg", you never know, same thing : anything suspicious at end of output.

Try switching to the information console (ctrl+alt+F12 on my distrib), same thing : anything suspicious at end of output.

Have a look at the most recent file in /var/log/gdm.

It smells like a program that blocks login may be taking an awful long time to start up. How about trying to log into another desktop environment, such as XFCE or Blackbox. I do not know if these are available on Ubuntu, but if they are they are *very* small and unobtrusive. That way we will know if it is GNOME related or not.

That is all I can think of for the moment, I will ponder on this and get back to you if I think of anything.

---

