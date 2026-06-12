---
title: "Need help testing something"
date: 2007-09-19
forum: Desktop Environments
---

### Post by Beggar on 2007-09-19
Hey guys I need some help. So I just installed a new login screen and splash screen, and I have been having problems all night. I have tracked it down to the splash screen. I can use any splash screen image, except the one I want to.
  Can anyone else confirm that the attached image can't be set as a splash screen thus rescuing my sanity from the brink?

  And can anyone explain to me why this image alone would not work? I have changed it to jpg, greyscale, resized it to 2 pxl/2 pxls. I can just grab any random image on my hdd and it works fine, but not this image...

---

### Post by Beggar on 2007-09-19
Oh, case anyone is interested, my xsession-errors file.

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "darren"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/beggarbox:/tmp/.ICE-unix/18062
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

(gnome-panel:18122): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x80ca248

(gnome-panel:18122): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x80ca248
Initializing gnome-mount extension

(update-notifier:18137): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:18143): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 78953 1190260800 1190181847
evolution-alarm-notify-Message:  Thu Sep 20 00:00:00 2007

evolution-alarm-notify-Message:  Wed Sep 19 02:04:07 2007


(gnome-power-manager:18144): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

---

### Post by Beggar on 2007-09-19
It would be awesome if someone could set this image as their splash image, then restart X. No damage or anything is done, you just need to change you splash back if it pops up an error dialog. Please guys :)

---

### Post by Beggar on 2007-09-20
Thanks for the help everyone, guess Ill try and track down a friend using ubuntu.

---

