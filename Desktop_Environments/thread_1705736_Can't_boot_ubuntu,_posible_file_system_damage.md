---
title: "Can't boot ubuntu, posible file system damage"
date: 2011-03-12
forum: Desktop Environments
---

### Post by Absol on 2011-03-12
I have the 3 HDs with different OS each one, the HD from which my PC that always boots has a grub and from that grub i can chose between two ubuntu installations that are in different HDs but both installations use the same swap file which is in the (i presume) damaged drive.
When trying to boot from any of the ubuntu installations and even from live CDs i get a bunch of error messages that i think are related the swap's HD (something like "ata5.000 ... error"), after some minutes errors stop appearing on terminal but nothing else happens after.
I tried disconnecting the HD that contains the swap then i can boot on live CDs and on the linux installation that is still connected, but without swap of course.

My problem is that i cant attempt to fix the HD if i boot without it connected and i cant boot when it is connected.

Please help.

---

### Post by XsheepX on 2011-03-12
GRUB is notorious for halting booting to try and fix whatever disk errors it may encounter, especially if it's because the disk has been altered by another OS. Did you alter anything in some sort of partition manager in one of your Operating Systems?

You said you have 3 HDD's, all with different OS? Try switching the host drive with a slave and try to boot from it.

If all else fails, boot from any live linux CD and reinstall grub or re-format the partition that's causing you trouble.

---

### Post by Krytarik on 2011-03-12
It seems that the only way to avoid the swap partition getting mounted at boot is to outcomment its entry in "/etc/fstab". Good luck!

---

### Post by Absol on 2011-03-13
Hi, thanks for you answers.

> **Krytarik said:**
> It seems that the only way to avoid the swap partition getting mounted at boot is to outcomment its entry in "/etc/fstab". Good luck!

I did this, now i am using a new swap in one of the good HDs. If i unplug the bad HD i can work fine but still want to recover some files from the bad HD.

> **XsheepX said:**
> Did you alter anything in some sort of partition manager in one of your Operating Systems?

No, but i did noticed that the last time i turned off my system before the failure (using ubuntu from the HD that still works but had swap on the bad HD) it stopped responding and since it did not turn off by it self i used the case power button.

> **XsheepX said:**
> You said you have 3 HDD's, all with different OS? Try switching the host drive with a slave and try to boot from it.

I'll try this next, but when i unplug the bad HD system boots normally.


Also i noticed that the recovery option from grub does boot (with bad HD pluged) but the terminal is being polluted all the time by the error messages (example below) and prom is quickly covered by errors.

I'll try now the "recover files from damaged HD" threads.

Some of the errors displayed repeatedly are:

```

[ 1266.977329] ata7.00: status: { DRDY ERR }
[ 1266.977383] ata7.00: error: { UNC }
[ 1271.######] ata7: EH in SWNCQ mode,QC:qc_active 0x1 sactive 0x1
[ 1271.######] ata7: SWNCQ:qc_active 0x1 defer_bits 0x0 last_issue_tag 0x0
[ 1271.######]   dhf is 0x1 dmafis 0x0 sdbfis 0x0
[ 1271.######] ata7: ATA_REG 0x51 ERR_REG 0x40
[ 1271.######] ata7: tag : dhfis dmafis sdbfis sactive
[ 1271.######] ata7: tag 0x0: 1 0 0 1
[ 1271.######] ata7.00: excepation Emask 0x1 SAct 0x1 SErr 0x0 action 0x6 frozen
[ 1271.######] ata7.00: Ata error. fis:0x21
[ 1271.######] ata7.00: failed command: READ FPDMA QUEUED
[ 1271.######] ata7.00: cmd 60/08:00:fe:00:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[ 1271.######]          res 51/40:08:fe:00:00/40:00:00:00:00/40 Emask 0x9 (media error)
[ 1271.934564] ata7.00: status: { DRDY ERR }
[ 1271.934617] ata7.00: error: { UNC }
[ 1272.480896] end_request: I/O error, dev sdc, sector 254
[ 1272.480951] Buffer I/O error on device sdc5, logical block 32
[ 1272.481007] Buffer I/O error on device sdc5, logical block 33

```

There is a lot of hex and have no idea of what that means, i guess i'll google that latter. ###### means that i got bored from coping numbers but there are numbers instead of #.

---

### Post by Absol on 2011-03-13
Well after checking other threads i ran some tests and found out that my file system is ok, so i concluded that it is a HW failure, sadly my HD seems to be about to die.

Thanks for your help :P

---

### Post by Krytarik on 2011-03-13
Were you at least able to save your data?

---

