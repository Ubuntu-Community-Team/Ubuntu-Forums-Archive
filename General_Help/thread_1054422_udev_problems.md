---
title: "udev problems"
date: 2009-01-29
forum: General Help
---

### Post by dread22 on 2009-01-29
Hi,

I need a udev rule which always links to the correct device when it is plugged in. The device gets labled under /dev/ttyUSB%n so I cannot use it directly and needed a constant name which my programs can call upon.
What I did was write a rule
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v12D1p1003d0000dc00dsc00dp00icFFiscFFipFF", ATTRS{bInterfaceNumber}=="00", SYMLINK+="3Gmodem", ENV{GENERATED}="1"
which is supposed to create a symbolic link to the device upon creation name /dev/3Gmodem. What's happening however is when i plug it in for the first time everything works perfectly, '/dev/ttyUSB0' is created and '/dev/3Gmodem -> /dev/ttyUSB0' is created too, and once unplugged both dissapear. The problems arise when I plug it in the next time '/dev/ttyUSB0' is created but this time '/dev/3Gmodem -> usbdev2.08_eps01' with the 2.08 changing to a new value each time I replug the device.

Anyone know how I can solve this problem so the device it gets pointed to is correct?
Cheers

---

### Post by fragos on 2009-01-29
If you reference /dev/3Gmodem don't you get the correct device? The mount point automatically selected by the system isn't important if you configure apps to use /dev/3Gmodem.

---

### Post by dread22 on 2009-01-29
Yeah but once the mount point is still /dev/ttyUSB0 except the symbolic link points somewhere else '/dev/3Gmodem -> usbdev2.08_eps01' which is causing the problems. My programs cannot use the 3Gmodem link anymore but they can use the /dev/ttyUSB0 link, I just don't understand why the pointer keeps shifting to a new location when the real mount point (/dev/ttyUSB0) exists.
This is an issue for me because I have other devices which use the tty link and I can't guarentee that the modem will be assigned ttyUSB0.

---

### Post by fragos on 2009-01-29
My experience with udev relates to /dev/video# devices for example TV cards and webcams all mount as video#. Problem is the assignment of # various between boots. To fix that I used udev to also assign specific device names based on the actual hardware. Variable video# problem went away by configuring aps to use my speciic device names. In my case I had two video cards and a USB webcam. My notes on solving the problem for my TV cards follows:

&#65279;To get the device info for my cards, I used the following udevinfo commands:
Code:
udevinfo -a -p $(udevinfo -q path -n /dev/video0)
udevinfo -a -p $(udevinfo -q path -n /dev/video1)

fragos@Geo:~$ udevinfo -a -p $(udevinfo -q path -n /dev/video0) 

Udevinfo starts with the device specified by the devpath and then 
walks up the chain of parent devices. It prints for every device 
found, all possible attributes in the udev rules key format. 
A rule to match, can be composed by the attributes of the device 
and the attributes from one single parent device. 

  looking at device '/class/video4linux/video0': 
    KERNEL=="video0" 
    SUBSYSTEM=="video4linux" 
    DRIVER=="" 
    ATTR{card}=="10" 
    ATTR{name}=="BT878 video _Hauppauge _bt878__" 
    ATTR{dev}=="81:0" 

  looking at parent device '/devices/pci0000:00/0000:00:0a.0': 
    KERNELS=="0000:00:0a.0" 
    SUBSYSTEMS=="pci" 
    DRIVERS=="bttv" 
    ATTRS{msi_bus}=="" 
    ATTRS{broken_parity_status}=="0" 
    ATTRS{modalias}=="pci:v0000109Ed0000036Esv00000070sd000013EBbc04sc00i00" 
    ATTRS{local_cpus}=="ff" 
    ATTRS{irq}=="19" 
    ATTRS{class}=="0x040000" 
    ATTRS{subsystem_device}=="0x13eb" 
    ATTRS{subsystem_vendor}=="0x0070" 
    ATTRS{device}=="0x036e" 
    ATTRS{vendor}=="0x109e" 

  looking at parent device '/devices/pci0000:00': 
    KERNELS=="pci0000:00" 
    SUBSYSTEMS=="" 
    DRIVERS=="" 

fragos@Geo:~$ udevinfo -a -p $(udevinfo -q path -n /dev/video1) 

Udevinfo starts with the device specified by the devpath and then 
walks up the chain of parent devices. It prints for every device 
found, all possible attributes in the udev rules key format. 
A rule to match, can be composed by the attributes of the device 
and the attributes from one single parent device. 

  looking at device '/class/video4linux/video1': 
    KERNEL=="video1" 
    SUBSYSTEM=="video4linux" 
    DRIVER=="" 
    ATTR{name}=="ivtv0 encoder MPEG" 
    ATTR{dev}=="81:1" 

  looking at parent device '/devices/pci0000:00/0000:00:0b.0': 
    KERNELS=="0000:00:0b.0" 
    SUBSYSTEMS=="pci" 
    DRIVERS=="ivtv" 
    ATTRS{msi_bus}=="" 
    ATTRS{broken_parity_status}=="0" 
    ATTRS{modalias}=="pci:v00004444d00000016sv00000070sd00008801bc04sc00i00" 
    ATTRS{local_cpus}=="ff" 
    ATTRS{irq}=="20" 
    ATTRS{class}=="0x040000" 
    ATTRS{subsystem_device}=="0x8801" 
    ATTRS{subsystem_vendor}=="0x0070" 
    ATTRS{device}=="0x0016" 
    ATTRS{vendor}=="0x4444" 

  looking at parent device '/devices/pci0000:00': 
    KERNELS=="pci0000:00" 
    SUBSYSTEMS=="" 
    DRIVERS=="" 

fragos@Geo:~$ 

Since the Hauppauge includes multiple devices, video0, video24, and video32, I had to use the name of the proper device to get the proper mapping.

My final /etc/udev/rules.d/95-perso.rules file is:
Code:
KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr150"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
This results in the following symlinks:
Code:
/dev/video/pvr150
/dev/video/bttv

---

### Post by dread22 on 2009-01-29
Thanks for you help. Figured out what was wrong with it. Another device was being created as a child in the device I needed to connect to. I just added
SUBSYSTEM=="tty"
into my udev script forcing it to connect to the device I wanted and it is able to detect the correct device now.:D

---

