---
title: "Racing pedals issue with Studio 14.04"
date: 2016-05-17
forum: Gaming &amp; Leisure
---

### Post by rlovi on 2016-05-17
Hi,  I have Ubuntu Studio 14.04 64 bit. I play speed-dreams-2 and have been having trouble getting my racing pedals to work.  I have a Playstation2 Logitech Rally wheel with a playstation to usb adapter that I use though the gas and brake pedals that connect to it would only show up as two buttons within the game. So I thought the solution would be to use a Bodnar cable and connect the pedals separately.  

I re-wired my d-sub connector so it matched  Logitech G25 pedals. The cable and pedal combo works fine in the Windows version of speed-dreams but  I cannot get the darn thing to work in Ubuntu.  

I created the following /lib/udev/rules.d/51-G25-pedals.rules file: 


 ```
SUBSYSTEMS=="input", ATTRS{name}=="Leo Bodnar Logitech® G25 Pedals", ENV{ID_INPUT_ACCELEROMETER}="0", ENV{ID_INPUT_JOYSTICK}="1" 
```  

This solves the permissions problem of the /dev/input/event10 file for the pedals and cable though a /dev/input/js* file is not created for the pedals. If I go into speed-dreams, the pedals do not show up. I'm pulling out what remaining hair I have over this. Can anyone offer help?

```
rlovison@rlovison-DX4300:/dev/input$ ls -l
total 0
drwxr-xr-x  2 root root    200 May 17 12:24 by-id
drwxr-xr-x  2 root root    200 May 17 12:24 by-path
crw-r-----  1 root root 13, 64 May 17 07:01 event0
crw-r-----  1 root root 13, 65 May 17 07:01 event1
crw-rw----+ 1 root root 13, 74 May 17 12:24 event10
crw-rw----+ 1 root root 13, 66 May 17 11:57 event2
crw-r-----  1 root root 13, 67 May 17 07:01 event3
crw-r-----  1 root root 13, 68 May 17 07:01 event4
crw-r-----  1 root root 13, 69 May 17 07:01 event5
crw-r-----  1 root root 13, 70 May 17 07:01 event6
crw-r-----  1 root root 13, 71 May 17 07:01 event7
crw-r-----  1 root root 13, 72 May 17 07:01 event8
crw-rw----+ 1 root root 13, 73 May 17 11:57 event9
crw-rw-r--+ 1 root root 13,  0 May 17 11:57 js0
crw-rw-r--+ 1 root root 13,  1 May 17 11:57 js1
crw-r-----  1 root root 13, 63 May 17 07:01 mice
crw-r-----  1 root root 13, 32 May 17 07:01 mouse0
crw-r-----  1 root root 13, 33 May 17 07:01 mouse1
```

```
rlovison@rlovison-DX4300:/dev/input$ sudo lsinput
[sudo] password for rlovison: 
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_USB
   vendor  : 0x810
   product : 0x1
   version : 272
   name    : "Twin USB Joystick"
   phys    : "usb-0000:00:12.1-3/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC EV_FF

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x62a
   product : 0x4101
   version : 272
   name    : "MOSART Semi. 2.4G Keyboard Mouse"
   phys    : "usb-0000:00:13.0-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x62a
   product : 0x4101
   version : 272
   name    : "MOSART Semi. 2.4G Keyboard Mouse"
   phys    : "usb-0000:00:13.0-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_ABS EV_MSC

/dev/input/event5
   bustype : BUS_USB
   vendor  : 0x3f0
   product : 0x2c24
   version : 272
   name    : "HP HP USB Laser Mouse"
   phys    : "usb-0000:00:12.0-3/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event6
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=3"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event7
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=7"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event8
   bustype : (null)
   vendor  : 0x0
   product : 0x0
   version : 0
   name    : "HDA NVidia HDMI/DP,pcm=8"
   phys    : "ALSA"
   bits ev : EV_SYN EV_SW

/dev/input/event9
   bustype : BUS_USB
   vendor  : 0x810
   product : 0x1
   version : 272
   name    : "Twin USB Joystick"
   phys    : "usb-0000:00:12.1-3/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC EV_FF

/dev/input/event10
   bustype : BUS_USB
   vendor  : 0x1dd2
   product : 0x100c
   version : 272
   name    : "Leo Bodnar Logitech® G25 Pedals"
   phys    : "usb-0000:00:12.1-2/input0"
   uniq    : "B43472"
   bits ev : EV_SYN EV_ABS

```

Syslog output:

```
May 18 09:35:55 rlovison-DX4300 kernel: [ 5373.309495] usb 4-2: USB disconnect, device number 9
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.363865] usb 4-2: new full-speed USB device number 10 using ohci-pci
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.518826] usb 4-2: New USB device found, idVendor=1dd2, idProduct=100c
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.518835] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.518840] usb 4-2: Product: Logitech® G25 Pedals
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.518844] usb 4-2: Manufacturer: Leo Bodnar
May 18 09:35:59 rlovison-DX4300 kernel: [ 5377.518847] usb 4-2: SerialNumber: B43472
May 18 09:36:09 rlovison-DX4300 kernel: [ 5387.531223] hid-generic 0003:1DD2:100C.000D: usb_submit_urb(ctrl) failed: -1
May 18 09:36:09 rlovison-DX4300 kernel: [ 5387.531248] hid-generic 0003:1DD2:100C.000D: timeout initializing reports
May 18 09:36:09 rlovison-DX4300 kernel: [ 5387.531406] input: Leo Bodnar Logitech® G25 Pedals as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/0003:1DD2:100C.000D/input/input20
May 18 09:36:09 rlovison-DX4300 kernel: [ 5387.531671] hid-generic 0003:1DD2:100C.000D: input,hidraw1: USB HID v1.10 Joystick [Leo Bodnar Logitech® G25 Pedals] on usb-0000:00:12.1-2/input0
May 18 09:36:09 rlovison-DX4300 mtp-probe: checking bus 4, device 10: "/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2"
May 18 09:36:09 rlovison-DX4300 mtp-probe: bus: 4, device: 10 was not an MTP device
```

---

### Post by MikeCyber on 2016-05-18
Maybe you could get hints from that Linux forum section:
[http://forums.x-plane.org/index.php?/forums/topic/72733-writing-and-debugging-udev-rules/](http://forums.x-plane.org/index.php?/forums/topic/72733-writing-and-debugging-udev-rules/)
Udev is a shame for Linux and should be removed.

---

### Post by rlovi on 2016-05-18
Thanks Mike. 

The X-Plane forum is where I found most of the info that got me as far as I have. I was hoping that someone here actually found a cure.

---

