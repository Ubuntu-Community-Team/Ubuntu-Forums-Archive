---
title: "wubi 8.1 vs 8.04"
date: 2008-12-16
forum: General Help
---

### Post by teddyearp on 2008-12-16
Hi guys.  I have a maybe unique problem with the wubi 8.1.  I've been trying to install wubi/ubuntu 8.1 over my win xp pro sp3 native.  My box has a Pentium D805, and the 'c' drive is a 120g IDE, the 'd' drive is a 250g SATA.  I have tried over and over again to get to 8.1, but whenever I select 'Ubuntu" in the bootloader, all it does is give me a "Booting GRLDR" message and then just sits there.

Now mind you, I can get 8.04 to load just fine on either drive, and after the second boot to Ubuntu, I get the "Error 15: File not found" error, but I/we have already figured out the workaround for that, thanks to 'ago' and his post way back in Feb, 2008.

I also tried after the initial install of 8.1 to let my box boot to windows first, then re-boot and select 8.1, but it still hangs there.

Now, I'm trying the method here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Under the "Cannot boot into Ubuntu" section where it suggests that under windows, I run the chkdsk /r command.  It is still running as I post.

So, I will continue with this, I have already read that I can upgrade from 8.04 to 8.1 anyways, but in the meantime if anyone else has had this tiny trouble and has an answer, then cool.  Or maybe I will figure it out and post thusly.  I would just like to see the 'newest' interface and maybe not have to d/l and intall 308 files from within the 8.04.

thx in advance.

---

### Post by ago on 2008-12-19
Press INSERT at boot to get more messages and see if there is a specific error

---

### Post by PCessna on 2008-12-19
> **teddyearp said:**
> Hi guys.  I have a maybe unique problem with the wubi 8.1.  I've been trying to install wubi/ubuntu 8.1 over my win xp pro sp3 native.  My box has a Pentium D805, and the 'c' drive is a 120g IDE, the 'd' drive is a 250g SATA.  I have tried over and over again to get to 8.1, but whenever I select 'Ubuntu" in the bootloader, all it does is give me a "Booting GRLDR" message and then just sits there.

Now mind you, I can get 8.04 to load just fine on either drive, and after the second boot to Ubuntu, I get the "Error 15: File not found" error, but I/we have already figured out the workaround for that, thanks to 'ago' and his post way back in Feb, 2008.

I also tried after the initial install of 8.1 to let my box boot to windows first, then re-boot and select 8.1, but it still hangs there.

Now, I'm trying the method here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Under the "Cannot boot into Ubuntu" section where it suggests that under windows, I run the chkdsk /r command.  It is still running as I post.

So, I will continue with this, I have already read that I can upgrade from 8.04 to 8.1 anyways, but in the meantime if anyone else has had this tiny trouble and has an answer, then cool.  Or maybe I will figure it out and post thusly.  I would just like to see the 'newest' interface and maybe not have to d/l and intall 308 files from within the 8.04.

thx in advance.
Same thing happened on my Dell. Dell is from '04. Worked on Gateway, though, Gateway from 07.

Both computers use similar Intel hardware. Weird.

---

### Post by wwarren on 2008-12-22
I also had the problem where it hangs at "Booting GRLDR".  I had a FAT32 formatted USB hard drive plugged in and it seemed to be trying to read from it.  Unplugging that drive fixed the problem entirely.  I then investigated what was on the drive and found a folder called "System" that had Western Digital files on it including an autorun.  I erased that folder and Wubi has booted fine ever since.  At least up until I added another USB drive formatted as NTFS.  Now its getting stuck again as it tries to access this new drive and there's nothing on this drive but data.

---

