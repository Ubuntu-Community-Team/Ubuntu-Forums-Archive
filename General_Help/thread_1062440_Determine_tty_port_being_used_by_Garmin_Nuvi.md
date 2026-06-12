---
title: "Determine tty port being used by Garmin Nuvi"
date: 2009-02-06
forum: General Help
---

### Post by heatpumpcontrol on 2009-02-06
I have installed all my Garmin software using this thread.

[Garmin GPS on Ubuntu?!]("http://ubuntuforums.org/showthread.php?t=413438&page=4")
> 
```
 Re: Garmin GPS on Ubuntu?!
I wasted some time figuring out how to get MapSource working with Wine on Hardy.

I am using Wine 1.0RC1

to get MapSource to install I used winetricks...
Code:

$ winetricks corefonts
$ winetricks gecko

To get MapSource to see the GPS, do this, then restart MapSource
Code:

$ sudo modprobe garmin_gps
$ ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

Use dmesg to figure out the exact tty device the garmin was attached to.
```

I am now trying to detect my Nuvi but I just don't know exactly how to go about this. I'm lost here.

> Use dmesg to figure out the exact tty device the garmin was attached to.

I have done dmesg: I've shortened it to show Garmin related stuff only
```
[ 4940.993117] usb-storage: device scan complete
[ 4940.996105] scsi 11:0:0:0: Direct-Access     Garmin   nuvi Flash       1.00 PQ: 0 ANSI: 5
[ 4940.999096] scsi 11:0:0:1: Direct-Access     Garmin   nuvi SD Card     1.00 PQ: 0 ANSI: 5


[ 1910.804682] usbcore: registered new interface driver usbserial
[ 1910.804701] usbserial: USB Serial support registered for generic
[ 1910.804741] usbcore: registered new interface driver usbserial_generic
[ 1910.804743] usbserial: USB Serial Driver core
[ 1910.812169] usbserial: USB Serial support registered for Garmin GPS usb/tty
[ 1910.812223] usbcore: registered new interface driver garmin_gps
[ 1910.812226] garmin_gps: garmin gps driver v0.31
```

lsusb
```
Bus 006 Device 004: ID 091e:22f2 Garmin International 
```

I read here:

[Garmin GPS no longer makes /dev/tty entry]("http://ubuntuforums.org/showpost.php?p=6041812&postcount=6")
> ```
 Re: Garmin GPS no longer makes /dev/tty entry
After digging around a bit more, the solution came crawling towards me.

Code:

sudo nano /etc/modprobe.d/blacklist

Put a # in front of (or remove) the entry garmin_gps
Save and exit

Code:

sudo modprobe garmin_gps

To load the correct garmin driver to use with Mapsource.
Now, to get Mapsource to identify the device all I had to do was
Code:

ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1


```

I've applied those changes separately to no avail.
So currently I'm back to where I've just installed Mapsource. I've deleted the files created by
```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

I even tried changing the 'USB0' to USB1 and the 'com1' to a com2, again to no avail. 

I don't know any of this... Mapsource runs fine in Wine, it's just that I don't know what settings to use to detect my Garmin unit.

please help

hpc

---

