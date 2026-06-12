---
title: "Won't Boot after Install"
date: 2005-12-01
forum: Desktop Environments
---

### Post by politicaldog on 2005-12-01
The next big hurdle!

After what appeared to be a succesful install I removed the CD-Rom like it said and it rebooted. "OPERATING SYSTEM NOT FOUND"

I tried re-installing but its the same result!

Rick

---

### Post by Murgle on 2005-12-01
It is not finding grub, Were there any hickups or anything during the install process?  or do you have more than one harddrive and the bios is looking at the wrong one?

---

### Post by xmastree on 2005-12-01
Hi Rick...

Yeah, I agree with Murgle. Check that your BIOS is looking at the right disk. Ideally, first should be the CDROM, second should be the first IDE, usually IDE0.

---

### Post by politicaldog on 2005-12-01
There were no problems that I saw during install. It really looked like it went great. It loaded the program on the PM HDD the first time, then the second time it loaded it on the PS HDD. I removed the ROM when it said to then went into setup after it was rebooting and changed the Boot order.

CD Rom                    Hard Disk                    Removable Drives
Hard Disk                  CD Rom                      CD Rom
Removable Drives       Removable Drives         Hard Drive

Tried all those. I CAN See the HD light come on for a moment when it boots up like its loking but only breifly.

Rick

---

### Post by politicaldog on 2005-12-01
MARK THIS SOLVED.

I didn't realize that I could select in the BIOS which drive it looked at first.

Of course it was looking at the Primary Slave First.

UBUNTU is loading up

Thanks
Rick

---

