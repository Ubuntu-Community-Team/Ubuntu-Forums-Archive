---
title: "Laitude D620 crashes before login"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by Zeratul7 on 2007-07-26
Hi,

I am having a very strange problem lately. Feisty on my Presario D620 hangs completely every time after the login background color and mouse cursor loads (but login form still has not loaded yet). Even the mouse wait-cursor is not moving. But even more strange - when I manage to move the mouse right after the background and mouse wait-cursor loads, the login screen will appear and everything works fine.

Here are some logs that can help to idetify the problem:

syslog with crash:
```

Jul 26 10:29:20 pm-suga NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul 26 10:29:20 pm-suga NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jul 26 10:29:20 pm-suga NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Withdrawing address record for 192.168.67.222 on eth0.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.67.222.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Withdrawing address record for fe80::218:8bff:feb2:2427 on eth0.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.67.222.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: New relevant interface eth0.IPv4 for mDNS.
Jul 26 10:29:20 pm-suga avahi-daemon[5098]: Registering new address record for 192.168.67.222 on eth0.IPv4.
Jul 26 10:29:20 pm-suga /etc/mysql/debian-start[5477]: Upgrading MySQL tables if necessary.
Jul 26 10:29:20 pm-suga kernel: [   36.912000] apm: BIOS not found.
Jul 26 10:29:21 pm-suga NetworkManager: <information>^IClearing nscd hosts cache. 
Jul 26 10:29:21 pm-suga NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  

```
this was the last message before I manually restarted...

syslog without crash:
```


Jul 26 10:30:21 pm-suga NetworkManager: <information>^IClearing nscd hosts cache. 
Jul 26 10:30:21 pm-suga NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul 26 10:30:21 pm-suga NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Jul 26 10:30:21 pm-suga NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Jul 26 10:30:21 pm-suga NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Jul 26 10:30:21 pm-suga kernel: [   33.144000] apm: BIOS not found.
Jul 26 10:30:22 pm-suga avahi-daemon[5108]: Registering new address record for fe80::218:8bff:feb2:2427 on eth0.*.
Jul 26 10:30:23 pm-suga kernel: [   35.004000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Jul 26 10:30:23 pm-suga nfsd[5674]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Jul 26 10:30:23 pm-suga nfsd[5674]: nfssvc: writing fds to kernel failed: errno 0 (Success)
Jul 26 10:30:23 pm-suga kernel: [   35.192000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jul 26 10:30:23 pm-suga kernel: [   35.192000] NFSD: starting 90-second grace period
Jul 26 10:30:23 pm-suga /etc/mysql/debian-start[5702]: Checking for crashed MySQL tables.
Jul 26 10:30:23 pm-suga kernel: [   35.616000] hub 1-2:1.0: port 3 disabled by hub (EMI?), re-enabling...
Jul 26 10:30:23 pm-suga kernel: [   35.616000] usb 1-2.3: USB disconnect, address 5
Jul 26 10:30:23 pm-suga kernel: [   35.616000] usb 1-2.3.1: USB disconnect, address 7
Jul 26 10:30:23 pm-suga kernel: [   35.616000] hub 1-2.3:1.0: hub_port_status failed (err = -71)
Jul 26 10:30:23 pm-suga kernel: [   35.616000] hub 1-2.3:1.0: cannot disable port 1 (err = -19)
```

Here are the last lines of Xorg logs
crashed log:
```

(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```

not crashed log:
```

(**) Option "MaxDoubleTapTime" "100"
(**) Option "ClickTime" "0"
(**) Option "EmulateMidButtonTime" "75"
(**) Option "FingerLow" "14"
(**) Option "FingerHigh" "15"
(**) Option "UpDownScrolling" "1"
(**) Option "CircularScrolling" "1"
(**) Option "CircScrollTrigger" "2"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?

```

These logs do not seem odd to me, but I have no idea where to search next.
The only strange thing I have noticed is the row "apm: BIOS not found." is the last line in many different logs but this row also is present in no-crash logs.

---

### Post by Knapra on 2007-08-08
Try commenting out the wacom stuff in xorg.conf. Those caused my comp to freeze just like that after I upgraded it a few days ago. Apparently they shouldn't cause a crash, but all evidence points the guiltyfinger their way.

Easiest workaround is the safe mode, root and startx unless yiou're used to wrestle with vi.

---

