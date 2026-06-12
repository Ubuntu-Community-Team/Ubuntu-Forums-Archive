---
title: "operation not permitted (permissions/owner/group)"
date: 2009-01-24
forum: General Help
---

### Post by kaligus on 2009-01-24
I just upgraded several fully working Hardy systems to Intrepid... all went mostly perfectly.

One system however now has some files which cant be deleted causing issues for me and dpkg.

there are several files in /lost+found (posted below)  I have tried removing these files using every method I can think of (sudo, sudo nautilus, sudo -i) to be root.

then hpodder failed to upgrade and has caused no shortage of problems due to another

*** paste of hpodder file
root@bigwill:/var/lib/dpkg/info# dir hpodder*
 0 -rw-rw-rw- 1 root   root     0 2009-01-23 23:12 hpodder.list
24 -r-xr--r-- 1 131072 klog 45056 2007-10-30 21:52 hpodder.md5sums

The first one is fine as far as I know, the second is listed in the dpkg error posted here

*** begin paste of dpkg error
root@bigwill:/var/lib/dpkg/info# dpkg -P --force-all hpodder
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 294964 files and directories currently installed.)
Removing hpodder ...
dpkg: error processing hpodder (--purge):
 unable to delete control info file `/var/lib/dpkg/info/hpodder.md5sums': Operation not permitted
Errors were encountered while processing:
 hpodder
root@bigwill:/var/lib/dpkg/info#


*** paste of files in /lost+found
 84 -r-xr-x---  1  3014769 gdm           110592 2008-04-17 09:25 #18383741
104 -r--r-xrwx  1 boinc    mlocate       110592 2002-02-13 11:16 #18384325
 76 -r-xrw--w-  1 boinc               57 110592 2007-08-03 14:58 #18391208
 12 -r--------  1  1835121 plugdev        45056 2007-08-03 14:59 #18391215
 24 -r--------  1  8847473            90  28672 2007-08-03 15:01 #18391216
 92 -rw---xr-x  1  7209073 winbindd_priv 110592 2007-08-03 15:01 #18391249
 88 -r-xrw--wx  1  6619249            97 110592 2007-08-03 14:58 #18391254
 84 -r--------  1 13107313 klog          110592 2007-09-20 14:30 #18391820
 92 -r-xrw--wx  1  7864433            84 110592 2007-08-06 00:57 #18391850
 88 -r-xr----x  1  6881393            69 110592 2007-08-06 00:57 #18391851
 92 -r-x-wxrwx  1  7209073            95 110592 2007-08-06 00:57 #18391858
 24 -rwxrwxrwx  1 13041777 kmem           45056 2007-08-06 00:56 #18391923
108 -r-xrw----  1  7340145 crontab       110592 2008-07-13 13:45 #18392009
 92 -r-xr-x--x  1  6357105 users         110592 2008-07-13 13:45 #18392015
 80 -r--------  1  1048576 gdm           110592 2008-04-03 09:01 #6276879
  4 -r-x------  1 root     root             870 2008-04-03 09:01 #6276880
 84 -r--------  1  1048576 gdm           110592 2008-04-03 09:01 #6276881
 80 -rw-------  1  4194304           224 110592 2008-04-03 09:01 #6283582

---

### Post by mssever on 2009-01-24
Stuff in lost+found is usually the result of filesystem corruption. The fact that lost+found isn't empty is cause for concern. You should definitely run an fsck, and possibly a hard disk test.

As far as removing those files goes, just do ```
sudo rm /the/file
```If that doesn't work, then post the exact error message you get.

For the hpodder package error, the permissions on hpodder.md5sums are weird (544). Change them to 644 and that problem should hopefully be cured: ```
sudo chmod 644 /var/lib/dpkg/info/hpodder.md5sums
```

The big question is, how did the permissions get messed up in the first place?

---

### Post by kaligus on 2009-01-24
> **mssever said:**
> Stuff in lost+found is usually the result of filesystem corruption. The fact that lost+found isn't empty is cause for concern. You should definitely run an fsck, and possibly a hard disk test.


Since this is my / partition I went so far as to boot the system rescue cd ([http://www.sysresccd.org/](http://www.sysresccd.org/)) and try to remover all files by brute force.  Ran a test of the drive from a manufacturers cd, etc. all say the hard drive is perfectly fine (the errors are all on the same physical device, same partition).



> **mssever said:**
> As far as removing those files goes, just do ```
sudo rm /the/file
```If that doesn't work, then post the exact error message you get.


```

will@bigwill:/lost+found$ sudo chmod 666 *
chmod: changing permissions of `#18383741': Operation not permitted
chmod: changing permissions of `#18384325': Operation not permitted
chmod: changing permissions of `#18391208': Operation not permitted
chmod: changing permissions of `#18391215': Operation not permitted
chmod: changing permissions of `#18391216': Operation not permitted
chmod: changing permissions of `#18391249': Operation not permitted
chmod: changing permissions of `#18391254': Operation not permitted
chmod: changing permissions of `#18391820': Operation not permitted
chmod: changing permissions of `#18391850': Operation not permitted
chmod: changing permissions of `#18391851': Operation not permitted
chmod: changing permissions of `#18391858': Operation not permitted
chmod: changing permissions of `#18391923': Operation not permitted
chmod: changing permissions of `#18392009': Operation not permitted
chmod: changing permissions of `#18392015': Operation not permitted
chmod: changing permissions of `#6276879': Operation not permitted
chmod: changing permissions of `#6276880': Operation not permitted
chmod: changing permissions of `#6276881': Operation not permitted
chmod: changing permissions of `#6283582': Operation not permitted
will@bigwill:/lost+found$

