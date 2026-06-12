---
title: "Wacom Bamboo Tablet is not working in ubuntu"
date: 2018-10-25
forum: Desktop Environments
---

### Post by jamautry on 2018-10-25
[FONT=arial][COLOR=#000000]I am having the same issue as a poster back in May.  Ubuntu sees the [/COLOR][/FONT][COLOR=#000000][FONT=arial]usb[/FONT][/COLOR][FONT=arial][COLOR=#000000] device but doesn't recognize it as an input device.  The screenshots below show my results when checking for the device and drivers.  Does anyone have any suggestions?  I am relatively new to Linux and Ubuntu.  Thanks in advance.[/COLOR][/FONT]

[COLOR=#000000]Code:
$ uname -r
4.15.0-22-generic[/COLOR]
[COLOR=#000000]Code:
$ lsusb | grep Wacom
Bus 001 Device 006: ID 056a:037a Wacom Co., Ltd[/COLOR]
[COLOR=#000000]Code:
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB OPTICAL MOUSE                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Synaptics TM3336-001                        id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; EasyCamera: EasyCamera                      id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)][/COLOR]
[COLOR=#000000]Code:
$ xsetwacom --list devices[/COLOR]
[COLOR=#000000](returns nothing)[/COLOR]

[COLOR=#000000]Code:
$ lsmod | grep wacom
wacom                 106496  0
usbhid                 49152  1 wacom
hid                   118784  5 i2c_hid,hid_generic,usbhid,hid_rmi,wacom[/COLOR]
[COLOR=#000000]Code:
$ apt list libwacom2
Listing... Pronto
libwacom2/bionic,now 0.29-1 amd64 [installed]

$ apt list libwacom-common
Listing... Pronto
libwacom-common/bionic,bionic,now 0.29-1 all [installed]

$ apt list xserver-xorg-input-wacom
Listing... Pronto
xserver-xorg-input-wacom/bionic,now 1:0.36.1-0ubuntu1 amd64 [installed][/COLOR]

---

