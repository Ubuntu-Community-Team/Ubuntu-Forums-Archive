---
title: "Dazzle Dvc100 Drivers on Ubuntu"
date: 2018-06-29
forum: Gaming &amp; Leisure
---

### Post by teakplum on 2018-06-29
I have a dazzle dvc100 and I'd like to try streaming old games on twitch.  Unfortunately, I don't have the drivers for it, so it is not recognized on obs.
[http://cdn.pinnaclesys.com/SupportFiles/Hardware_Installer/readmeHW10.htm](http://cdn.pinnaclesys.com/SupportFiles/Hardware_Installer/readmeHW10.htm)
These are the only online drivers that I have found.  Is there anyway to make this situation work, or should I look for different options.  Also, I'm a complete Ubuntu scrub.

---

### Post by deadflowr on 2018-06-30
It has kernel support so no drivers needed, in so far as I know.
Try this
unplug the device then plug it back in.
Wait a few seconds and then run this command in a terminal
```
dmesg | tail
```
post back the output.

---

### Post by teakplum on 2018-06-30
```
[146150.090976] writing to lpe: 00000010: ff 06 ff ff 00 00 01 00 ff 82 ff ff
           ............
[146150.091107] writing to lpe: 00000000: 01 01 01 01 00 00 14 00 ff ff ff ff 72 00 0c 00  ............r...
[146150.091111] writing to lpe: 00000010: ff 0e ff ff 00 00 01 00 ff 86 ff ff
           ............
[146150.091111] usb 1-1: new high-speed USB device number 28 using xhci_hcd
[146152.284894] usb 1-1: New USB device found, idVendor=2304, idProduct=021a, bcdDevice= 1.00
[146152.284894] usb 1-1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[146152.284907] usb 1-1: Product: DVC100
[146152.284916] usb 1-1: Manufacturer: Pinnacle Systems GmbH
[146152.297597] platform vpd: Driver vpd requests probe deferral
[146152.297706] platform vpd: Driver vpd: Driver vpd requests probe deferral
```

It appears to recognize the device, so maybe it's obs that has the problems with it?

---

### Post by deadflowr on 2018-06-30
Hmm,
It seems to not be loading the driver.
Reading around some it should load the em28xx kernel module(driver)
Running a similar dmesg command to the previous one what does
```
dmesg | grep em28
```
show?
(the | grep output will show all entries with the em28 string in the dmesg log file.
if nothing, then the driver never loaded, which is odd)

As an aside I wonder if you need the video4linux libraries.
In which case I think installing the v4l-utils package should bring in the proper libraries needed.
To install the v4l-utils run
```
sudo apt update
sudo apt install v4l-utils
```

---

### Post by teakplum on 2018-07-01
dmesg grep em28 shows

Usage:
 dmesg [options]

Display or control the kernel ring buffer.

Options:
-C, --clear
-c, --read-clear
-D, --console-off
-E, --console-on
-F, --file <file>
-f, --facility <list>
-H, --human
-k, --kernel
-L, --color[=<when>]

-l, --level <list>
-n, --console-level <level>
-P, --nopager
-r, --raw
-S, --syslog
-s, --buffer-size <size>
-u, --userspace
-w, --follow
-x, --decode
-d, --show-delta
-e, --reltime
-T, --ctime
-t, --notime
    --time-format <format>
Suspending/resume will make ctime and iso timestamps innacurate.

-h, --help
-V, --version

Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
   news - network news subsystem

Supported log levels (priorities):
  emerg - system is unusable
  alert - action must be taken immediately
  crit - critical conditions
  err - error conditions
 warn - warning conditions
 notice - normal but significant condition
 info - informational
 debug - debug-level messages


For more details see dmesg(1).



When I typed in dmesg | grep em23 nothing came up.
Also I installed video for linux.  Sorry for the late response.

---

### Post by deadflowr on 2018-07-02
Scrounging around I think the card requires usb 2.0 ports to work. (or work properly)
Which might be where the problems lie.

---

### Post by teakplum on 2018-07-02
I have both 2.0 and 3.0 ports and it doesn't seem to be working in either.

---

### Post by deadflowr on 2018-07-02
Yeah, not much more I can think of except the unenviable idea the card is broken.
If you have a Windows install somewhere you could use that to confirm whether it's the card as a whole, or something about the card that cannot be registered by linux.
If it registers in a Windows system correctly, then it's probably a tiny issue within the card that prevents linux from reading it properly.
But that's about as far as I can think on it.

I never asked what version of Ubuntu is being used? (as in is it Ubuntu 14.04 or 16.04 or 17.10 or 18.04)
( Oh, one thing I could think it might be is a regressive driver in the kernel in use.)
Perhaps see if another version of Ubuntu gets it to work or (if you dare) you could try a mainline kernel:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")
Note that using mainline kernels is not for the faint of heart.

Good luck in which ever direction you move or don't move.
Not that anything I've posted is or will be helpful

---

### Post by newsted44 on 2018-09-03
Any resolution to this?  Thanks!

---

