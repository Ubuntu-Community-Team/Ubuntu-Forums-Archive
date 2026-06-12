---
title: "Tried backup, now / folder is full"
date: 2009-05-13
forum: General Help
---

### Post by lsutiger on 2009-05-13
I really need some help here peeps!

My laptop's hard drive is partitioned so:
/ is on partition 0, /home is on partition 1
I was trying to backup because I have been having some problems with a stable system  of years. 

Well, I tried to run a backup with sbackup to a network drive (smb to another Ubuntu machine). It started fine, but stopped updating the backup file on the other machine. I ran df -h and here what I got:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  9.3G     0 100% /
varrun                950M  228K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   44K  950M   1% /dev
devshm                950M   24K  950M   1% /dev/shm
lrm                   950M   39M  911M   5% /lib/modules/2.6.24-23-generic/volatile
/dev/sda2             173G  103G   64G  62% /home
overflow              1.0M  364K  660K  36% /tmp
gvfs-fuse-daemon      9.3G  9.3G     0 100% /home/complexity/.gvfs
/dev/scd0             699M  699M     0 100% /media/Ubuntu 9.04 i386

```

So now my / is 100% full. I have no idea what happened here. I can not find the file that is filling up my / partition. 
I had 4+ GB free before this. 

How can I find it? Please help!

---

### Post by lsutiger on 2009-05-13
After googling some, I found this to be a common problem with sbackup on networked drives, but that does not fix my problem of / being full. I decided to pull the hard drive on the other networked computer and mount it via usb. 

Now the question arises...do I install 9.04 or stick with 8,04?
What do you all think?
Is the ext4 file system really that much faster? What are the cons/pros to upgrading to 9.04?
thanx in advance!

---

### Post by KhurramM on 2009-05-13
I have made errors my self many a times.

But then I learned one thing.

Keep the running system RUNNING.

Install the new kernel.

Test drive new kernel.

If it delivers what u require, delete away the older one.

This happened to me on my opensuse10.2, I am still using it, though 11.1 is there.

I am still using hardy, but jaunty is under testing.

Goodluck..................

---

### Post by lsutiger on 2009-05-13
Thanx for the reply. Go to [this link]("http://ubuntuforums.org/showthread.php?t=1157596") and click on the two links within that post.

My system has been acting funky and I have no idea why.
So I am doing a complete backup/install/restore
I just want to make sure that I have a backup before I do anything

---

