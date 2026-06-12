---
title: "making room in tmp file"
date: 2009-04-05
forum: General Help
---

### Post by imparja2 on 2009-04-05
There is currently only 56kb worth of data in this file yet when I go to a download a pdf 546kb it says the tmp file is full how can that be? Have I perhaps limited the amount that this file can store. How do I make this file store more? And I can't just save it elsewhere for some reason

---

### Post by taurus on 2009-04-05
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by imparja2 on 2009-04-05
branden@branden-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             7.4G  7.4G     0 100% /
varrun                248M  108K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   60K  248M   1% /dev
devshm                248M  168K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              29G   14G   14G  51% /home
overflow              1.0M  964K   60K  95% /tmp
gvfs-fuse-daemon      7.4G  7.4G     0 100% /home/branden/.gvfs

---

### Post by taurus on 2009-04-05
> **imparja2 said:**
> branden@branden-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
**/dev/sda1             7.4G  7.4G     0 100% /**
varrun                248M  108K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   60K  248M   1% /dev
devshm                248M  168K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              29G   14G   14G  51% /home
overflow              1.0M  964K   60K  95% /tmp
gvfs-fuse-daemon      7.4G  7.4G     0 100% /home/branden/.gvfs

You are maxing out your root partition.  You need to do some house cleaning.

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Make sure you empty trash bin (for root) also.

---

### Post by imparja2 on 2009-04-05
branden@branden-laptop:~$ sudo apt-get clean
[sudo] password for branden: 
branden@branden-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
branden@branden-laptop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             7.4G  7.3G     0 100% /
varrun                248M  108K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   60K  248M   1% /dev
devshm                248M  172K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              29G   14G   14G  51% /home
overflow              1.0M  964K   60K  95% /tmp
gvfs-fuse-daemon      7.4G  7.3G     0 100% /home/branden/.gvfs

I don't think it worked is there another way?

---

