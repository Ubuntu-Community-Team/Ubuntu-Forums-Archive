---
title: "Latitude 5430, UEFI, and Ubuntu 12.10 install"
date: 2012-12-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by smblion on 2012-12-13
I'm having several strange problems with installing 12.10 on this notebook.

First, it seemed to install correctly but I was receiving "invalid partition table" upon boot. At that time I was unfamiliar with UEFI, this is a new laptop and I haven't had one that uses that before.

After a few tries of reinstalling attempting to fix the booting issue, (which I later discovered could be fixed by manually booting the ubuntu option under the UEFI menu in the one-time boot menu), the ubuntu installer now simply hangs before it starts. I see the Ubuntu logo and the moving dots beneath it, and after a few moments they cease moving and the system hangs. Once in awhile it also crashes to a prompt, stating a general failure.

Windows 7 still works fine when I reinstalled it. I've tried using the 'help me boot from CD' option from the 12.10 install disc, but that didn't fix the issue.

I'm guessing there may be something broken in the original install I attempted, and I think if I could somehow remove that from the UEFI configuration it would allow me to install again, but this is only a guess, and I dont know how to remove that from UEFI. Any help is appreciated.

---

### Post by smblion on 2012-12-13
Interestingly enough, the 12/13/2012 build of 13.04 was able to install. Perhaps something between the differences in 12.10 and 13.04 resolved this issue?

However, I would much prefer to use a release version, so I am still looking for a solution to installing 12.10.

---

### Post by oldfred on 2012-12-13
Not sure what difference are now in 13.04.

You do need the 12.10 64bit version of Ubuntu and have to boot from the UEFI menu in UEFI mode not legacy/BIOS/AHCI or whatever.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Use Windows to shrink Window partition and reboot a couple of times so it can run chkdsk and make whatever repairs it likes to make on a resize. Then you can partition in advance or partition as part of the install.

Different model, but BIOS may be similar?
       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to [EasyBCD]("http://ubuntuforums.org/./EasyBCD.html"))
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

### Post by smblion on 2012-12-13
well, the only problem I was having with 12.10 it turns out was after a few install attempts which I thought were failing, but in fact were probably working as directed, when suddenly the installer would hang before reaching the first stage of the install.

However, now that 13.04 is installed and working.. I'm almost wary of even attempting to go back, at least until someone can explain why it was hanging. This is a work system and I'd rather not risk crippling it only to run 12.10 instead of 13.04, if 13.04 is working.

---

### Post by oldfred on 2012-12-13
Well 13.04 is still alpha. 

Most users booting 13.04 want breakage so they can solve the puzzle of why it broke. Part of the fun of a new system.

If you need system to work every time you boot, best not to rely on 13.04 until it is released.

Do you have room for another 10 to 25GB / (root) partition. Then you could have both?

---

