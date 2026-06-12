---
title: "CDROM is not being detected anymore"
date: 2009-01-21
forum: General Help
---

### Post by hanniph on 2009-01-21
I've got really annoying problem: cd/dvd drive no longer works. It cant mount. On my/etc/fstab I have this line:
```
/dev/scd0       /media/cdrom0   udf,iso9660 defaults,ro,user,exec 0       0
```
and in /dev there is no scd0 (neither cdrom, hda). What's more running
sudo lshw -C disk gives me only my hard drive and no cdrom. It seems that system doesn't recognize cdrom drive anymore.
So far I tried booting kernel with noapic acpi=off option and removing cdrom0 line in etc/fstab file but had no luck. 
I feel desperate about this:(

---

### Post by taurus on 2009-01-21
Make sure the cable on the back of the drive securely plugged in.

Go into the BIOS and see if your CD-ROM even shows up in there.

---

### Post by hanniph on 2009-01-21
It is not that easy since I'm running ubuntu on a laptop. But I checked bios settings and couldn't find cdrom there.

---

### Post by taurus on 2009-01-21
If the BIOS can't detect your CD-ROM, no OS will.  It could mean either the cable in the back of your CD drive is not connected securely or your drive is RIP.

---

### Post by hanniph on 2009-01-21
Checked bios once again and in boot priority section I have three options: 
sata hdd, pci lan stuff and IDE ODD. And..  have no clue what the last option is :D

---

### Post by ajcham on 2009-01-21
> **hanniph said:**
> Checked bios once again and in boot priority section I have three options: 
sata hdd, pci lan stuff and IDE ODD. And..  have no clue what the last option is :D

ODD stands for Optical Disk Drive - this would be your CD-ROM drive.  However, the boot order is not where you want to look, as this listing does not automatically change to reflect installed or removed hardware.

There should be another section in your BIOS that lists the installed hardware - I assume this is where you previously checked? As has been said, if the BIOS is not detecting the drive, the OS can't do a thing about it.

---

### Post by Tomatz on 2009-01-21
See if your laptop will boot a live cd, if not then there is a good chance the drive is faulty ;)

---

### Post by buzz57 on 2009-01-21
Is the CD drive one of the removeable type? If yes you might want to try removing it then reconnecting it. All of my laptops have removeable drives and occasionally after movement on the older laptops the drive loses its connection. You will need to hard boot again to ensure the Bios picks it up

---

### Post by hanniph on 2009-01-21
> There should be another section in your BIOS that lists the installed hardware - I assume this is where you previously checked? 
Yes, there is one line in MAIN section of bios that says everything:
```
DVD/CD-ROM Drive: None
```

>  	
See if your laptop will boot a live cd, if not then there is a good chance the drive is faulty 
No luck either

> Is the CD drive one of the removeable type? 
looked through manufacturers documents and found that it is fixed :(

So it is either dead or not connected. Thanks for replies guys!

---

### Post by Tomatz on 2009-01-21
Dead drive IMO :(

---

