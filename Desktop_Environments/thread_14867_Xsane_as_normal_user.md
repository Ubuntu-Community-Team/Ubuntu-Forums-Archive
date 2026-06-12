---
title: "Xsane as normal user"
date: 2005-02-10
forum: Desktop Environments
---

### Post by Syzygy on 2005-02-10
Hi!. I am new to Linux and I've been trying Ubuntu since last week. Most things are working fine, but I can't get Xsane to detect my scanner (Agfa snapscan 1212u, USB) as a normal user and I always have to start it with sudo in order to get it working. I have searched through forums and Google a lot before asking, but the solutions and answers I've found don't fix the problem (i.e.: adding myself to the scanner group, etc) or simply are too cryptic for a Linux novice...does anybody know how could I solve this?. The only thing that works is unplugging and re-plugging the scanner again, then Xsane detects it OK, but when I close the application I get an error message ("You don't have permission to create a file") and I'd like to use my scanner without needing to hotplug every time I need it...

Thanks in advance!.

---

### Post by Syzygy on 2005-02-10
Oops...I might have posted this in the wrong subforum...

---

### Post by Goob2k on 2005-02-10
First you need to find out which device your scanner is in /proc/bus/usb.  The file /proc/bus/usb/devices should tell you.

Here's a snippet of my scanner entry in that file.  The important things to look at are bus and Dev# in the T: line.
T:  **Bus=04** Lev=02 Prnt=03 Port=04 Cnt=01 **Dev#=  4** Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04a9 ProdID=2204 Rev= 0.05
S:  Product=CanoScan FB630U
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=10(unk. ) Sub=01 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

This means my scanner is "/proc/bus/usb/004/004".  As a test I ran:
sudo chown root:scanner /proc/bus/usb/004/004
sudo chmod 0660 /proc/bus/usb/004/004
and magically my scanner was found in Xsane without it having to be run as the superuser.

Since I run webmin on my system, I used it to make a new startup script to set the scanner permissions on startup.  

I guess if you save this to /etc/init.d/usbscannerperms (or another name of your choice) it ought to work.  Be sure to change the paths to match your scanner.  If you unplug and plug your scanner back in, these numbers will change and you'll have to re-edit the script to make it work again.

```

#!/bin/sh
# Set USB Scanner permissions

case "$1" in
'start')
        chown root:scanner /proc/bus/usb/004/004
        chmod 0660 /proc/bus/usb/004/004
        ;;
'stop')
        ;;
*)
        echo "Usage: $0 { start | stop }"
        ;;
esac
exit 0

```

---

### Post by Syzygy on 2005-02-11
Thank you!. I'm gonna try that, hope it works!.

---

### Post by Syzygy on 2005-02-11
Well..changing the permissions to 660 in /proc/bus/usb/001/003 (mine is there) works fine, but the script doesn't (it seems that it somehow doesn't get executed at startup???), so every time I reboot I have to manually set the permissions again. I have even tried:

sudo chown (me):scanner /proc/bus/usb/001/003

to set the scanner as mine and not owned by root, but that change is reverted when I close the session.

Any more ideas of how to make this run automatically at startup? I'm looking for the Linux equivalent to the DOS file "autoexec.bat"   :-D

---

