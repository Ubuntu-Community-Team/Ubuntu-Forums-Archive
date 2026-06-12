---
title: "/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for read"
date: 2009-03-29
forum: General Help
---

### Post by orengolan on 2009-03-29
Whenever I login to xubuntu I see a pop up with this message:
```
Your session only lasted less than 10 seconds.  
If you have not logged out yourself, 
this could mean that there is some installation problem 
or that you may be out of diskspace.
Try logging in with one of the failsafe sessions 
to see if you can fix this problem.
```
when I click on View details (~/.xsession-errors file) it shows this:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/yuka/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
**/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading**
/usr/bin/xmodmap:  1 error encountered, aborting.
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.7

Starting SCIM as daemon ...
SCIM has been successfully launched.
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          Key <OUTP> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KITG> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KIDN> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KIUP> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <RO> not found in evdev+aliases(qwerty) keycodes
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

** (xfce-mcs-manager:5974): WARNING **: display_plugin: Unable to configure display resolution
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-tnOkzf5883/agent.5883
read: Connection reset by peer
read: Connection reset by peer

** (update-notifier:6016): WARNING **: already running?


** (update-notifier:6032): WARNING **: already running?


** (nm-applet:6035): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6035): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
read: Connection reset by peer

** (update-notifier:6060): WARNING **: already running?


** (update-notifier:6071): WARNING **: already running?


(xfwm4:5989): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:5989): libxfcegui4-WARNING **: Disconnected from session manager.

I can still use the copmuter but if I bring the popup to the /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/yuka/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.7

Starting SCIM as daemon ...
SCIM has been successfully launched.
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
Warning:          Key <OUTP> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KITG> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KIDN> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <KIUP> not found in evdev+aliases(qwerty) keycodes
                  Symbols ignored
Warning:          Key <RO> not found in evdev+aliases(qwerty) keycodes
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

** (xfce-mcs-manager:5974): WARNING **: display_plugin: Unable to configure display resolution
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-tnOkzf5883/agent.5883
read: Connection reset by peer
read: Connection reset by peer

** (update-notifier:6016): WARNING **: already running?


** (update-notifier:6032): WARNING **: already running?


** (nm-applet:6035): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6035): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
read: Connection reset by peer

** (update-notifier:6060): WARNING **: already running?


** (update-notifier:6071): WARNING **: already running?


(xfwm4:5989): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:5989): libxfcegui4-WARNING **: Disconnected from session manager.
```

btw, I can still use my computer but if close popup, it log me out and I have to login again.

Thanks,
Oren

---

### Post by bomek on 2009-04-25
I got the same problem after upgrading to jaunty

---

### Post by eamonireland on 2009-05-05
Same here Bomek - Did you get it fixed? I'm completely stuck.

---

