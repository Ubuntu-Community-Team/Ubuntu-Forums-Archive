---
title: "Staticly assign device names (/dev/sda, etc.) to specific hard drives"
date: 2011-02-20
forum: Desktop Environments
---

### Post by jharris1993 on 2011-02-20
This is one of those questions where I highly suspect that the answer will be something like ". . .just stinks bein' you, kid."
 
My setup:
I have Ubuntu 10.04 x64 (desktop) installed on a computer with a bunch of SATA ports, including one e-SATA on the back
 
Because of the way the hardware works with these ports, the *external* port is the first SATA port, a second SATA port inside becomes #2, and a cluster of four ports (that can be made into a (ahem!) RAID array become ports 3 through 6.
 
All ports are configured as SATA (PATA emulation)
 
My boot drive is located on SATA-2 (the inside connector), a four disk "MD" raid array is located on SATA 3-6, and I have an external HD enclosure that I plug into the e-SATA connection.
 
With all six drives plugged in, they get ordered like this:
/dev/sda - External drive
/dev/sdb - Internal operating system drive (bootable)
/dev/sdc - RAID drive 1
/dev/sdd - RAID drive 2
/dev/sde - RAID drive 3
/dev/sdf - RAID drive4
 
Here's the problem:
If, for whatever reason, I decide to disconnect the external HD (/dev/sda), upon the next reboot everybody moves up a notch - making the boot drive /dev/sda, and the four RAID drives /dev/sdb - /dev/sde
 
This causes untold confusion - not only with myself, (I accidentally totally boffed a nicely configured Ubuntu install that I was working on, tweaking for days. Errrr!), but with the MD raid utillities because (via the mdadm.conf file) it expects the devices to be /dev/sdc - /dev/sdf - and when they all bump up a slot, the array fails to boot.
 
This is (IMHO) totally unacceptable because I would very much like to use that external SATA port to plug whatever I want into - like a USB port - especially since I have several HD docks that use eSATA, along with other external SATA devices.
 
I cannot use UUID's, because the four RAID drives do not have individual UUID's, they share the array-specific UUID established when the filesystem is generated.
 
What I would like to be able to do is assign certain logical positions to fixed device names.
Viz.: The boot drive as /dev/sda - the raid drives as /dev/sdb-sde, the eSATA as ../sdf and whatever I plug into a USB port come up as a device lower in the chain. (these would be allowed to change as needed) However I wold like the drive assignments for /dev/sda - /dev/sdf to be statically assigned.
 
I would especially like the devices to remain constant - despite the fact that they may be removed or not working - so that I can set up my system knowing that a particular drive will always remain where it is set to be - and if a drive fails, I can remove it and reboot (if necessary) without screwing up my entire configuration.

---

### Post by wizard10000 on 2011-02-20
Have you considered assembling the array by UUID?

---

### Post by Vollhorst on 2011-04-21
Hi Folks,

i have the same problem and i was stopping by via google.
What i dislike is when there are no answers or hints to find except dumb comments like 'why would you do this' or have you danced naked under a full moon....

There is no way to use uuid in the madm.conf to assign a array !!
Only the result of that array has a uuid "/dev/md0/"
If there is a way then s.o. should change the fu... bad maunual of madm.

So again, does anyone know a way to assing uuid to /dev/sdx 'before' fstab comes in place ?

THX

---

### Post by Vollhorst on 2011-04-21
Agread, 

thats why i will post my idea i have after reading the web.

To staticly assign /dev/sdX to an UUID you can use the udev rules:
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

this will avoid the 'randomly' assigning of the HDD described here:
[http://www.dell.com/downloads/global/power/ps1q07-20060392-Domsch.pdf](http://www.dell.com/downloads/global/power/ps1q07-20060392-Domsch.pdf)

BR

---

