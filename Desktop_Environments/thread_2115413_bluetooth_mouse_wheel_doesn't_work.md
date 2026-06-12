---
title: "bluetooth mouse wheel doesn't work"
date: 2013-02-12
forum: Desktop Environments
---

### Post by ghost shell on 2013-02-12
I have a bluetooth mouse and it works except for the mouse wheel.
The thing is, I don't know if the mouse wheel even works, as I was unable to test the mouse in a windows environment. I did test the mouse on android, and the mouse didn't work.
I also tried xev but it didn't say anything when scrolling with the mouse wheel. It the wheel button does work though.

From xinput --list:
> 
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                  id=14   [slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Mouse                           id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam                        id=11   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=12   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=13   [slave  keyboard (3)]
    &#8627; ACPI Virtual Keyboard Device              id=15   [slave  keyboard (3)]



What I get from xorg log:
> [ 28074.420] (II) config/udev: Adding input device Bluetooth Mouse (/dev/input/mouse0)
[ 28074.420] (II) No input driver specified, ignoring this device.
[ 28074.420] (II) This device may have been added with another device file.
[ 28074.420] (II) config/udev: Adding input device Bluetooth Mouse (/dev/input/event1)
[ 28074.420] (**) Bluetooth Mouse: Applying InputClass "evdev pointer catchall"
[ 28074.420] (II) Using input driver 'evdev' for 'Bluetooth Mouse'
[ 28074.420] (**) Bluetooth Mouse: always reports core events
[ 28074.421] (**) evdev: Bluetooth Mouse: Device: "/dev/input/event1"
[ 28074.424] (--) evdev: Bluetooth Mouse: Vendor 0x56e Product 0x61
[ 28074.424] (--) evdev: Bluetooth Mouse: Found 12 mouse buttons
[ 28074.424] (--) evdev: Bluetooth Mouse: Found scroll wheel(s)
[ 28074.424] (--) evdev: Bluetooth Mouse: Found relative axes
[ 28074.424] (--) evdev: Bluetooth Mouse: Found x and y relative axes
[ 28074.424] (--) evdev: Bluetooth Mouse: Found absolute axes
[ 28074.424] (II) evdev: Bluetooth Mouse: Forcing absolute x/y axes to exist.
[ 28074.424] (II) evdev: Bluetooth Mouse: Configuring as mouse
[ 28074.424] (II) evdev: Bluetooth Mouse: Adding scrollwheel support
[ 28074.424] (**) evdev: Bluetooth Mouse: YAxisMapping: buttons 4 and 5
[ 28074.424] (**) evdev: Bluetooth Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 28074.424] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/bluetooth/hci0/hci0:42/input16/event1"
[ 28074.424] (II) XINPUT: Adding extended input device "Bluetooth Mouse" (type: MOUSE, id 10)
[ 28074.424] (II) evdev: Bluetooth Mouse: initialized for relative axes.
[ 28074.424] (WW) evdev: Bluetooth Mouse: ignoring absolute axes.
[ 28074.424] (**) Bluetooth Mouse: (accel) keeping acceleration scheme 1
[ 28074.424] (**) Bluetooth Mouse: (accel) acceleration profile 0
[ 28074.425] (**) Bluetooth Mouse: (accel) acceleration factor: 2.000
[ 28074.425] (**) Bluetooth Mouse: (accel) acceleration threshold: 4

One odd thing is that it says it's a 12 button mouse but it's only a... well... 6?
2 normal buttons (right + left), another 2 sideways (back + forward) and a DPI button, plus the middle click with the wheel. I'm guessing the On/Off and pairing buttons don't count.
It's a Bluetooth Glaser Mouse (bought in ebay sent from china):
[img]http://i01.i.aliimg.com/img/pb/169/542/526/526542169_711.JPG[/img]


From what I could google I suspect I have to put up some udev rules, but I don't know what the correct recipe is.
I did find something that could be useful, [http://forums.fedoraforum.org/showthread.php?t=282707](http://forums.fedoraforum.org/showthread.php?t=282707) but I still can't see how can I adapt it to mine.

Another thing is that I have multiple user accounts on my laptop (personal, work, etc), and the above scripts seem to target one user. I'd like it for it to be multiple user.


Any ideas?

Thanks

---

### Post by volfoni54 on 2013-04-05
Hi,

I have excatly the same mouse.
Did you mannge to solve your Pb.

I have also a strange behaviour : She doesn't work as soon as I switch it on. I have to wait some long seconds that the mouse wakes up and finaly works as expected.

Thanks a lot

Raoul

---

