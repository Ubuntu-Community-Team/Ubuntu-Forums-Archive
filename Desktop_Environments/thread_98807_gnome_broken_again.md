---
title: "gnome broken again"
date: 2005-12-04
forum: Desktop Environments
---

### Post by teaker1s on 2005-12-04
this time to my knowlege all I've done is surf the web and empty the trash weird things started happening like I have a saved session- I use and unless I change something I used that session okay for ages. then the panel I added switched from left to right and on login I get

Failed to load image trashcan_full

Details: Icon not found

only affects my login:confused: 







Xsession: X session started for daniel at Sun Dec  4 13:31:14 GMT 2005
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu:/tmp/.ICE-unix/13665
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

(gnome-panel:13781): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `icon_name != NULL' failed

(gnome-panel:13781): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `icon_name != NULL' failed

(gnome-panel:13781): Gtk-CRITICAL **: gtk_drag_source_set_icon_name: assertion `icon_name != NULL' failed

** (gnome-session:13665): WARNING **: Host name lookup failure on localhost.
resutlt: 1

---

### Post by flopsy on 2005-12-04
As a guess, I'd log out and try

```
rm -ir /tmp/.ICE-unix
rm -ir ~/.ICEauthority
```

in a console (Ctrl-Alt-F2). Ctrl-D logs out. Alt-F7 takes you back to gdm.

---

### Post by teaker1s on 2005-12-04
turns out to be removing trash can didn't remove all settings from the panel-this will be third time gnome gone flakey kde is buggy but not this bad

---

