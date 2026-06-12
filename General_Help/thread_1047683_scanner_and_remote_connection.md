---
title: "scanner and remote connection"
date: 2009-01-22
forum: General Help
---

### Post by lxme on 2009-01-22
Dear all,

This problem is starting to get on my nerves and I don't know if I should file a bug report or if I made a mistake somewhere:
Here is the situation:

2 PCs
- PC1 Headless server running Ubuntu 8.10 with a Canon canoscan Lide50 (USB)
- PC2 Desktop PC running Ubuntu 8.10

1) If I attach a monitor to PC1 and logon locally as *root* and from a terminal do:


```
root@PC1:/home/user# scanimage -L
device `plustek:libusb:001:002' is a Canon CanoScan N1240U/LiDE30 flatbed scanner

```
Scanner is OK

2) If I attach a monitor to PC1 and logon locally as *user* and from a terminal do:


```
user@PC1:/home/user# scanimage -L
device `plustek:libusb:001:002' is a Canon CanoScan N1240U/LiDE30 flatbed scanner
```
Scanner is OK

3) If I logon remotely to PC1 from PC2 via VNC or SSH as *root* and from a terminal do:

```
root@PC1:/home/user# scanimage -L
device `plustek:libusb:001:002' is a Canon CanoScan N1240U/LiDE30 flatbed scanner
```
Scanner is OK

4) If I logon remotely to PC1 from PC2 via VNC or SSH as *user* and from a terminal do:

```
user@PC1:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```
Scanner WON'T WORK


5) If I log on locally to PC1 *AND* If I logon remotely to PC1 from PC2 via VNC or SSH afterward as *user* and from a terminal do:

```
user@PC1:/home/user# scanimage -L
device `plustek:libusb:001:002' is a Canon CanoScan N1240U/LiDE30 flatbed scanner

```
Scanner is OK
The goal is of course to log on PC1 remotely and be able to use the scanner remotely without having to log on locally on PC1. 
So, is this behavior normal, or did I miss something ?

Any help welcome

---

### Post by ayurchen on 2009-02-16
This is not a real solution (real solution probably involves some PAM/SEL/whatnot black magic), but this is what I put in rc.local
```
# Change scanner permissions to allow scanning from ssh sessions
VENDOR_ID=04b8:012f
BUS_ID=$(lsusb | grep $VENDOR_ID | awk '{ print $2 }')
DEV_ID=$(lsusb | grep $VENDOR_ID | awk '{ print $4 }' | sed s/://)
chown root.scanner /dev/bus/usb/$BUS_ID/$DEV_ID

```
where 04b8:012f is my scanner vendor id. Obviously you have to rerun the script every time the scanner is replugged.

---

