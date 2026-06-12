---
title: "gpsd with sirf-iii globalsat br-355 and ubuntu linux (breezy)"
date: 2005-12-08
forum: General Help
---

### Post by sporto on 2005-12-08
Hi All,

I am trying to get my new br-355 working with Breezy.I have the br-355 serial version that terminates with a ps2 connector. I bought some seperate cables, one that finishes in rj-11 to connect to my ipaq dock, and one that finishes with USB and has a prolific pl-2303 in a little box inline in the cable. It appears to detect ok when plugged in, dmesg shows this:

[4301846.762000] usb 2-1: new full speed USB device using uhci_hcd and address 6[4301846.861000] pl2303 2-1:1.0: PL-2303 converter detected
[4301846.865000] usb 2-1: PL-2303 converter now attached to ttyUSB0

To get it working I then do..

killall gpsd

(to kill the one that started with the hotlplug, haven't looked into how to turn this off)

then I do..

chmod a+rw /dev/ttyUSB0

then I run gpsd

gpsd -N -n -D 2 /dev/ttyUSB0

When I run xgps, I get fast switching between 2D and 3D lock. In windows or on my ipaq I get a consisten 3D lock reported.

I get the debug output...

which is long list of these:

9571: arguments to dbus_message_iter_append_basic() were incorrect, assertion "real->iter_type == DBUS_MESSAGE_ITER_TYPE_WRITER" failed in file dbus-message.c line 2125.
This is normally a bug in some application using the D-BUS library.

with the odd correct gps sentence every 20 or so of the above..

the sentences look like this which I presume is not erroneous..

gpsd: <= GPS: $GPRMC,122011.000,A,5328.5647,N,00214.1589,W,4.25,335.17,081205,,*10

I am using gpsd that is in the ubuntu repositories and was installed with apt. The version is 2.28.

Can you help me?

Thanks in advance,
Bear.

---

### Post by ranf on 2005-12-08
[QUOTE=sporto]
then I run gpsd

gpsd -N -n -D 2 /dev/ttyUSB0
[/QUOTE]
I can't find a `-N' in the man page. What is this good for?

And you didn't use the `-p' for the GPS device name.

---

### Post by sporto on 2005-12-08
hi,

-N is to run in foreground, not daemonize, this lets you see any problems, i.e. the errors I get.

-f is gps device name, but this option is depreciated, so I don't try to use it.

---

### Post by ranf on 2005-12-08
This option looks promising:
```
  -K           [ keep gps device open all the time (linux USB workaround) ]

```

---

### Post by sporto on 2005-12-08
what manpage are you reading?

-K isn't an a valid option....


thanks.

---

### Post by ranf on 2005-12-08
[QUOTE=sporto]what manpage are you reading?
-K isn't an a valid option....
[/QUOTE]
The one installed on my Ubuntu 5.10 box. That -K option is not in it but shown when I run:

gpsd -?

---

### Post by sporto on 2005-12-08
not shown and not an option here, not in the manpage, or the docs on the gpsd website..

i'm using the sources.list from [www.psychocats.net/linux/sources.php](www.psychocats.net/linux/sources.php) , which one are you using?

my gpsd version is 2.28 , 2.3 is the latest but this isn't available with apt yet.

i've had no problems getting gpsd to work in the past with other gps units.. hmm

---

### Post by ranf on 2005-12-08
Oops, sorry for the confusion.
Synaptic says gpsd is not installed.
"dpkg -l gpsd" says the same.
But I still have gpsd in the path:
```

ranf@schlepp:~ $ which gpsd
/usr/bin/gpsd
ranf@schlepp:~ $ ls -la `which gpsd`
-rwxr-xr-x  1 root root 26264 2004-08-13 20:55 /usr/bin/gpsd*

```
Hmm looks a bit old. I upgraded this box from Warty over Hoary to Breezy.

---

### Post by ranf on 2005-12-08
So to post something helpful at last. 
At the hardware page:
[http://gpsd.berlios.de/hardware.html](http://gpsd.berlios.de/hardware.html)

only lists a:
- BU-353
- with SiRFstarIII + PL2303

---

### Post by sporto on 2005-12-08
the list can be largely ignored as gpsd should work with anything that outputs nmea-0183, but it also supports other protocols e.g. sirf/garmin (some of these manf's products can output in both). And.. the list lists only what has been tested, which isn't very much as the authors cannot get hold of every gps - and not many people submit reports for the list, but actually the vast majority of gps's will work with gpsd...

as far as gpsd is concerned, most things sirf-iii based will appear to be the same thing..so if the 353 works...

i suspect this is a problem with the breezy package and d-bus being specified when it was compiled... and... hmm....

but it should be fixable.

---

### Post by sporto on 2005-12-12
bump.

---

### Post by treegezer on 2006-02-15
Same issue with the  US Gloab Sat BU-353. Anyone know of a fix?

---

