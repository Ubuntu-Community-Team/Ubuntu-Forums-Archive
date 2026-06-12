---
title: "Trying to get USB to work"
date: 2005-08-16
forum: Desktop Environments
---

### Post by grakker on 2005-08-16
Could someone with a system close to mine post their .config and /etc/udev/rules.d/udev.rules for me to compare.  I've reinstalled a couple of times on a spare partition and usb just doesn't work for me.  Either my Visor (yes, have the module loaded) nor my stick.  Nothing.  No activity in my logs, etc..  Knoppix shows everything, so I know that it's not my hardware, just my lameness.

Anyway, here's my deal:

SATA drive (So sda is not for usb stuff...)
Athlon64 w/1GB RAM
ATI Radeon 7000  (yep, I'm no gamer)
Realtek network, blah, blah

Not sure if it matters, but here is an excerpt from dmesg:

usb usb1: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: nVidia Corporation CK804 USB Controller
usb usb1: Manufacturer: Linux 2.6.12.3-hopethiseffinworks ehci_hcd  *<---- it didn't* 
usb usb1: SerialNumber: 0000:00:02.1
usb usb1: hotplug
usb usb1: adding 1-0:1.0 (config #1, interface 0)


Anyways, again, if someone could post a .config which actually works for them, I would appreciate it.  And maybe your udev.rules.  And if you really want to be nice, let me know how it works for you (ie, are you using Gnome?  Are you manually mounting?)  OR, just point me to a page which shows me how to trouble shoot this stuff, I've found a bunch of pages which skirt the problem.  If I was getting something in my logs I'm sure I could figure it out.

I seriously don't want to have to install from KNOPPIX, but I really need to get this working.  My son is getting tired of me mounting a folder on his M$ box and walking into his room all the time to copy to and from my stick.

Thanks.

---

### Post by ACK!! on 2005-08-16
[QUOTE=grakker]Could someone with a system close to mine post their .config and /etc/udev/rules.d/udev.rules for me to compare.  I've reinstalled a couple of times on a spare partition and usb just doesn't work for me.  Either my Visor (yes, have the module loaded) nor my stick.  Nothing.  No activity in my logs, etc..  Knoppix shows everything, so I know that it's not my hardware, just my lameness.

.....[/QUOTE]

# USB devices
BUS="usb", KERNEL="hiddev*",    NAME="usb/%k"
BUS="usb", KERNEL="auer*",      NAME="usb/%k"
BUS="usb", KERNEL="legousbtower*", NAME="usb/%k"
BUS="usb", KERNEL="dabusb*",    NAME="usb/%k"
BUS="usb", KERNEL="lp[0-9]*",   NAME="usb/%k"
BUS="usb", KERNEL="cpad[0-9]*", NAME="usb/%k"

That is all I got.  Both my ipod and my digital camera and a colleagues stick all work flawlessly.

---

### Post by grakker on 2005-08-16
[QUOTE=ACK!!]# USB devices
BUS="usb", KERNEL="hiddev*",    NAME="usb/%k"
BUS="usb", KERNEL="auer*",      NAME="usb/%k"
BUS="usb", KERNEL="legousbtower*", NAME="usb/%k"
BUS="usb", KERNEL="dabusb*",    NAME="usb/%k"
BUS="usb", KERNEL="lp[0-9]*",   NAME="usb/%k"
BUS="usb", KERNEL="cpad[0-9]*", NAME="usb/%k"
[/QUOTE]

Thanks.  I think that is the default for udev.rules.  Which is fine, as soon as I (if..) get this cleared up I need to go in there and clean out how many freaking entries are in /dev.

Here is some of my .config file looks like:
```

dominion:/usr/src/linux-2.6.12.3$ zcat /proc/config.gz | grep USB | grep -v ^#
CONFIG_USBPCWATCHDOG=m
CONFIG_VIDEO_CPIA_USB=m
CONFIG_SND_USB_AUDIO=m
CONFIG_SND_USB_USX2Y=m
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB=y
CONFIG_USB_DEBUG=y
CONFIG_USB_DEVICEFS=y
CONFIG_USB_BANDWIDTH=y
CONFIG_USB_EHCI_HCD=y
CONFIG_USB_EHCI_SPLIT_ISO=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_OHCI_HCD=y
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=y
CONFIG_USB_SL811_HCD=m
CONFIG_USB_PRINTER=y
CONFIG_USB_STORAGE=y
CONFIG_USB_STORAGE_DATAFAB=y
CONFIG_USB_STORAGE_FREECOM=y
CONFIG_USB_STORAGE_ISD200=y
CONFIG_USB_STORAGE_DPCM=y
CONFIG_USB_STORAGE_SDDR09=y
CONFIG_USB_STORAGE_SDDR55=y
CONFIG_USB_STORAGE_JUMPSHOT=y
CONFIG_USB_KBD=m
CONFIG_USB_MOUSE=m
CONFIG_USB_CATC=m
CONFIG_USB_KAWETH=m
CONFIG_USB_PEGASUS=m
CONFIG_USB_RTL8150=m
CONFIG_USB_USBNET=m
CONFIG_USB_ALI_M5632=y
CONFIG_USB_AN2720=y
CONFIG_USB_BELKIN=y
CONFIG_USB_GENESYS=y
CONFIG_USB_NET1080=y
CONFIG_USB_PL2301=y
CONFIG_USB_KC2190=y
CONFIG_USB_ARMLINUX=y
CONFIG_USB_EPSON2888=y
CONFIG_USB_ZAURUS=y
CONFIG_USB_CDCETHER=y
CONFIG_USB_AX8817X=y
CONFIG_USB_MON=y
CONFIG_USB_SERIAL=y
CONFIG_USB_SERIAL_GENERIC=y
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_PL2303=m

```

A lot of default crap in their that I need to clean out, but can someone run the same command and let me know what I'm missing?  If you don't have /proc/config.gz, just run it on your /boot/config-WHATEVER.  And drop the z on the zcat.

---

