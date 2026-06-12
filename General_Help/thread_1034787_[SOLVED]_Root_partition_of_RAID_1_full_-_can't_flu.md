---
title: "[SOLVED] Root partition of RAID 1 full - can't flush"
date: 2009-01-09
forum: General Help
---

### Post by miromiro on 2009-01-09
I recently installed Ubuntu 8.10 using a RAID 1. Current output of df -h is:

```

jr@machine:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               19G   18G  2.6M 100% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  128K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.9M  1.7G   1% /dev
tmpfs                 1.7G   12K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-8-generic/volatile
/dev/md2              892G   59G  788G   7% /home
/home/jason/.Private  892G   59G  788G   7% /home/jason/Private

```

I can't for the life of me figure out why md0 is full -- but whatever it is it is preventing me from doing pretty much anything on the machine.

I have tried rebooting after following this advice: [http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_clean_.2Ftmp.2F_folder_contents_on_shutdown](http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_clean_.2Ftmp.2F_folder_contents_on_shutdown) but to no avail.

Any and all help *really* appreciated at this point...

---

### Post by hyper_ch on 2009-01-09
(1) open a terminal

(2) run
```

cd /
sudo touch output.txt
sudo chmod 0666 output.txt
du -h > output.txt

```
and post the content of the output file here.

---

### Post by miromiro on 2009-01-09
Thanks hyper_ch.

I think I have sorted it: seems it is related to a problem with Simple Backup which I have been running for the last 2 days (documented here: [http://www.blog.arun-prabha.com/2008/07/22/deleting-files-from-roots-trash-folder-in-ubuntu/](http://www.blog.arun-prabha.com/2008/07/22/deleting-files-from-roots-trash-folder-in-ubuntu/)) - so it was a case of deleting Trash in /root/ (as found here: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)).

Unistalling Simple Backup now... [edit] package is actually called pybackpack [/edit]

Cheers,

/J

---

