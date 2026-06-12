---
title: "Moving /usr folder"
date: 2009-03-09
forum: General Help
---

### Post by sbcontt on 2009-03-09
While installing I accidentally allocated a full partition sda4 for /usr instead of /home :(, it is a complete waste of space on sda4. I want to move it to sda3 . Is it possible? I´ve heard that moving /usr renders installation corrupted. can anyone help?

---

### Post by sdennie on 2009-03-09
I'm not completely sure what you mean.  Can you post the output of:

```

df

```

It's possible that you've done nothing wrong.  And it's very likely that if you have done something wrong, it's very easy to fix.

---

### Post by sbcontt on 2009-03-09
> **sdennie said:**
> I'm not completely sure what you mean.  Can you post the output of:

```

df

```

It's possible that you've done nothing wrong.  And it's very likely that if you have done something wrong, it's very easy to fix.

Here is the output:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             15638836   2594772  12249652  18% /
tmpfs                   963908         0    963908   0% /lib/init/rw
varrun                  963908       108    963800   1% /var/run
varlock                 963908         0    963908   0% /var/lock
udev                    963908      2784    961124   1% /dev
tmpfs                   963908       604    963304   1% /dev/shm
lrm                     963908      2384    961524   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda4             15560556   2916956  11853208  20% /usr
/dev/sda1             31776536  21337500  10439036  68% /media/disk

```

---

### Post by bbabu84 on 2009-03-09
> **sbcontt said:**
> While installing I accidentally allocated a full partition sda4 for /usr instead of /home :(, it is a complete waste of space on sda4. I want to move it to sda3 . Is it possible? I´ve heard that moving /usr renders installation corrupted. can anyone help?

It is easiest to do this with the Live CD.  Boot with the CD, and run the following commands (comments after # in each line)
in a terminal:

sudo su   # become superuser
mkdir /mnt/3 /mnt/4   # create dirs for mount
mount /dev/sda3 /mnt/3
mount /dev/sda4 /mnt/4
cd /mnt/4     # cd to the usr directory
cp -iax . /mnt/3/usr  # copy all files
vi /mnt/3/etc/fstab   # edit fstab and comment out line for /usr with a # in front
cd /
umount /mnt/3 /mnt/4

Once you reboot, /usr will no longer be a separate partition.  You can change /usr entry to /home, as long as you copy the files from /mnt/4/home to /mnt/3 also.  All this can be done without booting from a Live CD, but it can be a little tricky

---

### Post by sdennie on 2009-03-09
Essentially, what you will need to do is boot into a LiveCD (the disk you used to install Ubuntu will be fine), drop to a terminal and mount / and /usr.  Once there, use tar to create an archive of the mounted /usr and then extract it on the mounted ./  Then modify the mounted /etc/fstab to no long mount /usr.  When you reboot, everything should be just fine and you will have an unmounted partition (previously /usr) that you can format and mount however you like.

These directions are correct but vague.  If you need more help, post back and I can give more detailed instructions.

Edit:
Hah!  I see while writing my vague instructions someone has posted more detailed instructions.

---

### Post by sbcontt on 2009-03-09
Thank you all for helping me solve the problem.
For archiving purpose:
```

First I followed bbabu84 ´s method but found that it has not copied the contents of sda4 (old /usr) to the new /usr in sda3. I may have done something wrong. I tried to do the copying from console, got frustrated, typed sudo nautilus & copied the files from sda4 to /usr on sda3 on GUI. Done. Now I´m posting this from that Ubuntu installation.

```

---

