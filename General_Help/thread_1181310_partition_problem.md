---
title: "partition problem"
date: 2009-06-07
forum: General Help
---

### Post by beatvsrhythm on 2009-06-07
greetings, ubuntu gurus! 

here's my problem: i had a 640gig external hard drive plugged in when i installed ubuntu, and it seems that i somehow accidentally installed ubuntu onto it instead of onto my 500gig internal hard drive. (at least, i'm pretty sure i did; i've attached gparted's maps of both drives). now, i can't boot without the external plugged in, i have a big chunk of wasted space on my internal hdd and if my external dies i'll lose *everything*! to make matters worse, my ubuntu installation is now just barely small enough to fit in the space where i had meant for it to go on the internal hdd. 

so, should i buy a new internal hard drive that's large enough to hold both my windows and ubuntu installations? if so, is there a program or something that would allow me to copy my windows partition to the new drive?

or, would it be possible to copy my ubuntu installation to a new internal drive (again, is there a program for this?) and have it plugged in and available alongside my windows hdd?

i'm pretty new to linux and i'm probably thinking about this all wrong, so anything you can suggest would be enormously helpful. :)

---

### Post by labinnsw on 2009-06-07
You can install Ubuntu in the free space on the internal HDD then copy the boot directory (/boot) and fstab (/etc/fstab) to the backup partition.

**Reboot with a Live CD or into the external Ubuntu**

Copy the existing Ubuntu files to the internal HDD overwriting the new installation.

Over write the boot directory and fstab with the ones you backed up earlier.

Reboot to test and make sure it all works. If it does you can delete the External HDD Ubuntu.

On the internal HDD you may have a problem using that much space for Ubuntu dual booting with Windows. Windows might not start. I was able to get it working with a partition size of 70 GiB allocated to Ubuntu.

---

### Post by lindsay7 on 2009-06-07
I think what happened is the space you wanted to use for Ubuntu was unallocated space. It there would have been a partition established there, Ubuntu could have found it. Any way, you should use Gparted and partition that unallocated space. You could break it up into two partitions. If you want to install Ubuntu again, I would unplug the external drive first, If you set up two partitions on the unallocated space you could install the root or / directory to one of then and make the other the/home directory. You could then delete the Ubuntu installation on the external drive and use that partition as a place for data etc.

---

### Post by labinnsw on 2009-06-07
> **lindsay7 said:**
> I think what happened is the space you wanted to use for Ubuntu was unallocated space. It there would have been a partition established there, Ubuntu could have found it. 

Not quite, I installed Jaunty recently and all my partitions were recognized. (allocated and unallocated, Windows and Hardy)

[ATTACH]116820[/ATTACH]

---

### Post by beatvsrhythm on 2009-06-08
thank you for your help! i have a couple more questions though: 

> **labinnsw said:**
> You can install Ubuntu in the free space on the internal HDD then copy the boot directory (/boot) and fstab (/etc/fstab) to the backup partition. did you mean that i should copy the /boot and fstab directories from the new, internal installation or from the existing external one?

and 

> **labinnsw said:**
> Copy the existing Ubuntu files to the internal HDD
the existing files would be my /home directory, right?


and finally, would these steps also work if i wanted the new ubuntu installation to be on a newly-purchased internal hdd?

thanks again.

---

### Post by labinnsw on 2009-06-09
> did you mean that i should copy the /boot and fstab directories from the new, internal installation or from the existing external one?

Yes. After you overwite the partition you will need to replace them

> the existing files would be my /home directory, right?

No. I mean't the entire external system. (Although if you only copy the home directory, you will not need to save /boot directory and fstab.)

But if you replace the /home directory only, open a terminal (applications >> Accessories >> Terminal) and type:
```
chmod 644 .dmrc
chmod 700 ~
```
Otherwise you will get errors when you reboot.

After that you can ignore the rest of the process. 

> and finally, would these steps also work if i wanted the new ubuntu installation to be on a newly-purchased internal hdd?

Yes

---

