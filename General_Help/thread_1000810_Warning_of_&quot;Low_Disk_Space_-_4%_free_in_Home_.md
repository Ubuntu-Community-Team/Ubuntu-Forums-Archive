---
title: "Warning of &quot;Low Disk Space - 4% free in Home Partition&quot;"
date: 2008-12-03
forum: General Help
---

### Post by flutti-tutti on 2008-12-03
I am getting a warning "Low Disk Space", showing that "you are running low on disk space on your home partition (currently 4% free) ... ". 

My home partition has a 80GB space, and "System Monitor" shows 807 MB out of 5.7 GB in RAM memory and 4.0 KB of 3.0 GB in Swap.  My system is Ubuntu 8.04 (AMD64) with Kubuntu-Desktop.

I don't see any reason why I am getting the above warning. Could that be a sign of a big problem?  

Would appreciate any suggestions on where to begin for fixes.
(I have spent a lot of time to fine-tune my system, so I do not want to reinstall the OS.)

---

### Post by philinux on 2008-12-03
Post the result of this command.

```
df -h
```

---

### Post by taurus on 2008-12-03
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by flutti-tutti on 2008-12-03
Thanks for your response.

The output of "df -h" is:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              69G   64G  2.1G  97% /
varrun                2.9G  176K  2.9G   1% /var/run
varlock               2.9G     0  2.9G   0% /var/lock
udev                  2.9G   56K  2.9G   1% /dev
devshm                2.9G     0  2.9G   0% /dev/shm
lrm                   2.9G   44M  2.9G   2% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb1             3.8G  186M  3.6G   5% /media/KINGSTON

Now, I see the problem, but there is no way to use up that much space. please advise what to do.

---

### Post by taurus on 2008-12-03
> **flutti-tutti said:**
> Thanks for your response.

The output of "df -h" is:

Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Blue"]/dev/sda2              69G   64G  2.1G  97% /[/COLOR]**
varrun                2.9G  176K  2.9G   1% /var/run
varlock               2.9G     0  2.9G   0% /var/lock
udev                  2.9G   56K  2.9G   1% /dev
devshm                2.9G     0  2.9G   0% /dev/shm
lrm                   2.9G   44M  2.9G   2% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb1             3.8G  186M  3.6G   5% /media/KINGSTON

Now, I see the problem, but there is no way to use up that much space. please advise what to do.

Your $HOME is part of the root filesystem, /.  Make sure you empty your trash bin (and that includes the one for root as well) to free up some spare.  Also, clean out the cache too.

```
sudo apt-get clean
df -h
```

---

### Post by flutti-tutti on 2008-12-03
thanks for the suggestion.

the directory, home/"user name"/.strigi, was found to be the one taking more than 90% of the disk space.  After emptying the trash bin, the space usage is reduced to 11%.
Thanks a lot!

---

