---
title: "Palm Zire72"
date: 2005-05-04
forum: Desktop Environments
---

### Post by swalsh on 2005-05-04
So I have read everything about this topic but have found no luck.  Anyone know how to sync with K-Pilot, J-Pilot, anything but gnome pilot?  I run Kubuntu Hedehog and have everything working except my palm  :???: I've been at it for 3 days and I'm getting tired of reading and typing to no avail (or syncing).

---

### Post by praekon on 2005-05-04
Hi!
What's the problem?
I don't try it yet to install my Zire72 unter Kubuntu now.
But i was sucessfull under FC3.
First you need hal-device-manager for cheking the symlinks and other info.

Gnome-pilot has problems with the new palmOne PDA's.
You have to update the device file from gnome-pilot with the identitie of the zire.
i wrote down how to do that in a german fedora forum.
Have to look and translate first :)

greets
praekon

---

### Post by swalsh on 2005-05-04
I have tailed the USB log and my comptuer recognizes my palm when I press the Hotsync button, but neither KPilot or JPilot realize what's going on.  Both programs just sit there and act like nothing is happening.

---

### Post by praekon on 2005-05-05
OK, first install hal-device-manager
'apt-get install hal-device-manager'

start it and press the hotsync button on your palm.
Note the following Infos from HAL D Manager:

usb.product
usb.product_id
usb.vendor_id

Then you have to write a UDEV Rule in /etc/udev/rules.d/
filename like 10-custom.rules

fill in this text (in one line):

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

SYSFS{product} is the Info from usb.product

Now the Palm will be linked on /dev/pilot (default in KPilot, Gnome-pilot etc.) instead of /dev/ttyUSB0 and /dev/ttyUSB1.

KPilot should be working now.
If you want to use Gnome-pilot (GUI for pilot-xfer
) you have to change the Gnome-pilot device file /usr/share/gnome-pilot/devices.xml.
This file have no Device Informations (March 2005) for Palm Zire72 and T5.

On EOF enter this:

<!-- Palm Zire72 / T5 -->
<device vendor_id="0830" product_id="0061" />

device vendor_id is usb.vendor_id form HAL D and product_id is usb.product_id.
Save finish (hopefully  ;-)  ).
Oh, with Gome-pilot you have to start HotSync 2 times. Gnome-pilot will not react  on the first try.

greets
praekon

---

### Post by swalsh on 2005-05-05
I vote for Sticky.  No one else has put this so easily.  I followed directions and had no problems syncing up with KPilot.  Thanks a lot!

---

### Post by abowman on 2005-05-08
I agree.

---

### Post by amckenzie on 2006-01-20
Thanks praekon!  I've been trying to get my Zire31 to sync to ANYTHING but windows (SuSE, FreeBSD, even Mac OS X didn't work correctly...) for about 5 months, now.

Your instructions finally did it... thanks again!

---