```

> **mssever said:**
> For the hpodder package error, the permissions on hpodder.md5sums are weird (544). Change them to 644 and that problem should hopefully be cured: ```
sudo chmod 644 /var/lib/dpkg/info/hpodder.md5sums
```


```

will@bigwill:/var/lib/dpkg/info$ sudo chmod 666 hpodder.md5sums
chmod: changing permissions of `hpodder.md5sums': Operation not permitted
will@bigwill:/var/lib/dpkg/info$ sudo rm hpodder.md5sums
rm: cannot remove `hpodder.md5sums': Operation not permitted
will@bigwill:/var/lib/dpkg/info$

```


I went to bed while this machine (my personal machine no less LOL) upgraded so I dont know how/why  it happened, but when I rebooted as instructed I got the dreaded CLI session telling me something had gone wrong and fsck etc... I powered down and immediately rebooted with a known fresh good version of the sysrescd in hand (3 or so days old to help my father-in-law recover from his 2nd virus of the year/month...), then the manufacturers CD to make sure the drive is good and well, then Intrepid again which had forgotten about it's troubles but the files are still in /lost+found (and yes I tried them from sysrescd too)

I can not find anything in any of the log files indicating a problem, but I havent rebooted in months (probably 6).  Hpodder and everything else worked perfectly yesterday.

Everything is working fine today except that I cant install or uninstall anything because of the error, including hpodder which I ran once just to make sure I could say that LOL.

My next theory is to try and find a disk sector editor (maybe one already on sysrescd if I look) and figure out how to hard edit the hpodder file (the rest just annoy me but dont seem to be affecting anything else)

---

### Post by The Cog on 2009-01-24
I would check the permissions on the lost+found directory itself. And check if the filesystem is mounted readonly. The mount command might tell you. I think fstab says something like errors=remount-ro. So you may need to do a succesful fsck before you can mount properly again.

---

### Post by Yashiro on 2009-01-24
Run fsck on the hard drive after booting into the CD live environment.

---

### Post by mssever on 2009-01-24
As The Cog says, check whether your filesystem is mounted read-only (ro). If so, you can do ```
sudo mount -o remount,rw /
```to remount it read-write.

Regardless, make sure you have a good backup. If you keep having these problems after running fsck, you'll likely have to reformat the partition. It looks like something might be seriously hosed.

---

### Post by kaligus on 2009-01-24
I am running on the system, and it is mounted RW

lost+found is drwxrwxrwx (777)

I have a fresh backup daily but reformatting and reinstalling sounds like a MS answer especially when no cause is known.

Somehow /var/lib/dpkg/info/hpodder.md5sums came to be owned by user# 131072 in group klog a task which apparently even root CAN-NOT do or undo.

Somehow /lost+found came to be full of files similarly owned or grouped exotically.

Formatting and starting over seems to me to be more than a little out of control until the reasons are understood.

---

### Post by mssever on 2009-01-24
> **kaligus said:**
> I am running on the system, and it is mounted RW

lost+found is drwxrwxrwx (777)

I have a fresh backup daily but reformatting and reinstalling sounds like a MS answer especially when no cause is known.

Somehow /var/lib/dpkg/info/hpodder.md5sums came to be owned by user# 131072 in group klog a task which apparently even root CAN-NOT do or undo.

Somehow /lost+found came to be full of files similarly owned or grouped exotically.

Formatting and starting over seems to me to be more than a little out of control until the reasons are understood.
Files end up in lost+found as the result of a filesystem error. See [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html) for some (somewhat outdated) info. If you're using ext3 instead of ext2, then an unclean shutdown is probably insufficient.  Somehow, it appears that your filesystem got corrupted, and fsck hasn't been able to fully fix it. Unless you can persuade fsck to fix your problems, I don't think that you have very many options.

However, reformatting doesn't necessarily mean reinstalling. Assuming you have adequate disk space, you could try the following from a live CD:
```
# Mount both your root partition and an ext2/3 partition somewhere (e.g., /mnt/root and /mnt/backup)
sudo cp -a /mnt/root /mnt/backup  # The -a option preserves ownership, permissions, special files, etc.
sudo umount /mnt/root
# Reformat your root partition, then mount it
sudo cp -a /mnt/backup /mnt/root
# You should now be able to fix your permissions, and everything should be restored without a reinstall
```

---

### Post by kaligus on 2009-02-01
Well I finally just started fresh (root only) as everything else seemed ok and there was too much work moving stuff around to make space to copy root.

marking it solved...

---

