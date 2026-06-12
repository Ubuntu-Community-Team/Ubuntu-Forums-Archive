---
title: "Sudden restart of my window manager everytime i log in due to segmentation fault"
date: 2008-12-22
forum: Desktop Environments
---

### Post by Alaak on 2008-12-22
Hi

I recently got a problem with my xfce desktop manager. Actually it occured after the update I did last friday (19.12.2008). My desktop manager restarts everytime I log in after telling me that the session lasted for less than 10 seconds. If I do not klick on OK on this error message I can however work normally. At first I got the following .xsession-errors file:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=de_DE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
Agent pid 6836
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
                  Ignoring extra symbols
Warning:          Key <OUTP> not found in evdev+aliases(qwertz) keycodes
                  Symbols ignored
Warning:          Key <KITG> not found in evdev+aliases(qwertz) keycodes
                  Symbols ignored
Warning:          Key <KIDN> not found in evdev+aliases(qwertz) keycodes
                  Symbols ignored
Warning:          Key <KIUP> not found in evdev+aliases(qwertz) keycodes
                  Symbols ignored
Warning:          Key <RO> not found in evdev+aliases(qwertz) keycodes
                  Symbols ignored
Warning:          No symbols defined for <AB11> (keycode 97)
Warning:          No symbols defined for <JPCM> (keycode 103)
Warning:          No symbols defined for <I120> (keycode 120)
Warning:          No symbols defined for <AE13> (keycode 132)
Warning:          No symbols defined for <I149> (keycode 149)
Warning:          No symbols defined for <I154> (keycode 154)
Warning:          No symbols defined for <I161> (keycode 161)
Warning:          No symbols defined for <I168> (keycode 168)
Warning:          No symbols defined for <I178> (keycode 178)
Warning:          No symbols defined for <I183> (keycode 183)
Warning:          No symbols defined for <I184> (keycode 184)
Warning:          No symbols defined for <FK13> (keycode 191)
Warning:          No symbols defined for <FK14> (keycode 192)
Warning:          No symbols defined for <FK15> (keycode 193)
Warning:          No symbols defined for <FK16> (keycode 194)
Warning:          No symbols defined for <FK17> (keycode 195)
Warning:          No symbols defined for <FK18> (keycode 196)
Warning:          No symbols defined for <FK19> (keycode 197)
Warning:          No symbols defined for <FK20> (keycode 198)
Warning:          No symbols defined for <FK21> (keycode 199)
Warning:          No symbols defined for <FK22> (keycode 200)
Warning:          No symbols defined for <FK23> (keycode 201)
Warning:          No symbols defined for <FK24> (keycode 202)
Warning:          No symbols defined for <I217> (keycode 217)
Warning:          No symbols defined for <I219> (keycode 219)
Warning:          No symbols defined for <I221> (keycode 221)
Warning:          No symbols defined for <I222> (keycode 222)
Warning:          No symbols defined for <I224> (keycode 224)
Warning:          No symbols defined for <I226> (keycode 226)
Warning:          No symbols defined for <I228> (keycode 228)
Warning:          No symbols defined for <I230> (keycode 230)
Warning:          No symbols defined for <I247> (keycode 247)
Warning:          No symbols defined for <I248> (keycode 248)
Warning:          No symbols defined for <I249> (keycode 249)
Warning:          No symbols defined for <I250> (keycode 250)
Warning:          No symbols defined for <I251> (keycode 251)
Warning:          No symbols defined for <I252> (keycode 252)
Warning:          No symbols defined for <I253> (keycode 253)
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-jfIHwI6835/agent.6835

** (xfce4-session:6838): WARNING **: Unable to launch "xfce4-volstatus-icon" (specified by autostart/xfce4-volstatus-icon.desktop): Failed to execute child process "xfce4-volstatus-icon" (No such file or directory)

** (xfce4-session:6838): WARNING **: Unable to launch "xfce4-volstatus-icon" (specified by autostart/xfce4-volstatus-icon.desktop): Failed to execute child process "xfce4-volstatus-icon" (No such file or directory)

(file-roller:6872): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6893): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6879): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6873): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6871): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6899): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:6885): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(xfwm4:6853): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:6853): libxfcegui4-WARNING **: Disconnected from session manager.
Segmentation fault
Agent pid 6836 killed

```

Due to some threads I read on our german forums I deactivated the session saving of xfce, changed the symbol style and made another upgrade on saturday. With these modifications the error was gone until the next upgrade yesterday. Now it occurs producing the following .xsession-errors file:
```

...

(xfce4-session:7205): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed

(xfwm4:7216): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:7216): libxfcegui4-WARNING **: Disconnected from session manager.

(xfdesktop:7219): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:7219): libxfcegui4-WARNING **: Disconnected from session manager.
Agent pid 7203 killed

```

Does someone have an idea how to fix this problem? I feel very uncomfortable working on my master thesis with this error message in the background. ^^

---

### Post by Alaak on 2008-12-28
I fixed the issue by reinstalling my system.

---

