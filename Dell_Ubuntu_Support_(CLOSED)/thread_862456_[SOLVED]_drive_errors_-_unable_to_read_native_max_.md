---
title: "[SOLVED] drive errors - unable to read native max address"
date: 2008-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cosborn72 on 2008-07-17
Hi all,

I am having an issue that maybe someone can help me with.  I am running ubuntu on a dell Ispiron. 530, purchase two weeks ago.  

When I got it, i cleared off all the partitions and created the following setup. (I'm typing this from memory, but I think it's accurate.)

250gb drive

small boot drive
50gb NTFS drive for Windows XP
196gb ext3 drive with Ubuntu 8.04 (not 7.10)
2 gb swap

Initially it worked fine.
Then it started stalling during startup.

I tried to start up in recovery mode, so I could see what was going on, and these are the last two lines.

>ata1.00 failed to read native max address err_mask=0X4
>ac timeout

One other possible factor - It seemed to start happening around the time I installed ext2 IFS in windows.  I use ext2 IFS on my laptop and have never had a problem, but I wonder if that could be causing it.  I removed it from windows, but the problem is still there.

Thanks!

Chris

---

### Post by cosborn72 on 2008-08-31
I was able to solve my problem here.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

Giddiup!

---

### Post by rescdsk on 2008-09-16
I had the same errors on upgrading from kernel 2.6.22 to 2.6.24.  The same Dell script fixed it for me.  Thanks for the pointer!

---

### Post by gaebriel on 2009-11-06
I ran into this error along with a "qc timeout" error immediately before it. I had just installed 8.04.3 LTS server x64 edition and the install worked fine, but after the reboot, these errors appeared and I was dropped down to the (initramfs) shell. 

Changing the way the SATA controller represented drives in my BIOS fixed the problem for me. I changed the BIOS settings on the SATA controller from IDE to AHCI and the next time I rebooted, everything worked.

---

