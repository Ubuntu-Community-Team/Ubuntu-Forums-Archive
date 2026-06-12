---
title: "USB media devices not mounting"
date: 2006-08-06
forum: Desktop Environments
---

### Post by BluntedBoyWonder on 2006-08-06
Hello folks. I am sorry if this is going to be double-posted anywhere, but I searched the web and the forums for a similar complaint but found none. 

Ever since I upgraded from Breezy to Dapper my Maxtor external harddrive and Sony DVD writer won't mount. It's not the USB sockets themselves because my Logitech wireless mouse worked from the start (and I tried connecting the external drives to the one my mouse uses, no success). 

I suppose I should give some more information about my system here. Please ask for what I should tell more in order for you to help me properly-- and I will suply it.

I didn't have this problem in Breezy with any Linux kernel. I am using the latest official Dapper release.

Thanks in advance!

---

### Post by taurus on 2006-08-06
Can you mount them by hand from a terminal (something like)?

```

sudo mount -t vfat /dev/sda1 /media/usb

```

---

### Post by BluntedBoyWonder on 2006-08-06
>  	Can you mount them by hand from a terminal

Thanks for the fast reply, Taurus. 

I tried the command and got an error saying 
```
mount: speciale apparaat /dev/sda1 bestaat niet

``` (TR.- special device /dev/sda1 does not exist.)

:confused:

---

### Post by adverb on 2006-08-06
i also tried to do the 'sudo mount -t vfat /dev/sda1 /mnt/usb' 
and got
mount: special device /dev/sda1 does not exist

any ideas?  i know that slackware put the usb devices there, but in ubuntu, im just not sure, i checked the /dev/* directory, and there's nothing with sda or sr or anything... will it be one of the /dev/tty*?

where does dapper put usb devices?

thanks

---

### Post by BluntedBoyWonder on 2006-08-20
Ok something has changed. Using USB View, I found that Dapper thinks I have USB 1.0! This is absolutely not true, I have USB 2.0 - it explains why my external media devices won't mount... 

I don't know how to fix this, do any of you? Help would be greatly appreciated. :(

---

### Post by taurus on 2006-08-20
When you plug in your USB device, open a terminal and see what the system thinks it is with

```
dmesg | tail
```
It will tell you whether it's /dev/sda, /dev/sda1, /dev/sdb, etc.  Once you know what it is, mount it with the same name...

---

### Post by BluntedBoyWonder on 2006-08-20
Dmesg is telling me this:
 > [17180063.912000] usb 1-3: new high speed USB device using ehci_hcd and address 3
[17180064.912000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.


Now this is nothing I did, it must have come from the upgrade from Breezy to Dapper (remember all was fine with Breezy.)

I have absolutely no clue how to assign IRQs, anyone? Device in question is an external Maxtor OneTouch harddrive.

---

### Post by taurus on 2006-08-20
Try

```
dmesg | more
```
since I want to see the whole message...

---

