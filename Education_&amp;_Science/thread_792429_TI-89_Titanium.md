---
title: "TI-89 Titanium"
date: 2008-05-12
forum: Education &amp; Science
---

### Post by twodayslate on 2008-05-12
I posted this a while back. TiLP did not support the Ti-89 Titanium back then. I redownloaded TiLP and I still can not get it to work even though I am hearing it works. 

I have a gray cord by Sony (mini-usb to usb). Settings: Graylink port #2?

I get the following error when I ready...
```
Msg: Error occured while writing to the device.
System: Input/output error (errno = 5)
```
Thanks a bunch!

---

### Post by ethoxyethaan on 2008-05-13
this tread is relevant to my intrests, but sorry i Have no idea how to link the TI 89 platinum to your PC.
i am very eager to know aswell. 
lets hope the programmers stumble upon it one day. =D

to help you out some way... where exactly did you heard it worked?

---

### Post by phoenix23 on 2008-05-13
[http://www.ticalc.org/archives/news/articles/11/118/118565.html](http://www.ticalc.org/archives/news/articles/11/118/118565.html)
TI89+ should work should work under 89. However, i have not gotten it to work.

---

### Post by twodayslate on 2008-05-14
Anyone?

---

### Post by twodayslate on 2008-05-16
Really need this. Thanks

---

### Post by bunny rabbit on 2008-05-18
I have a 89 titanium too. Mine is not connecting by usb cable either(out of the box anyway). I think it says on mr. TiLP's website that a 98t usb connection is supported:

[I]23/03/2006 by roms:
I am currently actively working on the DirectUsb (TI84+) link support. This should have been done 1 year earlier but I was involved in many professionnal projects and not really/fully motivated. Things are OK for now.

Note: thanks to the greatest/wonderful USB documentation from B. Moody, the TI84+ USB support is growing quickly. On April the 5th, TiLP-II is supporting all operations except FLASH related ones.

Note2: beta release of TiLP-II with partial (all functions except OS transfers) TI84+ & [COLOR="Blue"]Titanium USB support is available[/COLOR]: win32 linux. [/I]

Maybe I ought to do more research into this, but pointers are very welcome. Cheers.

---

### Post by twodayslate on 2008-05-18
I was thinking that perhaps it is just ubuntu?

---

### Post by bunny rabbit on 2008-05-21
> **twodayslate said:**
> I was thinking that perhaps it is just ubuntu?

Do you mean that something in the settings has to be changed? Like something in a driver for usb devices or so? (I'm a n00b so don't hold your breath for a comprehensive contribution from me :P ) Because I'm guessing it has something to do with the usb on the PC. It doesn't show up when I type lsusb in the terminal for example.

---

### Post by twodayslate on 2008-05-21
It apparently works in Fedora. 
[http://forums.fedoraforum.org/showthread.php?t=156140](http://forums.fedoraforum.org/showthread.php?t=156140)

edit:// Arch Linux too: [http://bbs.archlinux.org/viewtopic.php?id=48094](http://bbs.archlinux.org/viewtopic.php?id=48094) w/bugs

---

### Post by twodayslate on 2008-05-27
Anyone?

---

### Post by twodayslate on 2008-05-31
ups one more time.

---

### Post by bunny rabbit on 2008-06-01
What can I say, I haven't tried very hard but then I don't have my webcam, a second screen, a serial device, a bluetooth connection with a phone and a cradle for a palm working yet either ;)
Actually, I am happy that the OS itself runs so well on a PC that is covered with "designed for windows" stickers in the first place. But I wonder if there are users of ubuntu who actually did get their TI-89t to work with the usb cable at all.

---

### Post by bunny rabbit on 2008-06-02
Okay, so I've made a tiny bit of progress. Apparently it _does_ show up when I type lsusb after a fresh boot:
> Bus 002 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB Flash Drive
Bus 002 Device 005: ID 0bda:0103 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 058f:6331 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 0451:e004 Texas Instruments, Inc. TI-89 Titanium Calculator
Bus 001 Device 005: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 004: ID 045e:00dd Microsoft Corp. 
Bus 001 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 001 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000   I think I can see light at the end of the tunnel...

---

### Post by twodayslate on 2008-06-02
That is great!

I am done with school now so I don't need this done until next semester. Still want it. I would like to get rid of XP but I don't want wine or anything on my computer.
```
name@linux-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0451:e004 Texas Instruments, Inc. TI-89 Titanium Calculator
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

```
edit:// Trying this out: [https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251](https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251)

---

### Post by bravemenrun333 on 2008-06-08
tilp2 (install with synaptic) works like a charm for me on ubuntu 8.04 with ti-89 titanium, BUT: i have tu run it with

```
sudo tilp
```

it detects my device and also the cable type, port and all. very nice!

---

### Post by bunny rabbit on 2008-06-14
> **bravemenrun333 said:**
> tilp2 (install with synaptic) works like a charm for me on ubuntu 8.04 with ti-89 titanium, BUT: i have tu run it with

```
sudo tilp
```

it detects my device and also the cable type, port and all. very nice!

I'm getting close, but no cigar ;)

> ruben@linda:~$ sudo tilp
[sudo] password for ruben: 
TiLP2 - Version 1.01, (C) 1999-2006 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Sep  3 2007 16:56:25
tilp-INFO: setlocale: <en_GB.UTF-8>
tilp-INFO: bindtextdomain: </usr/share/locale/>
tilp-INFO: textdomain: <tilp2>
ticables-INFO: ticables library version 1.0.3
ticables-INFO: setlocale: <en_GB.UTF-8>
ticables-INFO: bindtextdomain: </usr/share/locale>
ticables-INFO: textdomain: <libticables2>
ticables-INFO: kernel: 2.6.24-19-generic
tifiles-INFO: tifiles library version 1.0.2
tifiles-INFO: setlocale: <en_GB.UTF-8>
tifiles-INFO: bindtextdomain: </usr/share/locale>
tifiles-INFO: textdomain: <libtifiles2>
ticalcs-INFO: ticalcs library version 1.0.2
ticalcs-INFO: setlocale: <en_GB.UTF-8>
ticalcs-INFO: bindtextdomain: </usr/share/locale>
ticalcs-INFO: textdomain: <libticalcs2>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticalcs-INFO: Checking hand-held status:
Segmentation fault
ruben@linda:~$ 

Did the program to work for you bravemenrun333? Or only the driver? Because I think that the TiLp2 just doesn't work with the usb to usb cable, but the driver does.

---

### Post by twodayslate on 2008-08-22
Does [this](http://www.linux.com/feature/144995) help anyone?
> TiLP's dependencies include a set of modules that enable access to supported devices, as well as instructions for setting the proper permissions for such access. How you invoke the program will depend on your calculator and link cable hardware arrangement. I use primarily a TI-89 and a SilverLink USB cable. TiLP requires you to pass the command-line options to specifying this -- for example, tilp --calc=ti89 --cable=SilverLink. 

---

### Post by bunny rabbit on 2008-08-25
Maybe it is a good idea to simply buy or use another kind of cable since it is more likely to be compatible... :-k

---

### Post by seth556 on 2008-08-30
I have a Ti-89 Ti and the regular mini-usb connector. Also I got Tilp2 installed from the debian repos. The problem is now getting it to connect with my calculator. 

This is what shows up from the terminal although nothing shows up in the actucal program saying my calculator is connected.

```

ticables-INFO: Link cable probing:
ticables-INFO:  found TI-89 Titanium on #1, version <3.00>
tilp-INFO: Searching for hand-helds on DirectLink...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-89 Titanium on #1, version <3.00>
ticables-INFO:  found TI-89 Titanium on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found  on #1, version <3.00>

(tilp:9238): ticables-WARNING **: usb_set_configuration (could not set config 1: Connection timed out).

kbuildsycoca running...
Error: "/var/tmp/kdecache-seth" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/var/tmp/kdecache-seth" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-seth" is owned by uid 1000 instead of uid 0.
ticalcs-INFO: Checking hand-held status:

(tilp:9238): ticables-WARNING **: usb_bulk_write (error submitting URB: No such file or directory).

ticalcs-INFO: Checking hand-held status:

(tilp:9238): ticables-WARNING **: usb_bulk_write (error submitting URB: No such file or directory).


(tilp:9238): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 2: Connection timed out).


(tilp:9238): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 129: Connection timed out).


```

---

### Post by seth556 on 2008-08-30
I'm not sure what I just did but now it seems to be working.

---

### Post by twodayslate on 2008-09-01
```
Msg: illegal operation or argument.
Cause: the program which uses this library is buggy. Fire-up the developer!
```
I now get it to show the TI89 on TILp but all the info is corrupt/wrong (screen shows random chars etc;)
```
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
1: 0 0 0 0
2: 0 0 0 0
3: 0 0 0 0
4: 0 0 0 0
5: 1 0 0 0
tilp-INFO: Searching for hand-helds on 5:1...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>

(tilp:9447): ticables-WARNING **: usb_claim_interface (could not claim interface 0: Operation not permitted).

1: 00 00 00 00
2: 00 00 00 00
3: 00 00 00 00
4: 00 00 00 00
5: 00 00 00 00
tilp-INFO: Searching for link cables...
ticables-INFO: Link cable probing:
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS1: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS2: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS3: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS1: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS2: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS3: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- lp scanner
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'scanner': yes
ticables-INFO:     is useable: yes

(tilp:9447): ticables-WARNING **: ioctl failed on parallel device: can't claim parport.
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport1: does not exists
ticables-INFO:     => you will have to create the node.
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport2: does not exists
ticables-INFO:     => you will have to create the node.
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
1: 0 0 0 0
2: 0 0 0 0
3: 0 0 0 0
4: 0 0 0 0
5: 1 0 0 0
tilp-INFO: Searching for hand-helds on 5:1...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>

(tilp:9447): ticables-WARNING **: usb_claim_interface (could not claim interface 0: Operation not permitted).

1: 00 00 00 00
2: 00 00 00 00
3: 00 00 00 00
4: 00 00 00 00
5: 00 00 00 00
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
tilp-INFO: tilp_device_err catched error 51

tilp-INFO: tilp_device_err catched error 51

ticables-INFO:  found <> on #1, version <3.00>
ret = 0
tilp-INFO: Searching for link cables...
ticables-INFO: Link cable probing:
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS1: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS2: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS3: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS1: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS2: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS3: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- lp scanner
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'scanner': yes
ticables-INFO:     is useable: yes

(tilp:9447): ticables-WARNING **: ioctl failed on parallel device: can't claim parport.
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport1: does not exists
ticables-INFO:     => you will have to create the node.
ticables-INFO: Check for parport support:
ticables-INFO:     parport support: available.
ticables-INFO: Check for parport usability:
ticables-INFO:     node /dev/parport2: does not exists
ticables-INFO:     => you will have to create the node.
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
1: 0 0 0 0
2: 0 0 0 0
3: 0 0 0 0
4: 0 0 0 0
5: 1 0 0 0
tilp-INFO: Searching for hand-helds on 5:1...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>

(tilp:9447): ticables-WARNING **: usb_claim_interface (could not claim interface 0: Operation not permitted).

1: 00 00 00 00
2: 00 00 00 00
3: 00 00 00 00
4: 00 00 00 00
5: 00 00 00 00
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
tilp-INFO: tilp_device_err catched error 51

ticables-INFO:  found <> on #1, version <3.00>
ret = 0
ticables-INFO: Check for tty support:
ticables-INFO:     tty support: available.
ticables-INFO: Check for tty usability:
ticables-INFO:     node /dev/ttyS0: exists
ticables-INFO:     permissions/user/group: -rw-rw---- root dialout
ticables-INFO:     is user can r/w on device: no
ticables-INFO:     are others can r/w on device: no
ticables-INFO:     is the user 'zac' in the group 'dialout': yes
ticables-INFO:     is useable: no
tilp-INFO: tilp_device_err catched error 51

```This happens when I do sudo tilp too.

---

### Post by twodayslate on 2008-10-29
ARG!  I even installed wine so I could run TI connect but that does not even work!
[[IMG]http://img300.imageshack.us/img300/6707/screenshotvx4.th.png[/IMG]](http://img300.imageshack.us/my.php?image=screenshotvx4.png)[[IMG]http://img300.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
[[IMG]http://img117.imageshack.us/img117/9008/screenshot1rr8.th.png[/IMG]](http://img117.imageshack.us/my.php?image=screenshot1rr8.png)[[IMG]http://img117.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
```
sudo tilp
TiLP2 - Version 1.01, (C) 1999-2006 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Sep  3 2007 16:56:25
tilp-INFO: setlocale: <en_US.UTF-8>
tilp-INFO: bindtextdomain: </usr/share/locale/>
tilp-INFO: textdomain: <tilp2>
ticables-INFO: ticables library version 1.0.3
ticables-INFO: setlocale: <en_US.UTF-8>
ticables-INFO: bindtextdomain: </usr/share/locale>
ticables-INFO: textdomain: <libticables2>
ticables-INFO: kernel: 2.6.24-21-generic
tifiles-INFO: tifiles library version 1.0.2
tifiles-INFO: setlocale: <en_US.UTF-8>
tifiles-INFO: bindtextdomain: </usr/share/locale>
tifiles-INFO: textdomain: <libtifiles2>
ticalcs-INFO: ticalcs library version 1.0.2
ticalcs-INFO: setlocale: <en_US.UTF-8>
ticalcs-INFO: bindtextdomain: </usr/share/locale>
ticalcs-INFO: textdomain: <libticalcs2>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
tilp-INFO: Searching for link cables...
ticables-INFO: Link cable probing:
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
tilp-INFO: Searching for hand-helds on DirectLink...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <TI-89 Titanium> on #1, version <3.00>
ticalcs-INFO:   PC->TI: Buffer Size Request (1024 bytes)
ticalcs-INFO:   TI->PC: Buffer Size Allocation (1023 bytes)
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>

(tilp:8536): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 2: Connection timed out).


(tilp:8536): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 129: Connection timed out).

ticalcs-INFO: Checking hand-held status:

(tilp:8536): ticables-WARNING **: usb_bulk_write (error submitting URB: No such file or directory).

ticalcs-INFO: Checking hand-held status:

(tilp:8536): ticables-WARNING **: usb_bulk_write (error submitting URB: No such file or directory).

ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/proc/bus/usb): mounted
ticables-INFO:  found <> on #1, version <3.00>

(tilp:8536): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 2: Connection timed out).


(tilp:8536): ticables-WARNING **: usb_clear_halt (could not clear/halt ep 129: Connection timed out).

```

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0451:e004 Texas Instruments, Inc. TI-89 Titanium Calculator
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by twodayslate on 2008-11-20
this is a really old thread... how did you guys get it too work?

---

### Post by coppercow on 2008-11-21
I have Tipl2 working on my machine like everything it took research and trial and error. from memory so may not be very accurate;

I got tilp2 1.12 from _ticalc dot org_

libticalc and libticables3 just in case.

I didn't install the tilp2 from repos since the one I found there was not the latest version available which I think is 1.12.

Also you will need to make sure your usb ports are working (independent of the TI-89) You can look around for help with that.

You will need to run tilp using sudo (sudo tipl) then enter your password. I have not been able to make it work otherwise.

Its buggy and crashes often but you can get what you need done. 

when you try to do the screenshot it will look like noise, just refresh it and you will get your shot. 

Can't think of anything else other than the ubiquitous search Google for help.

Hope this helps some

Coppercow ;)

---

### Post by jpeach on 2009-01-31
coppercow: Have you been able to get it to work with a SilverLink (USB) cable?  The details of how I installed it are detailed here:
[https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251/comments/13](https://bugs.launchpad.net/ubuntu/+source/tilp/+bug/49251/comments/13)

TiLP runs but it is not able to detect the calculator.  Any suggestions?

---

### Post by brunolabs on 2009-02-01
I have a TI-83Plus and TiLP cannot establish a connection.
I use the black cable.
Any ideas?

Thanks.

---

### Post by jdunn on 2009-04-01
I have a TI-89 Titanium and 64-bit Ubuntu 8.10.  Using 'lsusb' at the command prompt, I was able to see my calculator on the USB port.  Next, I tried TILP2 from the repositories (sudo tilp) but wasn't able to connect...even with the various program arguments.

I was going to install the latest TILP2 debs and all its dependencies directly from the TILP websight but, then I saw the latest builds depend on KDE libraries.  I have no desire to mix and match desktop environments.  :P

*Edit*
It looks like TILP2 v1.12 has both GTK and QT as dependencies.  That doesn't make any sense.  Why would you need both?...Or, do you get to choose (Qt for KDE or gtk for gnome)?

---

### Post by oponto on 2009-11-14
```
Msg: Invalid command ID.
Cause: TiLP received an unexpected Command ID, probably due to a transmission error.
```

How is a mini USB b cable called in "terminal language" like

```
tilp --calc=ti89 --cable=SilverLink
```

---

### Post by Ramwi on 2010-01-15
Ok, here's how i got my ti89 titanium working... hope its helpfull.
(DirectLink is usb cable in "terminal language of tilp;)")

```
sudo tilp --calc=ti89t --cable=DirectLink 
```

---

### Post by bunny rabbit on 2010-01-18
> **Ramwi said:**
> Ok, here's how i got my ti89 titanium working... hope its helpfull.
(DirectLink is usb cable in "terminal language of tilp;)")

```
sudo tilp --calc=ti89t --cable=DirectLink 
```

I've been trying all kinds of things since a long time until your suggestion.
Because that worked like a charm! :D Thanks.

---

### Post by killabee44 on 2011-02-10
> **Ramwi said:**
> Ok, here's how i got my ti89 titanium working... hope its helpfull.
(DirectLink is usb cable in "terminal language of tilp;)")

```
sudo tilp --calc=ti89t --cable=DirectLink 
```

Ramwi,

I also would like to thank you. This worked great and now my TI89 can connect to my pc with TILP2 without any problem. 

One less reason to boot into XP!

:D

---

