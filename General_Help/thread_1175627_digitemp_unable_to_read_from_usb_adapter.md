---
title: "digitemp unable to read from usb adapter"
date: 2009-06-01
forum: General Help
---

### Post by mike4ubuntu on 2009-06-01
Has anybody been able to get digitemp working with a DS2490 USB to 1-wire adapter in Jaunty, or any other release for that matter?

```

$ digitemp_DS2490 -w
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 001/006
could not set config 1: Operation not permitted
USB ERROR: Failed to set configuration

$ sudo digitemp_DS2490 -w
[sudo] password for mike:
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 001/006
could not set config 1: Device or resource busy
USB ERROR: Failed to set configuration

$ sudo digitemp_DS2490 -i -s/dev/bus/usb/001/006
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 001/006
USB ERROR: owAcquire called with invalid port string

$ sudo chmod 777 /dev/bus/usb/001/006

$ ll /dev/bus/usb/001/006
0 crwxrwxrwx 1 root root 189, 5 2009-05-19 17:35 /dev/bus/usb/001/006

$ sudo digitemp_DS2490 -i -s/dev/bus/usb/001/006
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 001/006
USB ERROR: owAcquire called with invalid port string

```

---

### Post by MickSulley on 2009-08-25
Did you make any progress with this?  I have the same problem.
Cheers

---

### Post by Lowgrey on 2009-10-18
try:

sudo digitemp_DS2490 -i -sUSB

this worked for me...

---

### Post by sbudd on 2009-10-22
> **MickSulley said:**
> Did you make any progress with this? I have the same problem.
Cheers
 This particular digitemp usb club is growing....still trying
regards
SteveBudd

---

### Post by mike4ubuntu on 2009-11-13
Yes, this has finally worked for me in Karmic.

seems like for now you have to:

```
sudo modprobe -r ds2490
```

then

# to setup automatically for next time you reboot
```

sudo gedit /etc/modprobe.d/blacklist.conf
=at bottom=>
#To get digitemp to work
blacklist ds2490

```

```

sudo digitemp_DS2490 -q -a -o "%F" -i
Found DS2490 device #1 at 001/009
10B3CB4D01080057 : DS1820/DS18S20/DS1920 Temperature Sensor
ROM #0 : 10B3CB4D01080057
68.562500

```

It's not clear to me yet how you specify individual devices with the -s option, but this seems to work

```

sudo digitemp_DS2490 -q -a -o "%F" -i -sUSB
Found DS2490 device #1 at 001/009
10B3CB4D01080057 : DS1820/DS18S20/DS1920 Temperature Sensor
ROM #0 : 10B3CB4D01080057
68.562500

```

---

### Post by MickSulley on 2009-11-13
Yes I did get the USB device to work, but it was far from reliable.  I could send the initialise command 6 or 8 times before it worked.  I contacted Brian Lane, the guy that wrote Digitemp, and he said that he could not get USB devices to work reliably, so I bought a serial device (DS9097U) and that works fine.

---

### Post by sbudd on 2009-11-23
One small step for man....DS2490

I followed Mike's instructions and I have readings, (185 but I can fix that). In any case, the software fix worked on a USB9490R.It takes al little patience for a newbie.

Many thanks.
Steve
;)

---

### Post by mike4ubuntu on 2010-08-09
well, as best I can tell, this is broken again in Lucid.  This gets a little frustrating, from release to release, when working stuffs gets broken again.

```

$ sudo modprobe -r ds2490
$ sudo digitemp_DS2490 -q -a -o "%F" -i
Found DS2490 device #1 at 001/005

```

but that's it.  It won't return the temperature anymore.

---

### Post by scanman717 on 2010-08-09
I'm right there with you...  Get Found DS2490 device #1 at 001/005 and nothing else... grrrr...

---

### Post by baetmaen on 2010-08-14
Hi,

I have exactly the same problem with lucid amd64.

When I connect my DS9490R (USB), the following appears in dmesg:
```
[707129.680060] usb 2-1.4: new full speed USB device using ehci_hcd and address 19
[707129.790825] usb 2-1.4: configuration #1 chosen from 1 choice
[707131.336563] w1_master_driver w1 bus master: Family 10 for 10.000801e6040a.b6 is not registered.
[707132.880680] w1_master_driver w1 bus master: Family 10 for 10.000801e5ff89.5b is not registered.
```When I try to run "sudo digitemp_DS2490 -w" I get:
```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 002/019
could not set config 1: Device or resource busy
USB ERROR: Failed to set configuration
```After removing the module ds2490 (which was auto loaded after pluging the device):
```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 002/019
Turning off all DS2409 Couplers
.
Devices on the Main LAN
```I tried the GetTemps.exe from the SdK on Win7 and this one gives me (with two Temp sensors in place):
```
1-Wire List:
==========================

Address = B6000801E6040A10
Name = DS1920
Description = Digital thermometer measures temperatures from -55C to 100C in typically 0.2 seconds.  +/- 0.5C Accuracy between 0C and 70C. 0.5C standard resolution, higher resolution through interpolation.  Contains high and low temperature set points for generation of alarm.
Temperature = 22,5 °C

Address = 5B000801E5FF8910
Name = DS1920
Description = Digital thermometer measures temperatures from -55C to 100C in typically 0.2 seconds.  +/- 0.5C Accuracy between 0C and 70C. 0.5C standard resolution, higher resolution through interpolation.  Contains high and low temperature set points for generation of alarm.
Temperature = 22 °C
```Any ideas ?

