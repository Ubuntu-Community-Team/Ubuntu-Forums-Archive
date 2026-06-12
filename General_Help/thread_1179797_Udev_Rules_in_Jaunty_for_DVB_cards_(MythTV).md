---
title: "Udev Rules in Jaunty for DVB cards (MythTV)"
date: 2009-06-06
forum: General Help
---

### Post by BatPenguin on 2009-06-06
Hello everybody,

I'm having problems re-creating the Udev rules I used in Intrepid for assigning static /dev/dvb/adapterXX devices for my TV cards. This is for Mythtv, since having the device numbers change after reboots causes problems.

This is Jaunty 64-bit, a fresh install. I'm trying to use these rules as /etc/udev/rules.d/10-local.rules:

```
# 
# Adapted from examples found online

# Create a symlink /dev/dvb/adapter101 pointing to DVB-C 0
SUBSYSTEM=="dvb", KERNELS="0000:00:1e.0", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter101/%%s $${K#*.}'", SYMLINK+="%c"

# Create a symlink /dev/dvb/adapter102 pointing to DVB-T
SUBSYSTEM=="dvb", ATTRS{manufacturer}=="Ultima", ATTRS{product}=="ART7070", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter102/%%s $${K#*.}'", SYMLINK+="%c"
 
```

So what I want is to have an adapter /dev/dvb/adapter101 for the DVB-C card and /dev/dvb/adapter102 for the DVB-T. I've tried inserting various identification information for both cards, doesn't seem to work. I'm pretty unsure about what I actuallY SHOULD use there, I've just tried many of these ATTRS infos and such. Here's the output for udevparm:

```
risto@Galactica:/dev/dvb$ udevadm info -q path -n /dev/dvb/adapter1/frontend0 -a

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.2/dvb/dvb1.frontend0':
    KERNEL=="dvb1.frontend0"
    SUBSYSTEM=="dvb"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.2':
    KERNELS=="2-3.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="4201431"
    ATTRS{idVendor}=="05d8"
    ATTRS{idProduct}=="810f"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="4"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Ultima"
    ATTRS{product}=="ART7070"
    ATTRS{serial}=="001"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-3':
    KERNELS=="2-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  2mA"
    ATTRS{urbnum}=="81"
    ATTRS{idVendor}=="050d"
    ATTRS{idProduct}=="0237"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="02"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="7"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="62"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.28-11-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x147b"
    ATTRS{subsystem_device}=="0x1082"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d00002836sv0000147Bsd00001082bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

and the other one: 

```
risto@Galactica:/dev/dvb$ udevadm info -q path -n /dev/dvb/adapter0/frontend0 -a 

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:02:06.0/dvb/dvb0.frontend0':
    KERNEL=="dvb0.frontend0"
    SUBSYSTEM=="dvb"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0/0000:02:06.0':
    KERNELS=="0000:02:06.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="budget_av"
    ATTRS{vendor}=="0x1131"
    ATTRS{device}=="0x7146"
    ATTRS{subsystem_vendor}=="0x1894"
    ATTRS{subsystem_device}=="0x0022"
    ATTRS{class}=="0x048000"
    ATTRS{irq}=="23"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00001131d00007146sv00001894sd00000022bc04sc80i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1e.0':
    KERNELS=="0000:00:1e.0"
    SUBSYSTEMS=="pci"
    DRIVERS==""
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x244e"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{class}=="0x060401"
    ATTRS{irq}=="0"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i01"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Unfortunately I don't have my intrepid rules (which worked fine) saved anywhere but in 8.10 I just took whatever attributes from those lists and it created the links for /dvb/adapter101 etc. just fine with the 10-local.rules file.

Any ideas why this isn't working now or about what info would be good to try to get it to identify these correctely? Thank you.

---

### Post by BatPenguin on 2009-06-06
OK, after countless tries I've finally found a setup that creates the symlinks fine:

```

# Create a symlink /dev/dvb/adapter101 pointing to DVB-C with modalias
SUBSYSTEM=="dvb", ATTRS{modalias}=="pci:v00001131d00007146sv00001894sd00000022bc04sc80i00", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter101/%%s $${K#*.}'", SYMLINK+="%c"

# Create a symlink /dev/dvb/adapter102 pointing to Antec DVB-T with serial 0000:00:1d.7 
SUBSYSTEM=="dvb", ATTRS{serial}=="0000:00:1d.7", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter102/%%s $${K#*.}'", SYMLINK+="%c"
```

There were two problems I noticed: first of all, these information (serial and modalias) were the only ones that seemed to be properly detected - I discovered them by trial and error, one by one. Also, simply restarting udev (/etc/init.d/udev restart) was not enough to get it to create the links so I had to actually reboot the machine many times to get this to work.

In any case, marking this as solved. Hope it helps someone.

---

