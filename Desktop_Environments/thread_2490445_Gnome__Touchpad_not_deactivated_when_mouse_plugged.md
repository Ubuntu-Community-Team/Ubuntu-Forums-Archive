---
title: "Gnome : Touchpad not deactivated when mouse plugged in."
date: 2023-09-04
forum: Desktop Environments
---

### Post by georgesgiralt on 2023-09-04
Hi Guys,
On my old laptop, running 22.04.1 LTS, I configured the Gnome config to set "org.gnome.desktop.peripherals.touchpad" to "Disabled-on-external-mouse".
IT was effective on two other laptops I own, but on this one, does not work. 
As does not work the "disable touchpad when typing". 
So I decided to investigate the problem...
Below you will see what happens when I turn on the Bluetooth mouse ON : 
```

Sep  4 16:39:41 isengrin systemd[2905]: Reached target Bluetooth.
Sep  4 16:39:41 isengrin kernel: [   70.666641] hid: raw HID events driver (C) Jiri Kosina
Sep  4 16:39:42 isengrin kernel: [   71.237833] input: BT5.0 Mouse as /devices/virtual/misc/uhid/0005:000E:3412.0001/input/input16
Sep  4 16:39:42 isengrin kernel: [   71.238150] hid-generic 0005:000E:3412.0001: input,hidraw0: BLUETOOTH HID v5.06 Mouse [BT5.0 Mouse] on ac:7b:a1:4f:fd:1b
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) config/udev: Adding input device BT5.0 Mouse (/dev/input/mouse2)
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) No input driver specified, ignoring this device.
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) This device may have been added with another device file.
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) config/udev: Adding input device BT5.0 Mouse (/dev/input/event14)
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) BT5.0 Mouse: Applying InputClass "libinput pointer catchall"
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) Using input driver 'libinput' for 'BT5.0 Mouse'
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) systemd-logind: got fd for /dev/input/event14 13:78 fd 57 paused 0
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) BT5.0 Mouse: always reports core events
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) Option "Device" "/dev/input/event14"
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) event14 - BT5.0 Mouse: is tagged by udev as: Mouse
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) event14 - BT5.0 Mouse: device is a pointer
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) event14 - BT5.0 Mouse: device removed
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) Option "config_info" "udev:/sys/devices/virtual/misc/uhid/0005:000E:3412.0001/input/inp  from Gnomeut16/event14"
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) XINPUT: Adding extended input device "BT5.0 Mouse" (type: MOUSE, id 14)
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) Option "AccelerationScheme" "none"
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) BT5.0 Mouse: (accel) selected scheme none/0
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) BT5.0 Mouse: (accel) acceleration factor: 2.000
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (**) BT5.0 Mouse: (accel) acceleration threshold: 4
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) event14 - BT5.0 Mouse: is tagged by udev as: Mouse
Sep  4 16:39:42 isengrin /usr/libexec/gdm-x-session[3053]: (II) event14 - BT5.0 Mouse: device is a pointer
Sep  4 16:39:49 isengrin geoclue[2699]: Service not used for 60 seconds. Shutting down..
Sep  4 16:39:49 isengrin systemd[1]: geoclue.service: Deactivated successfully.
Sep  4 16:40:04 isengrin zeitgeist-datah[3929]: zeitgeist-datahub.vala:210: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
Sep  4 16:40:04 isengrin systemd[2905]: Started Application launched by gnome-session-binary.
Sep  4 16:40:04 isengrin systemd[2905]: message repeated 2 times: [ Started Application launched by gnome-session-binary.]

```
The touchpad is active. 
On another laptop, I get different messages with the same mouse (it has 2 Bluetooth interfaces) ... and the touchpad is inactive.... when the mouse is "plugged".
```

Sep  4 17:04:07 Espineux systemd[3169]: Reached target Bluetooth.
Sep  4 17:04:07 Espineux kernel: [ 4535.749875] input: BT5.0 Mouse as /devices/virtual/misc/uhid/0005:000E:3412.0005/input/input21
Sep  4 17:04:07 Espineux kernel: [ 4535.750182] hid-generic 0005:000E:3412.0005: input,hidraw2: BLUETOOTH HID v5.06 Mouse [BT5.0 Mouse] on b0:60:88:f2:05:d9
Sep  4 17:04:15 Espineux NetworkManager[1409]: <info>  [1693839855.9164] agent-manager: agent[c1d84d28b6ea0545,:1.99/org.gnome.Shell.NetworkAgent/1000]: agent registered
Sep  4 17:04:15 Espineux ubuntu-appindicators@ubuntu.com[3415]: unable to update icon for software-update-available
Sep  4 17:04:15 Espineux ubuntu-appindicators@ubuntu.com[3415]: unable to update icon for livepatch
Sep  4 17:04:15 Espineux ubuntu-appindicators@ubuntu.com[3415]: unable to update icon for MEGAsync
Sep  4 17:04:16 Espineux dbus-daemon[3189]: [session uid=1000 pid=3189] Activating service name='org.gnome.ArchiveManager1' requested by ':1.183' (uid=1000 pid=38658 comm="gjs /usr/share/gnome-shell/extensions/ding@rasters" label="unconfined")
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Sep  4 17:04:16 Espineux gnome-shell[3415]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Sep  4 17:04:16 Espineux dbus-daemon[3189]: [session uid=1000 pid=3189] Successfully activated service 'org.gnome.ArchiveManager1'
Sep  4 17:04:16 Espineux gnome-shell[3415]: DING: Detected async api for thumbnails

```
And I can't understand why the two outputs are different and why, even if both configurations are set the same, it works on one machine and not in the other. 
So any help will be greatly appreciated ! 
Have a nice day !

---

### Post by #&amp;thj^% on 2023-09-04
I'm seeing this more and more, just not on my end though.
This seems to work for me:
```
 gsettings set org.gnome.desktop.peripherals.touchpad send-events disabled-on-external-mouse
###AND
gsettings set org.gnome.desktop.peripherals.touchpad disable-while-typing true

```
NOTE: This no longer works on All Hardware so have a look here:[https://github.com/atareao/Touchpad-Indicator](https://github.com/atareao/Touchpad-Indicator)
Touchpad Indicator also allows you to disable the touchpad when a mouse is plugged in, but it also comes with some other features, like allowing you to enable or disable the touchpad from its menu, and enable or disable touchpad when the application starts or quits.

Good Luck

---

### Post by georgesgiralt on 2023-09-04
Hello 1Fallen,
I switched from Touchpad-Indicator because it won't work in 22.04LTS due to Wayland not handling Xinput "properly" ( like the X11 server did)...
Seems I'm doomed ...
The two gsettings are properly set for my laptop...

---

### Post by georgesgiralt on 2023-09-04
Hello,
I've solved my issue. 
Looking at the logs from the culprit machine, I saw that the lines were "old style" 
```
/usr/libexec/gdm-x-session[3053]: (II) This device may have been added with another device file.
```
This did not look at all like Wayland log lines, but X11. 
So I logged out and checked the login parameters (the little gear you have in the right lower hand side of the screen. 
Bingo ! It was set to "Ubuntu" and not to "Ubuntu on Wayland". Switched and problem solved.
It is fun, though, that Gnome is unable to switch between two detection methods. even if the session management and display are Gnome ...
Well, I retired too long ago. 
Thanks for your help.

---

