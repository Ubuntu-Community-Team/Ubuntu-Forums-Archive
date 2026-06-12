---
title: "quick usb tty help"
date: 2009-02-07
forum: General Help
---

### Post by heatpumpcontrol on 2009-02-07
using
dmesg | grep -i garmin 

I get the following:
```
[   74.660665] scsi 9:0:0:0: Direct-Access     Garmin   nuvi Flash       1.00 PQ: 0 ANSI: 5
[   74.663610] scsi 9:0:0:1: Direct-Access     Garmin   nuvi SD Card     1.00 PQ: 0 ANSI: 5
[  640.284080] scsi 10:0:0:0: Direct-Access     Garmin   nuvi Flash       1.00 PQ: 0 ANSI: 5
[  640.287080] scsi 10:0:0:1: Direct-Access     Garmin   nuvi SD Card     1.00 PQ: 0 ANSI: 5
[  867.745829] usbserial: USB Serial support registered for Garmin GPS usb/tty
[  867.746509] usbcore: registered new interface driver garmin_gps
[  867.746513] garmin_gps: garmin gps driver v0.31

```

so if I want to create a simlink what should I enter in the "?" in the command below?

```
ln -s /dev/ttyUSB[COLOR="Red"]?[/COLOR] ~/.wine/dosdevices/com[COLOR="Red"]?[/COLOR]
```

or should this be another code?

---

### Post by funkyFlash on 2009-02-07
I can't say I've ever dealt with GPS devices and their placement as ttyUSB devices.  I do, however, use a usb to serial adapter for configuring switches and what not (stupid mac book pro...)

I take it there isn't an obvious device node corresponding to the garmin?  Do you have anything else that shows up as a ttyUSB device?

---

### Post by heatpumpcontrol on 2009-02-07
> **funkyFlash said:**
> I can't say I've ever dealt with GPS devices and their placement as ttyUSB devices.  I do, however, use a usb to serial adapter for configuring switches and what not (stupid mac book pro...)

I take it there isn't an obvious device node corresponding to the garmin?  Do you have anything else that shows up as a ttyUSB device?

Only this under 
dmesg | grep -i tty
```
dmesg | grep -i tty
[    0.004000] console [tty0] enabled
[    1.353553] tty ptys5: hash matches
[  867.745829] usbserial: USB Serial support registered for Garmin GPS usb/tty
[ 5395.516789] SLIP: version 0.8.4-NET3.019-NEWTTY (dynamic channels, max=256) (6 bit encapsulation enabled).
[ 8223.105286] usbserial: USB Serial deregistering driver Garmin GPS usb/tty

```

---

### Post by funkyFlash on 2009-02-07
What do you get for ```
ls /dev/ttyUSB*
```?

---

### Post by heatpumpcontrol on 2009-02-08
Sorry went to bed.

ls /dev/ttyUSB*

```
ls: cannot access /dev/ttyUSB*: No such file or directory

```

---

