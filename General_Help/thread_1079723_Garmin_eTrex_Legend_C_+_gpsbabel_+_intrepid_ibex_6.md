---
title: "Garmin eTrex Legend C + gpsbabel + intrepid ibex 64"
date: 2009-02-24
forum: General Help
---

### Post by sinukas on 2009-02-24
Hello! I am trying (without luck) to download routes from my Garmin eTrex Legend C using gpsbabel. I am running Ubuntu 8.10 64-bit.

When I connect my GPS unit the syslog says:
Feb 24 17:46:48 catawba kernel: [33208.800013] usb 5-2: new full speed USB device using uhci_hcd and address 2
Feb 24 17:46:49 catawba kernel: [33208.951021] usb 5-2: configuration #1 chosen from 1 choice

To download routes I use:
will@catawba:~/gps_down$ gpsbabel -t -i garmin -f usb:0 -o gpx -F upper-kestral.gpx

It returns:
usb_set_configuration failed, probably because kernel driver ''
 is blocking our access to the USB device.
For more information see [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

The page provided does not list any solutions for getting Intrepid Ibex to work. Has anyone gotten a eTrex Legend to work on Intrepid Ibex to work? and if so, how/what did you do to get your USB drivers to work? What should be my next step for troubleshooting this?

Thanks in advance

---

### Post by _march_ on 2009-05-11
Hi :)

I'm running a Garmin eTrex Legend HCx with Ubuntu 32bit. Create **/etc/udev/rules.d/51-garmin.rules** with the following content:

```

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666"

```
After you plugged in your device again you can fetch the desired via gpsbabel. Also read [here](http://translate.google.com/translate?js=n&prev=_t&hl=de&ie=UTF-8&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FGarmin_eTrex_Serie&sl=de&tl=en&history_state0=&swap=1).

---

### Post by sinukas on 2009-05-11
Thank you!!!

---

### Post by toddwbucy on 2009-05-14
I had a similar problem with an older Garmin rino 520.  I fixed it in only seven easy step :-)

1. make sure you have libusb-1.0-0 and libusb-dev installed
2. unblacklist the garmin_usb driver in /etc/modprobe.d/blacklist.conf
3. modprobe garmin_usb
4. sudo mount -t usbfs none /proc/bus/usb
5. plug in the garmin gps reciever
6. run gpsd: sudo gpsd -F /var/run/gpsd.sock /dev/ttyUSB0
7 should work use xgps to test for data

worked like magic.  of course I have to do step 4 every time I boot up but that is fixed with a simple script.

that said the previous post is a much more efficient way to solve the problem

todd

Todd

---

