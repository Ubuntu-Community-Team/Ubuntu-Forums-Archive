---
title: "Hardware Identification"
date: 2006-08-25
forum: Desktop Environments
---

### Post by notquitehere188 on 2006-08-25
what can i use to identify the hardware in a computer i recently installed ubuntu on

i am used to using cpu-z and windows control panel to find out what hardware is in a  computer

---

### Post by infoseeker on 2006-08-26
In a terminal type```
lspci
```

---

### Post by amo-ej1 on 2006-08-26
lspci gives you all information of the devices found on the pci bus, the usb equivalent is called lsusb and when you go looking around in the /proc directory you will also find various information (e.g. /proc/cpuinfo for cpu information ) yet another option is to use dmidecode this read the DMI (smbios) information and dumps this to screen. This identifies the hardware as known to bhe tios (not necessary what is acutally there)

---

### Post by v1ct0r on 2006-08-26
[Hardware Lister](http://ezix.org/project/wiki/HardwareLiSter) is pretty good. 

So are the [usbutils...](http://packages.ubuntulinux.org/edgy/utils/usbutils)

---

### Post by tturrisi on 2006-08-26
you can also use lshw to see ALL hardware.

---

