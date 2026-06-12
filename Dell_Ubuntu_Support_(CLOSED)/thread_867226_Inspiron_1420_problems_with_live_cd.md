---
title: "Inspiron 1420 problems with live cd"
date: 2008-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by henrybrad on 2008-07-22
I have had Ubuntu for about 1 year now and love it.  My computer is a dell inspiron 1420 that came with Ubuntu 7.04 factory installed.  The problem is that i have never been able to boot the laptop off of a live cd.  I can boot off live cd's of fedora and DSL but not Ubuntu.  
The process goes as follows:
I insert cd and reboot,
I press f12 and boot off the cd,
It comes to a menu and i select English,
Then i select "Try Ubuntu....."(live cd),
The window that says "Loading Linux Kernel" comes up,
It loads to 100% and then freezes,
After about 2 min, it comes up with a message "I/O Error - Error reading boot CD"
The only choice is a button that says "Reboot"

I don't think that it is the cd because it boots up fine on my other computer.  Thank you in advance for any help that you can give.

---

### Post by falcon61102 on 2008-07-22
Even thought you don't believe it's the cd because it boots on other computers, have you tried the Check CD function on the LiveCD boot menu?

It may be that your CD has a bad segment on it and your dell is attempting to read before it continues loading whereas your other computer ignores the bad segment and contiues.

I've had this happen to me in the past with damaged discs.  Some computers will skip past the error and load what is possible to and only give an error when I try to manually access the corrupt data while other computers would output an error as soon as it detected bad data.

---

### Post by henrybrad on 2008-07-22
Thank you for your quick reply.
I did the defects test on my other computer (because it could not load the kernel for the test on my main conputer...) and it failed with errors in three files.  It seems that it is the cd.  The only thing is that i tried a defects test on the cd that canonical sent me and there were no errors, but when i try to boot off of that cd (feisty fawn version 7.04) i get a different error.  It succesfully loads the kernel but fails to load any gui coming up with this:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off

And then a command line.  I am pretty sure there cannot be a problem with a cd that was created by canonical, so is there any way to fix this.  I am currently downloading the iso so i can try and make the cd again. Thanks again for your help.

---

### Post by falcon61102 on 2008-07-22
Burn the cd nice and slow.  1x would be ideal but I typically do my LiveCds at 4x and they normally come out fine.

---

### Post by henrybrad on 2008-07-22
Thanks a lot.  I used a different computer and burnt it at 1x and now the live cd works.  I now have a strange problem with wireless.  The system works with a wired ethernet connection but when i try to use my wireless network, it not only is unable to connect, but it takes down my whole network.  My network box goes crazy and i have to reboot my computer in order to get my network back up.  Any thoughts here?

---

### Post by falcon61102 on 2008-07-23
Go into your terminal and run:
```
lshw -C network
```
And post the results here.

Also, are you on a secured network?

---

### Post by henrybrad on 2008-07-23
This is the output:
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:9c:23:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:fc:81:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=172.16.1.39 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
```

Yes there is a password protection of the network.  I am currently downloading 300MB of updates (over wired connection) that i hope will fix the problem.  Thank you.

---

### Post by falcon61102 on 2008-07-23
Well, if the updates don't work, there are a few threads throughout the forum on working with wireless security.  And by the sounds of your post, that may be part of your problem.  If things don't work out, let us know and we'll help you get them fixed.

---

### Post by henrybrad on 2008-07-23
K. Thanks so much for your help.

---

