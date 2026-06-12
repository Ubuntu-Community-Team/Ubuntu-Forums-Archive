---
title: "HOWTO: Garmin Oregon 400t &amp; GPSMap 60CSx interfacing"
date: 2008-12-27
forum: General Help
---

### Post by tescott on 2008-12-27
Just thought I'd post in case anyone else ran into the same issues as me.  Being a Ubuntu newb, I ran into trouble getting my Oregon 400t up and reporting positional information.  The steps I took to get my GPSMap 60Csx got me pointed in the right direction:

GPSMap 60CSx

1) Install gpsd using the System > Administration > Synaptic Package Manager
2) Perform a 'sudo modprobe garmin_gps'.  This will create /dev/ttyUSB0 when the device is connected.
3) Perform a 'sudo mount -t usbfs none /proc/bus/usb'.  This is needed by gpsd.
4) Set the 60CSx to "Text Out".  (I set the baud rate for 9600 also.  I haven't experimented to see if this is even required.)
5) Connect the 60CSx to the USB port.
6) Get gpsd running: 'sudo gspd /dev/ttyUSB0'.
7) Verify it is operating by running 'xgps'.  You should see satellite information confirming incoming data is working.

Oregon 400t

For whatever reason, I couldn't follow the same steps for my Garmin Oregon 400t.  Read on for those (might also apply to the Garmin Colorado).

1) Install gpsd using the System > Administration > Synaptic Package Manager
1a) Download, build, and install garminusb2nmea.  This can be downloaded from Sourceforge: [http://sourceforge.net/project/showfiles.php?group_id=115375](http://sourceforge.net/project/showfiles.php?group_id=115375)
2) Perform a 'sudo modprobe garmin_gps'.  This will create /dev/ttyUSB0 when the device is connected.
3) Perform a 'sudo mount -t usbfs none /proc/bus/usb'.  This is needed by gpsd.
4) Set the Oregon to "Garmin Spanner" mode.  Use the defaults.
5) Connect the Oregon to the USB port.
6) Follow the instructions in garminusb2nmea: 'mkfifo /tmp/gps', followed by 'garminusb2nmea /dev/ttyUSB0 /tmp/gps'.
7) The README further states to use '-K' to allow gpsd to read from the pipe.  In version 2.37, this option is not present.  Instead, you can just do a 'gpsd -n /tmp/gps'.
8) Use xgps to verify that incoming data is working.

One observation I've made is that sometimes incoming data quits.  To correct, unplug the gps, then plug it in again, and then fire up garminusb2nmea/gpsd again.  Sometimes this corrects the problem, sometimes it doesn't.  So, repeat until you get things going.  Not a very good answer, but at least it gets you up and running. :P

Hope this helps!
--tim

---

### Post by tescott on 2008-12-27
Just to clarify, this will get you going as far as being able to read NMEA positional data from the GPS receiver via gpsd.  For getting MapSource, etc. running, you may want to take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=413438](http://ubuntuforums.org/showthread.php?t=413438)

--tim

---

