---
title: "bios does not detect my hdd, in aspire laptop??"
date: 2009-01-28
forum: General Help
---

### Post by kronictokr on 2009-01-28
acer aspire 5000, sis chips, amd 64 procesor

this all happened when i tried reinstalling windows over ubuntu wich was installed at the time. i dint have the internet, so i dint reset any drivers, and they were all configured to ubuntu linux. still are, i think. 

i did
sudo lshw -C disk

and got this

 *-cdrom                 
       description: DVD writer
       product: DVDRW SOSW-833S
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: VRS2
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: FreeAgentDesktop
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 100D
       serial: 5QF4CEGF
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=00085167

i am currently running off an external hd, on the same laptop. i can see when bios is booting up it can see my ram, my dvd(which doesnt work either??) but no hdd. if unplug my external hd and try to boot, all i get is "operating system not found" ??  if i try to boot from cd/dvd it just hangs in black screen with a little cursor in the top left. i even tried physicaly removing starting my laptop, then reinstalling it and restarting my laptop...nothing.  i think may be my mbr, bios upgrade?, or ???  i have tried grub and recovery disks to no avail, arrrrg
please help

---

### Post by ajgreeny on 2009-01-28
Go into your BIOS and check whether the disks are seen by the system (hit Del or one of the function keys to get into BIOS; check what the system says at boot for the correct key).  It sounds as if they are not seen by the system for some reason.  It could also be worth looking in the partition editor on the Live CD to see if ubuntu can see the disks.

---

### Post by kronictokr on 2009-01-28
tx for your reply, no bios has no listing under hdd, and i am unable to use my live cd with this laptop, as my cd/dvd rom doesnt work right either. i installed ubuntu on an external hd from a friends computer which lets my laptop boot to the external hd. when in ubuntu on the external, it reads the dvd, but it work work on boot up???  i also have an external dvd that i can use, but i dont know how i could boot to it with my live cd. but i have installed partition editor before and not seen any sign of my internal hd at all.

---

### Post by ajgreeny on 2009-01-28
Sorry to say this, but I don't know where to tell you to look further for any help.  It must be a hardware problem, I think.  Motherboard, or hard disk?

---

### Post by kronictokr on 2009-01-29
if my bios is not detecting my hdd, is it posible to flash or reset it, to make re detect my hdd.  

or, are there any programs for linux that may be able to detect the funked piece of hardware so i can format it.

i think my bios is fraged, if i stay in bios too long it crashes on me, just freezes and sends my fan in overdrive.

---

