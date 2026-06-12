---
title: "gnome session failed"
date: 2005-11-27
forum: Desktop Environments
---

### Post by cheirekov on 2005-11-27
After Installing several packages from Synaptic e.g. smb4k Amarok e.t.c after reboot when i try to login gnome session fails whith thise generated error .xsession-errors:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nemo"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu.nautilus.digsys.bg:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu.nautilus.digsys.bg:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu.nautilus.digsys.bg:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu.nautilus.digsys.bg:/tmp/.ICE-unix/7200

** (gnome-session:7200): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command =
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030
** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030
kbuildsycoca running...

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7310): WARNING **: IPP request failed with status 1030
(gnome-terminal:7457): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7457): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```
When i delete .ICEauthority starts Gnome fail-start or something like this 
Can Somebody Help Me ?:confused:

---

