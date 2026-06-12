---
title: "Samba Share - No permission"
date: 2016-02-18
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-02-18
Folks,

I have a samba share set up on a RaspberryPi running Raspian/Debian.

The share is a 500GB hard drive partitoioned into one FAT32 and one Ext4

The Ext4 is no problem, I know I cannot alter permissions on a FAT32 drive but it does show readable by anyone but two Ubuntu machines I have report 'Permission Denied' when I try to open the folder.

Strangely my Android phone can view all folders and files using ES File Explorer !!!

Any suggestions how I might view these on my Ubuntu machine?

Geffers

---

### Post by ik-0 on 2016-02-18
How are you mounting the CIFS shares in Ubuntu?  Are you using nautilus'  "connect to server" or using a command line.  Depending on how you setup the share, you might not be able to list the shares on your raspian but you can directly mount them.

---

### Post by Geoff_Lane on 2016-02-19
ik-O

Thank you for prompt reply, my main Ubuntu laptop failed a couple of months back hence me trying to temporarily survive using Raspberry Pi and Ubuntu Mate.

I may have found a potential problem, my phone and Nexus both allow me to alter Server, Domain, user and password. The R-Pi has the default 'user' which I am able to enter on the phone and netpad.

My Samba configuration has my Ubuntu login username as a Samba user but cannot display the FAT32 share contents but of course CAN display the Ext4 partition.

Same settings, same machine, only difference appears to be the Filesystem and even they are on the same HD, just different partition.

Geffers

---