Regards
Joerg

---

### Post by scanman717 on 2010-08-15
Joerg, 

After I did the Modprobe and edited the blacklist.conf I had the same problem, but a reboot of the system and it works great now.

I use this command: ./digitemp_DS2490 -i -d 5 -n 0

I also found this page to be helpful for me, I know it is the wrong platform, but nevertheless provided good info: [http://www.nslu2-linux.org/wiki/HowTo/AddUSBOneWireAdapter](http://www.nslu2-linux.org/wiki/HowTo/AddUSBOneWireAdapter)

---

### Post by baetmaen on 2010-08-16
> **scanman717 said:**
> I use this command: ./digitemp_DS2490 -i -d 5 -n 0
When I try your command it starts searching but nothing happens afterwards.

```
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 002/007
Turning off all DS2409 Couplers
.
Searching the 1-Wire LAN
^C
```

> I also found this page to be helpful for me, I know it is the wrong platform, but nevertheless provided good info: [http://www.nslu2-linux.org/wiki/HowTo/AddUSBOneWireAdapter](http://www.nslu2-linux.org/wiki/HowTo/AddUSBOneWireAdapter)

I've not found the time to have a deeper look there. Maybe I can continue to try this evening or tomorrow.

Best Regards
Joerg

---

### Post by mike4ubuntu on 2010-08-18
yeah, rebooting didn't seem to help me either

```

$ sudo digitemp_DS2490 -q -a -o "%F" -i
Found DS2490 device #1 at 001/005
$

```

```

$ sudo digitemp_DS2490 -i -d 5 -n 0
[sudo] password for mike:
DigiTemp v3.5.0 Copyright 1996-2007 by Brian C. Lane
GNU Public License v2.0 - http://www.digitemp.com
Found DS2490 device #1 at 001/005
Turning off all DS2409 Couplers
..
Searching the 1-Wire LAN
&#9829;
$

```

---

### Post by baetmaen on 2010-08-19
Hi,

I solved my problem in another way. Since digitemp only supports temperature sensors (AFAIK) and I want to extend my 1wire net in the future, I had a closer look to owfs.

The following ppa provides owfs packages (Version 2.7p27-1 only but for me it works). The module needs to be blacklisted too.

With my USB connector I mount the owfs with the command:
```
sudo owfs -u /mountpoint
```And this is what I get:
```
10.0A04E6010800
10.472701020800
10.89FFE5010800
81.F6D42D000000
alarm
bus.0
settings
simultaneous
statistics
structure
system
uncached
```Below those 10. sensor folders, their is a subfolder called temperature and this gives the current sensor value:
```
cat /mnt/1wire/10.0A04E6010800/temperature
      23.375
```From that data those nice graphs are created:
[IMG]http://img714.imageshack.us/img714/8551/logh.png[/IMG]

Running ~ 21h without problems.

Best Regards
Joerg

---

### Post by mike4ubuntu on 2010-08-24
yep, owfs seems to work ok.

```

sudo add-apt-repository ppa:devil66/owfs

sudo apt-get update

sudo apt-get install owfs

mike@lic7:~$ sudo mkdir /mnt/owfs
mike@lic7:~$ sudo owfs -u /mnt/owfs
DEFAULT: ow_ds9490.c:DS9490_sub_open(555) Opened USB DS9490 adapter at 001/007.
DEFAULT: ow_ds9490.c:DS9490_detect_found(415) Set DS9490 001/007 unique id to 81 F6 01 29 00 00 00 44
mike@lic7:~$ sudo ls -Fals /mnt/owfs
total 4
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 ./
4 drwxr-xr-x 11 root root 4096 2010-08-24 15:40 ../
0 drwxrwxrwx  1 root root    8 2010-08-24 15:40 21.37611D000000/
0 drwxrwxrwx  1 root root    8 2010-08-24 15:40 81.F60129000000/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 alarm/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 bus.0/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 settings/
0 drwxrwxrwx  1 root root    8 2010-08-24 15:40 simultaneous/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 statistics/
0 drwxr-xr-x  1 root root   30 2010-08-24 15:40 structure/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 system/
0 drwxr-xr-x  1 root root    8 2010-08-24 15:40 uncached/

mike@lic7:~$ sudo cat /mnt/owfs/21.37611D000000/temperature
          23mike@lic7:~$


```

---

### Post by mike4ubuntu on 2010-08-24
however, I noticed that the owread function in owfs doesn't seem to work:

```

mike@lic7:/opt$ sudo owread -F 21.37611D000000/temperature
mike@lic7:/opt$
```

just doesn't return anything

---

### Post by mike4ubuntu on 2010-08-24
I guess I'm not sure how to use the special ow functions

```

mike@lic7:/opt$ sudo owread --autoserver 21.37611D000000/temperature
Zeroconf/Bonjour is disabled since dnssd library isn't found.
mike@lic7:/opt$

```

---

