---
title: "Frequent lock-ups w/GNOME xsession-errors"
date: 2009-11-13
forum: Desktop Environments
---

### Post by JohnE1 on 2009-11-13
I recently upgraded from Ubuntu 9.04 to 9.10 via the Update program.

Frequent = multiple times in a single day

The .xsessions-error file is too big to post here, 136 lines, but the first critical error appears in the first 12 lines... maybe showing you those lines is enough to get some suggestions rolling?


1. /etc/gdm/Xsession: Beginning session setup...
2. Setting IM through im-switch for locale=en_US.
3. Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
4. GNOME_KEYRING_SOCKET=/tmp/keyring-XE2sCd/socket
5. SSH_AUTH_SOCK=/tmp/keyring-XE2sCd/socket.ssh
6.
7. (gnome-settings-daemon:2463): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
8. Unable to find a synaptics device.
9. gnome-session[2374]: WARNING: Could not launch application '106b2a5d4fac162210125793716635178200000023440005.desktop': Unable to start application: Failed to execute child process "indicator-applet-session" (No such file or directory)
10. ** Message: Reading of RFKILL events failed
11. ** Message: killswitches state 3
12. ** Message: killswitches state 3

Any suggestions on how to correct this first GLIB-CRITICAL error?

Thank you all in advance!!

John

---

### Post by JohnE1 on 2009-11-13
Right after posting this message, I walked away... came back to the screensaver... moved the mouse... the screen went black and the gdmlogin never popped up.

I had to force a power down. Upon login, I selected Failsafe GNOME and this time .xsession-errors was only 33 lines, but still have errors... and no doubt, the system will lock-up again multiple times today.

Failsafe GNOME makes the system more stable, but still not out of the woods.

Here's the first 12-lines of .xsession-errors with Failsafe GNOME running.

1.
2. (gnome-settings-daemon:2417): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
3. Window manager warning: Failed to read saved session file /home/jellard/.config/metacity/sessions/1098d84e9735f301a5125811880015754300000024030001.ms: Failed to open file '/home/jellard/.config/metacity/sessions/1098d84e9735f301a5125811880015754300000024030001.ms': No such file or directory
4. Unable to find a synaptics device.
5. 
6. (nautilus:2443): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
7.
8. ** (nautilus:2443): WARNING **: No marshaller for signature of signal 'UploadFinished'
9.
10. ** (nautilus:2443): WARNING **: No marshaller for signature of signal 'DownloadFinished'
11.
12. ** (nautilus:2443): WARNING **: No marshaller for signature of signal 'ShareCreateError'

Thanks again!

John

---

