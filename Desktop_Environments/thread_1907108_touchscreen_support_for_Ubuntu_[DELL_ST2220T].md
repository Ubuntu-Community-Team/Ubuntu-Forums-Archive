---
title: "touchscreen support for Ubuntu [DELL ST2220T]"
date: 2012-01-10
forum: Desktop Environments
---

### Post by vmtb on 2012-01-10
[LIST]
[*]Using Ubuntu 11.10 32bit Unity
[/LIST]

[LIST]
[*]Having a DELL ST2220T Touchscreen Monitor, reporting internally as "LG Display LGD-MultiTouch"
[/LIST]

Iam sort of Stuck with getting it to work.
Status is, when Its plugged in it gets recognized.
Somehow works, but not really.
It reacts on a touch, but the calibration is completely borked. If i use two fingers (Multitouch) it moves the mouse around, but only in the left upper corner not more than 5cm left right, and 2cm up down - while using the whole screen to touch. 
If i run "xinput_calibrator" it reacts on the upper left touchpoint, but not the second one. Its reported as to near to the first toouchpoint. (seems its only operating in the 5cm area) 

Its weird, somehow it works, and reacts on the touches - and somehow I cant really get it to work.

at some spots in the Net its reported that some people have get it to work properly - So i assume its more like a calibration, Installation and Softwareproblem rather that its not working at all.

Its actually the only really Usefull Touchscreen on the Market at the moment (High Resolution1920x1080, IPS-Panel, Multitouch, ...) and the best is you can really put it to any angle you want to have it - even laying it flat on the table. No other Touchscreen has this at the moment, which makes it prefect for a Touchscreen to work with. Thats why i try to put some effort in it, and really want to get it to work. Unfortunately there is not much to read on the Web about this Touchscreen.
Some say they managed it getting to work with "evdev".

Tried to add some parts to /etc/X11/xorg.conf 
without any success, it does not really react on that parts. more likely i just do not know where the possible problem is - or could be. 
Why is it not recognizing the Touchscreen as real Touchdevice, and why is there "Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect" in the Xorg Log file?
It also does not recognize the Mouse for the LG Device.

Maybe someone can Help out with this, since iam really stuck somehow.
Maybe even somone who has specially this Monitor running with ubuntu. Its reported that it worked with Fedora, and somehow with Debian Squeeze. So it must be possible to get it to work with Ubuntu somehow. (see the Links at the bottom)


**evtest**
```

> evtest
/dev/input/event7:    LG Display LGD-MultiTouch

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x1fd2 product 0x64 version 0x100
Input device name: "LG Display LGD-MultiTouch"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 330 (Touch)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value  65535
      Min        0
      Max    32767
    Event code 1 (Y)
      Value  65535
      Min        0
      Max    32767
    Event code 47 (Slot)
      Value      0
      Min        0
      Max        1
    Event code 53 (Positi659] (**) mytouchscreen: Device: "/dev/input/event6"
[  8317.660] (WW) mytouchscreen: Don't know how to use device
on X)
      Value      0
      Min        0
      Max    32767
    Event code 54 (Position Y)
      Value      0
      Min        0
      Max    32767
    Event code 57 (Tracking ID)
      Value      0
      Min        0
      Max    65535

```cat /var/log/Xorg.0.log
```

[  8317.723] (II) config/udev: Adding input device LG Display LGD-MultiTouch (/dev/input/event7)
[  8317.723] (**) LG Display LGD-MultiTouch: Applying InputClass "evdev touchscreen catchall"
[  8317.723] (II) Using input driver 'evdev' for 'LG Display LGD-MultiTouch'
[  8317.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8317.723] (**) LG Display LGD-MultiTouch: always reports core events
[  8317.723] (**) LG Display LGD-MultiTouch: Device: "/dev/input/event7"
[  8317.724] (--) LG Display LGD-MultiTouch: Found absolute axes
[  8317.725] (--) LG Display LGD-MultiTouch: Found x and y absolute axes
[  8317.725] (--) LG Display LGD-MultiTouch: Found absolute touchscreen
[  8317.726] (II) LG Display LGD-MultiTouch: Configuring as touchscreen
[  8317.726] (**) LG Display LGD-MultiTouch: YAxisMapping: buttons 4 and 5
[  8317.726] (**) LG Display LGD-MultiTouch: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  8317.726] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4.1/1-4.1:1.0/input/input7/event7"
[  8317.726] (II) XINPUT: Adding extended input device "LG Display LGD-MultiTouch" (type: TOUCHSCREEN)
[  8317.726] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[  8317.726] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[  8317.726] (II) LG Display LGD-MultiTouch: initialized for absolute axes.
[  8317.726] (**) LG Display LGD-MultiTouch: (accel) keeping acceleration scheme 1
[  8317.726] (**) LG Display LGD-MultiTouch: (accel) acceleration profile 0
[  8317.726] (**) LG Display LGD-MultiTouch: (accel) acceleration factor: 2.000
[  8317.726] (**) LG Display LGD-MultiTouch: (accel) acceleration threshold: 4
[  8317.728] (II) config/udev: Adding input device LG Display LGD-MultiTouch (/dev/input/mouse1)
[  8317.728] (II) No input driver/identifier specified (ignoring)

```having nothing but a basic setup in the /etc/X11/xorg.conf

**reference Links:**

[LIST]
[*][http://www.innovationsts.com/blog/?p=3040](http://www.innovationsts.com/blog/?p=3040)
[/LIST]

[LIST]
[*][http://debianforum.de/forum/viewtopic.php?f=13&t=129134&start=30](http://debianforum.de/forum/viewtopic.php?f=13&t=129134&start=30)
[/LIST]

[LIST]
[*][https://groups.google.com/group/fa.linux.kernel/browse_thread/thread/51eb74dac9866a4f/7c7e23afdee025e8?lnk=gst&q=Dell+ST2220T#7c7e23afdee025e8](https://groups.google.com/group/fa.linux.kernel/browse_thread/thread/51eb74dac9866a4f/7c7e23afdee025e8?lnk=gst&q=Dell+ST2220T#7c7e23afdee025e8)
[/LIST]

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1765217&page=2](http://ubuntuforums.org/showthread.php?t=1765217&page=2)
[/LIST]

---

### Post by HughR on 2012-08-19
It isn't working for me on Ubuntu 12.04 + all updates.

It is working on Fedora 17 (I haven't tried multitouch).

---

### Post by HughR on 2012-10-29
There's a new thread at [http://ubuntuforums.org/showthread.php?p=12323939]("http://ubuntuforums.org/showthread.php?p=12323939")

---

