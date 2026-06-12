---
title: "Boot failure: &quot;DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER&quot;"
date: 2011-04-27
forum: Desktop Environments
---

### Post by Daemond on 2011-04-27
My power supply broke down. After getting a new power supply, I ended up getting this error message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" instead of getting the grub menu.

I've been trying to read threads about re-installing grub from the Ubuntu 10.10 Live CD but I fail on those steps, where I am supposed to mount something like "/dev/sda6". In fact, I can't see anything with the name "sda*" in the /dev/ directory. I don't even know if I am supposed to see them there.

My hard disk had Vista installed on it before I installed Ubuntu and grub on a different partition. I would very much like to restore both op-systems. I can't remember which system is on which "sdax" - I mean, I can't remember the numbers.

---

### Post by phz_swe on 2011-04-27
The Master Boot Record (MBR) where GRUB resides shouldn't have been specifically altered by a failed PSU. That your BIOS says that it can't find a device to boot from might very well mean that it can't read your drive.

Firstly I would check that you have connected the power and the SATA cables correctly to your hard drive. Your BIOS complains that it can't find a device to boot from - if the device is not powered on or plugged in, that is very natural.

Also, you might have shuffled some cables when you changed PSU - make sure the SATA cable for the main drive is in the same port as before the failure (probably SATA1). If this is not the case, maybe BIOS is looking for a drive on SATA1 to boot from, doesn't find it since the disk is on SATA2, and fails.

Examine the above thoroughly. A secondary possibility is that your drive has failed, either permanently (buy a replacement) or just lost the organization of its contents (some disk recovery might be possible, but a reformat is needed to use it as normal again). It is not uncommon for a faulty PSU to take equipment with it in its fall. Can you see any content on the drive?

For closure, go into the BIOS setup utility (press Del or F1 or F2 or F10 or whatever button your BIOS wants you to during startup) and make sure that it is set to boot from your hard drive. It is insanely unlikely that there should be a problem with this, but maybe you'll see something else that seems weird. You should be able to see auto-detected information about your disk in the BIOS setup program.

---

### Post by Yellow Pasque on 2011-04-27
> **phz_swe said:**
> Also, you might have shuffled some cables when you changed PSU..
..or completely forgot to plug a power connector into the drive. ;)
phz_swe is also correct that you should make sure the BIOS sees the disk to rule out hardware issues before trying LiveCD's and other software solutions.

EDIT: I guess it's also possible you have one of those early SATA drives with both a Molex and SATA power connector, and you connected both (thus, frying the drive). For your sake, I hope that's not the case.

---

### Post by RJARRRPCGP on 2011-04-27
The Award BIOS can't find the MBR!

---

### Post by deconstrained on 2011-04-28
Since you installed a new PSU, did you remember to plug one of its power connectors into the hard drive? HDD needs juice.

If the drive has power going to it and the issue still occurs, then you have a strange problem.

---

### Post by Daemond on 2011-04-28
Thanks a lot guys for the help and for teaching me some new technical knowledge!

I remembered to plug all the wires, but indeed I accidentally pulled out the sata cable for my HDD :$. How embarrassing is that? It was the error message that got me so confused, because it said "insert system disc", which I thought, meant like Windows recovery disc or Ubuntu Live CD...

Anyway, I'm glad I joined the forum, because it seems there are lots of nice people here willing to help with these things ;).

Thanks!

---

### Post by deconstrained on 2011-04-28
Happens to the best of us. Nobody's immune to making mistakes with cables and wires, but few admit so.

---

