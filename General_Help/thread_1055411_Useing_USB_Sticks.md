---
title: "Useing USB Sticks"
date: 2009-01-30
forum: General Help
---

### Post by carlo bolzonello on 2009-01-30
Hello All,

I have built a 8.10 server, and need to copy some files from a USB stick connected to it. How do i go about doing this please.

I am using the command line interface, as the gui is for whimps ;)

---

### Post by phinullfermata on 2009-01-30
You need to find out what device the usb will be, i.e. /dev/sdc1.  Usually you can look at the file /etc/mtab to find out how many devices are mounted, add one letter to the name and that should be it.  Once you know that you can use the mount, or pmount command like this:

```
pmount /dev/sdc1 usb
```will mount the usb with your user permissions to /media/usb

```
sudo mount /dev/sdc1 /media/usb
```will do the same thing, but as the root user, so your specific user will have to gain root priveledges to access the files.

The commands to safely remove are ```
pmount /dev/sdc
``` and ```
sudo umount /dev/sdc
``` respectively.

---

### Post by carlo bolzonello on 2009-01-31
thank you very much for the help, i see the following listed 


support@ubuntusrvcpt:~$ lsusb
Bus 004 Device 002: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
support@ubuntusrvcpt:~$ support@ubuntusrvcpt:~$ lsusb

Which name do i use for the usb device?, sorry bit of a noob, windows operator for way too many years :)

---

### Post by phinullfermata on 2009-01-31
Without the USB in, run:
```
ls /dev | grep sd
```Plug in the USB drive and run the same command.  The extra entries added are the ones for your usb device (note, these can change for a specific device depending on how many other drives are in when you plug the USB drive in - it is not always the same)

---

### Post by carlo bolzonello on 2009-01-31
thanks, will try a bit later and revert back.....

---

### Post by carlo bolzonello on 2009-02-01
> **phinullfermata said:**
> You need to find out what device the usb will be, i.e. /dev/sdc1.  Usually you can look at the file /etc/mtab to find out how many devices are mounted, add one letter to the name and that should be it.  Once you know that you can use the mount, or pmount command like this:

```
pmount /dev/sdc1 usb
```will mount the usb with your user permissions to /media/usb


```
sudo mount /dev/sdc1 /media/usb
```will do the same thing, but as the root user, so your specific user will have to gain root priveledges to access the files.

The commands to safely remove are ```
pmount /dev/sdc
``` and ```
sudo umount /dev/sdc
``` respectively.

I get this error when i use the pmount code: I get this error: support@ubuntusrvcpt:~$ pmount /dev/sdc1 usb
Error: device /dev/sdc1 does not exist
support@ubuntusrvcpt:~$

---

### Post by carlo bolzonello on 2009-02-01
> **phinullfermata said:**
> Without the USB in, run:
```
ls /dev | grep sd
```Plug in the USB drive and run the same command.  The extra entries added are the ones for your usb device (note, these can change for a specific device depending on how many other drives are in when you plug the USB drive in - it is not always the same)

this is what i see when i run your code before the usb stick is in:
support@ubuntusrvcpt:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda5
ttysd
support@ubuntusrvcpt:~$

After i put in the USB stick, i see this when i run the command:
support@ubuntusrvcpt:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda5
sdb
sdb1
ttysd
support@ubuntusrvcpt:~$

so i assume that the sdb is my sick? but if i try and mount that, i get a error, am i missing something?

thank you for your help

---

### Post by orethrius on 2009-02-01
> **carlo bolzonello said:**
> this is what i see when i run your code before the usb stick is in:
support@ubuntusrvcpt:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda5
ttysd
support@ubuntusrvcpt:~$

After i put in the USB stick, i see this when i run the command:
support@ubuntusrvcpt:~$ ls /dev | grep sd
ptysd
sda
sda1
sda2
sda5
sdb
sdb1
ttysd
support@ubuntusrvcpt:~$

so i assume that the sdb is my sick? but if i try and mount that, i get a error, am i missing something?

thank you for your help

Try ```
pmount /dev/sdb1 usb
``` and see what happens.  If that doesn't work, try ```
sudo mount /dev/sdb1 /media/usb
``` and let us know if either one works.

---

### Post by carlo bolzonello on 2009-02-01
hey Orethrius,

still not, get this

support@ubuntusrvcpt:~$ pmount /dev/sdb1 usb
Error: device /dev/sdb1 is not removable
support@ubuntusrvcpt:~$ sudo mount /dev/sdb1 /media/usb
[sudo] password for support:
mount: mount point /media/usb does not exist

thanks again

---

### Post by orethrius on 2009-02-01
> **carlo bolzonello said:**
> hey Orethrius,

still not, get this

support@ubuntusrvcpt:~$ pmount /dev/sdb1 usb
Error: device /dev/sdb1 is not removable
support@ubuntusrvcpt:~$ sudo mount /dev/sdb1 /media/usb
[sudo] password for support:
mount: mount point /media/usb does not exist

thanks again

Well, pmount is preferred to save the trouble of having to alter permissions by hand, but you might try
```
gksudo mkdir /media/usb; sudo mount /dev/sdb1 /media/usb
```
and see if that seems to work.

---

### Post by carlo bolzonello on 2009-02-01
WORKS!!!!!!!!!!!, thank you very much, you are a legend

---

### Post by orethrius on 2009-02-01
> **carlo bolzonello said:**
> WORKS!!!!!!!!!!!, thank you very much, you are a legend

If anything, you're a legend: I botched my 8.10 install and am still trying to successfully burn ISOs for 8.04 and 8.10 from my backup partition.  Guess I won't go accidentally deleting the apt-get cache (/var/cache, DO NOT DELETE IT) any time soon. :rolleyes:

At any rate, you're certainly welcome. :)

---

