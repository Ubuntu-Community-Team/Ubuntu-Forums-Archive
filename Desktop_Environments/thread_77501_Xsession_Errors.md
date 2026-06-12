---
title: "Xsession Errors"
date: 2005-10-16
forum: Desktop Environments
---

### Post by flyingbrass on 2005-10-16
This is on a clean install of Breezy.

Logging into gnome has been flaky.  Sometimes the progress bar would hang after getting to update-notifier.  Occasionally the progress bar window wouldn't close, staying on my desktop for a while after the session had fully loaded.

I haven't been able to make firestarter load consistently at startup.  I have the correct entry in sudoers.  From a terminal sudo firestarter --start-hidden (my startup entry) works fine, but not when a session starts.  Sometimes nothing happens, as if the entry were skipped.  Sometimes firestarter launches fine with nary a peep.  Other times I get the "you need to be root for this" error message, and when that happens sometimes firestarter starts anyway and other times it doesn't.  I've tried changing the startup order around and using gksudo instead.  

When firestarter does load it shows 2 entries in the current session.  My firestarter startup entry shows at order 80 or whatever I've set it at, but there is also another firestarter that is the one actually running.  It is at order 50.

I've tried different session options at login (last, default, gnome) and saving my session when things seem to be working.  Didn't help.  I deleted my ~/.gnome2/session, which seems to have at least temporarily eliminated the progress bar from hanging or sticking around too long.  I renamed .ICEauthority to get a fresh one (just a shot in the dark).  No change.

.xsession-errors shows some things out of whack.  Any idea what is causing them?  Wrong permissions somewhere?  Could this be why firestarter won't load consistently?

These errors happen every time, even without any additional startup programs.

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jd"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/gertrude:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/gertrude:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/gertrude:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/gertrude:/tmp/.ICE-unix/16677
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
Initializing nautilus-open-terminal extension

** (gnome-session:16677): WARNING **: Host name lookup failure on localhost.

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (nautilus:16763): WARNING **: No description found for mime type "x-special/socket" (file is ".gnome-system-monitor.jd"), please tell the gnome-vfs mailing list.

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:16778): WARNING **: IPP request failed with status 1030

[many more of these gnome-cups-icon warnings]
```

---

### Post by flyingbrass on 2005-10-17
The solution [here](http://www.ubuntuforums.org/showpost.php?p=317937&postcount=5) may have solved my firestarter startup issue. It's hard to say for sure after only a few logins, but so far so good.

I'm still wondering about the xsession errors.  Are they common?  Are they a problem?

---

