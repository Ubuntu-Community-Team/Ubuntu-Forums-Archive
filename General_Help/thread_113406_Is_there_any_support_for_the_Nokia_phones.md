---
title: "Is there any support for the Nokia phones?"
date: 2006-01-06
forum: General Help
---

### Post by PryGuy on 2006-01-06
Hello!
I have plugged my Nokia 6100 in the USB port usin the data cable and... nothing... :( Is there any possibility to make Nokia phones work with Breezy?

---

### Post by Lord Illidan on 2006-01-06
Try gnokii

I am not sure how it works though, never used it.

---

### Post by Denis on 2006-01-06
I would like to know too. i've also got a cable. I use it to transfer images and midi sound mostly, but I haven't been able to use it in Ubuntu. 
I don't think it is possible to do this. It also requires some drivers that are not available for Linux. If the system were more open it would be easier to make an open source driver for Linux.

Gnokii doens't seem to work for me. 
I get this error
```
Timeout: aborting command ``/usr/lib/gnokii/gnokii'' with signal 9
/usr/bin/gnokii: line 16: 13890 Killed                  timeout $TIMEOUT $BINARY "$@"

```
I also have no idea what value this should be in my .gnokii.rc: 
```
# Set port to the physical serial port used to connect to your phone.
# Linux version is:
port = /dev/ttyS0
```
I don't know if this program should work with me, because I don't have a cable from Nokia, but from another manufacturer.

---

### Post by s_spiff on 2006-01-06
If Gnokii works, please post about it, as to how to install it and stuff? I got a Nokia NGage, and haven't tried connecting it via USB, for the simple reason, I don't know what exactly will happen. I searched the wiki for anything concerning such stuff, but in vain.

---

### Post by Denis on 2006-01-06
I found it! It must be /dev/ttyUSB0 with me. 

Untill now I did the following: 

- install Gnokii
- copy /usr/share/xgnokii/help/en_US/sample/gnokiirc  to  ~/.gnokiirc
- open .gnokiirc and adjust it

I found the port using "device manager" in system > admin menu. 
I have connected it to a USB port, which was /dev/ttyUSB0

- gnokii --identify says something useful now, so I'll try to do something with it now.

---

### Post by Denis on 2006-01-06
pretty exciting, I am getting some output with: 

gnokii --identify

GNOKII Version 0.6.8
IMEI         : 355667008395573
Manufacturer : Nokia
Model        : RM-37
Revision     : V 4.10

and gnokii --monitor

Entering monitor mode...
RFLevel: 100
Battery: 100
SIM: Used 0, Free 250
Phone: Used 21, Free 479
DC: Used 2, Free 254
EN: Used 0, Free 12544
FD: Used 0, Free 12544
MC: Used 0, Free 512
ON: Used 0, Free 50
RC: Used 0, Free 768
SMS Messages: Unread 0, Number 61
Network: Mobistar (Belgium), LAC: 4bc8, CellID: ca01
CALL0: IDLE
CALL1: IDLE


It seems that some of the commands work, but others don't. I can get info from my mobile phone, but the logo and file options don't seem to work like they should. 
I'll try to test the program some more later. 
I tested Gammu too, it's based on Gnokii: you can get the DEBs here: [http://www.cihar.com/gammu/debs/](http://www.cihar.com/gammu/debs/)

Maybe we can get some things to work, if we look for it...
I did these tests with a Nokia 6610i, I've attached my config file for nokii. (remove .txt)

---

### Post by rasher on 2006-04-25
Using a DKU5 clone cable (PL2303 serial controller) together with my Nokia 6101, with the following settings:```
[global]
port=/dev/ttyUSB0
model=6510
connection=dlr3p
```.. and the rest as defaults, is giving me good results - even file operations appear to work (haven't tried up- or downloading files, but --getfilelist "A:\*.*" worked).

---

