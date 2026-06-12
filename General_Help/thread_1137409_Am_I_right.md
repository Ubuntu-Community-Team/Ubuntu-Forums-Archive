---
title: "Am I right?"
date: 2009-04-25
forum: General Help
---

### Post by Crafty Kisses on 2009-04-25
So as of right now my current setup is a Vista / Ubuntu 8.10 partition, I rarely boot into Vista, but I do occasionally boot into Vista for some essential programs. So what I want to do is put Jaunty in place of the Intrepid partition. So this is how I think it will work, I just want to make sure this is why I'm posting. First I need to reinstall the Windows MBR by using EasyBCD, then once I have done that, I remove the Intrepid partition, then reshrink the Windows parition, then put Jaunty on the unallocated space. Am I right, or am I missing something?

---

### Post by ninjapirate89 on 2009-04-25
Instead of doing all that, why not just upgrade Intrepid to Jaunty?

---

### Post by 3Miro on 2009-04-25
Do you want to keep Intrepid? If not, then your scheme is too hard.

If you wish to make a clean install of Jaunty over the existing Intrepid install:

1. Backup all important data from the Intrepid partition.
2. Boot from the LiveCD
3. Select manual partition and select Jaunty to be installed on the Intrepid partition (select it to be formated and possibly under ext4)
4. Install and tell it to install the boot-loader.

That should preserve Vista and install Jaunty on top of Intrepid.

WARNING: the above will completely destroy all data that you have on the Intrepid partition - so backup.

---

### Post by lisati on 2009-04-25
You *migh*t be able to skip the EasBCD step if both Ubuntu & Vista currently boot. I have limited experience doin a (re)install on a machine with Vista, but when I've reinstalled on machines dual-booting XP & Ubuntu, I've deleted the Ubuntu partition with gparted and then run the install, grub has installed correctly.

Just one thought: how have you installed Intrepid? Via wubi or in its own partition?

EDIT: I repeat the warning by 3Miro: the method I suggested will also destroy Intrepid's data.

BACKUP BACKUP BACKUP: can't say it enough. Make sure you have the means to recover Vista and/or your data!

---

### Post by Crafty Kisses on 2009-04-25
In my experience updating by using "dist-upgrade" can save a lot of time, but in other cases it just doesn't work, and then if it doesn't work I would need to do a reinstall anyway. In theory dist-upgrade should work fairly well, but there have been a couple of stories that turn me off. I would prefer a fresh install.

---

### Post by Crafty Kisses on 2009-04-25
For the two questions asked, I want Intrepid gone. For the second question Ubuntu has it's own boot. I didn't use Wubi, and of course all my data is backed up, I ALWAYS backup my data.

---

### Post by ninjapirate89 on 2009-04-25
> **Codename said:**
> In my experience updating by using "dist-upgrade" can save a lot of time, but in other cases it just doesn't work, and then if it doesn't work I would need to do a reinstall anyway. In theory dist-upgrade should work fairly well, but there have been a couple of stories that turn me off. I would prefer a fresh install.

I did an upgrade and everything went just fine. No issues whatsoever. However I later decided to do a clean install so that I could use ext4.

---

### Post by spiderbatdad on 2009-04-25
hey codename.
I usually prefer fresh install myself. Decided to run dist upgrade this time. It worked excellently with. ```
sudo update-manager -d
```

---

### Post by snowpine on 2009-04-25
I think you are jumping to conclusions, nothing wrong with upgrading your existing install. Why not try it the easy way first, then if you are not satisfied with the results, try it the hard way? :)

---

