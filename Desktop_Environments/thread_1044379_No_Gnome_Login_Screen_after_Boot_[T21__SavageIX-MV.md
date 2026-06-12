---
title: "No Gnome Login Screen after Boot [T21 / Savage/IX-MV]"
date: 2009-01-19
forum: Desktop Environments
---

### Post by oberubu on 2009-01-19
Hello,

although my English is probably not the very best, i hope you can help me with this annoying problem. I have an IBM Thinkpad T21 with Savage/IX-MV Graphics Card. 
When i power on my notebook ubuntu starts just fine, the splash screens shows up an the loading bar goes through until the end and then i get a black screen with a "_". 
Nothing more happens, it doesn't keep on doing anything. I tried every key combination I remembered like CRTL+ALT+F1(-F12) and CRTL+ALT+Backspace => without reaction:(

Then i poweroff the notebook an turn it on again: Ubuntu starts just fine and shows the GNOME login screen. When i shutdown the computer properly with the shutdown menu and then try to reboot it i get the same result as described above > black screen.:confused:

I tried to look in the Xorg.log, but i could not determine the problem. Here is a diff of both Xorg.logs, left when the computer starts properly and right when it hangs up with the black screen before login:

```
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 18 15:54:56 2009	|(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 18 15:57:43 2009
(II) SAVAGE(0): [drm] Status handle = 0x0fcb6000			|(II) SAVAGE(0): [drm] Status handle = 0x0fcba000
(II) SAVAGE(0): [drm] Status page mapped at 0xb1f44000			|(II) SAVAGE(0): [drm] Status page mapped at 0xb1f65000
(II) SAVAGE(0): [junkers]	status:handle:0x0fcb6000		|(II) SAVAGE(0): [junkers]	status:handle:0x0fcba000
(II) SAVAGE(0): [junkers]	status:map:0xb1f44000			|(II) SAVAGE(0): [junkers]	status:map:0xb1f65000
(II) SAVAGE(0): [junkers]	statusHandle:0x0fcb6000			|(II) SAVAGE(0): [junkers]	statusHandle:0x0fcba000
(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event7"			|(**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event6"
(**) Video Bus: Device: "/dev/input/event6"				|(**) Video Bus: Device: "/dev/input/event7"
									>(II) Video Bus: Found keys
									>(II) Video Bus: Configuring as keyboard
									>(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
									>(**) Option "xkb_rules" "evdev"
									>(**) Video Bus: xkb_rules: "evdev"
									>(**) Option "xkb_model" "pc105"
									>(**) Video Bus: xkb_model: "pc105"
									>(**) Option "xkb_layout" "de"
									>(**) Video Bus: xkb_layout: "de"
									>AUDIT: Sun Jan 18 15:57:55 2009: 5288 X: client 4 rejected from local host ( uid=0 gid=0 pid=5494 )
									>AUDIT: Sun Jan 18 15:58:02 2009: 5288 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5499 )
									>AUDIT: Sun Jan 18 15:58:02 2009: 5288 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5500 )
									>AUDIT: Sun Jan 18 15:58:02 2009: 5288 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=5501 )
```

Can anyone explain why it says "Video Bus: Configuring as keyboard"??
I have attached the full Xorg.logs and my Xorg.conf (which is standard).

Hope you might help me,
oberubu

Edit: System is latest Ubuntu 8.10

---

### Post by oberubu on 2009-03-12
I finally figured it out. It is an already documented bug on launchpad.[https://launchpad.net/ubuntu/+source/xserver-xorg-driver-savage/+bug/33617](https://launchpad.net/ubuntu/+source/xserver-xorg-driver-savage/+bug/33617)

Adding:

```
Option "BusType" "PCI"

```
in Section "Device" to xorg.conf helped for me.

Could anyone mark this topic now as solved?

regards

---

