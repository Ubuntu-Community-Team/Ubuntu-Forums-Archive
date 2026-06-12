---
title: "/dev/video*"
date: 2009-01-23
forum: General Help
---

### Post by tonyuk123 on 2009-01-23
Have posted this on another thread but the thread is titled {solved}etc
so noone seems to be answering

Trying to get my aiptek pencam working

tried the command 'lsusb' 
here are the results 

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 03f0:b802 Hewlett-Packard Photosmart 7400 Series
Bus 003 Device 005: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

seems it thinks it is an Aiptek PenCam, good start i guess.
When you use the /dev/video*
where * is a number (i think it is 0 (zero)on mine) 
how does that relate to the info above.
I notice the webcam is on Bus001 device 002
should the software be set to look for /dev/video2 ?
Is this is my problem?
Or am i getting this all wrong?

---

### Post by fragos on 2009-01-23
The problem is that there are multiple devices, tv cards and web cams, that will be /dev/video{#} and there's no way to insure that the same # is used every time the system boots. You can however fix this with udev rules as follows:

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

### Post by tonyuk123 on 2009-01-24
Thanks for your help, although i have found something else going on.
Seems that my cam works in CHEESE
but not in amsn or gyachi
They just say error while capturing initial image.
I assume if it works in one program the driver is ok?

I have found i only have /dev/video0 on my system as i only have one cam, so i guess video0 is fine and wont move (at least for now) when booted up.

Tony

---

### Post by fragos on 2009-01-24
It may be an application issue. there are also differences between v4L and v4L2. Some software is good at adapting to what ever configuration you have and other need a lot more or different configuration setup.

---

### Post by tonyuk123 on 2009-01-24
how do i know which i am using or should be using?

v4L or v4L2?

i have read a few threads where people have got an aiptek pencam working, but some seem to say it just worked or it didn't
never really seen any solution that works for me?!

any help is much appreciated

Tony

---

### Post by fragos on 2009-01-24
Focus your search for a solution on the application you're trying to use aaand how to get webcams to work with it. You may find that although MSN supports video the Linux based application you're using doesn't. Microsoft isn't very forthcoming with any documentation that will help a Linux application work with MS products.

---

### Post by lwnexgen2 on 2009-01-28
There's a program called gstfakevideo that will work to convert between colorspaces (v4l and v4l2s) by piping the webcam output to gstreamer and letting gstreamer do the conversions, and output to a second, fake webcam. 

People have had some success getting it to work with Skype, though no guarantees with your software.

Good luck!

---

