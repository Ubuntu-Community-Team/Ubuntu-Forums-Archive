---
title: "HDD Full, Cannot Login"
date: 2009-04-29
forum: General Help
---

### Post by wilhelm on 2009-04-29
Hello, 

I am running kubuntu 7.10

Last night my harddrive got filled up to 100%, this morning I was still able to remove some files to clean up space. I then rebooted because KDE kept giving errors on some services not running.

After the reboot, I cannot login. The xserver just restarts, and gives me the login prompt again. Failsafe doesn't work, neither does console login.

I am able to connect remotely via ssh 

This is my current disk usage:

root@null:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  136G     0 100% /
varrun               1010M  264K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   76K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-16-generic/volatile
/dev/sdb1             233G   18G  216G   8% /media/manni
overflow              1.0M  4.0K 1020K   1% /tmp


There seems to be about 5gb available that I cleaned up. But it still shows as 100% used.

Any ideas?

wdp

---

### Post by zeex on 2009-04-29
> **wilhelm said:**
> Hello, 

I am running kubuntu 7.10

Last night my harddrive got filled up to 100%, this morning I was still able to remove some files to clean up space. I then rebooted because KDE kept giving errors on some services not running.

After the reboot, I cannot login. The xserver just restarts, and gives me the login prompt again. Failsafe doesn't work, neither does console login.

I am able to connect remotely via ssh 

This is my current disk usage:

root@null:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  136G     0 100% /
varrun               1010M  264K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   76K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-16-generic/volatile
/dev/sdb1             233G   18G  216G   8% /media/manni
overflow              1.0M  4.0K 1020K   1% /tmp


There seems to be about 5gb available that I cleaned up. But it still shows as 100% used.

Any ideas?

wdp

Hi, 

Boot from live CD and run file check on / . let's say it's /dev/sda1 then 

```
$ sudo fsck /dev/sda1 
```

and then reboot .

---

### Post by Bindsa on 2009-04-29
I had the same problem, I solved it this way:

I booted up a fail-safe terminal and just removed some packages, if that doesn't work there is something wrong with your filesystem I guess.

Hope this helped you.

--
B!ndsa

---

### Post by wilhelm on 2009-04-29
I will try the suggestions thanks

---

### Post by wilhelm on 2009-04-29
Well after 2 more reboots it made the auto fsck after usual 30 mounts. This took a bit longer that usual I guess but still no success. 

df still gives me the same stats.
Busy getting dsl now, to check if I can run fsck -f from there...

---

### Post by kpkeerthi on 2009-04-29
There is no need to run fsck when your disk is full. It just helps clear errors with improperly unmounted disks.

---

### Post by kpkeerthi on 2009-04-29
```

/dev/sda1 142G 136G 0 100% /

```

Ubuntu (ext3, actually) reserves 5% (7.1 GB in your case) of the space for its own book keeping chores. So 142 GB - 136GB = 6GB free is still not good enough.

From GRUB, boot into Recovery Mode and then run these commands:
```
sudo apt-get autoremove
sudo apt-get clean

``` and see if it frees up some space. If not consider uninstalling packages you don't need and move some stuffs to additional drive if you have one.

Also consider, [uninstalling kernels you no longer use]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") (when you are back at your desktop).

---

### Post by wilhelm on 2009-04-29
well that is exactly my problem, it isn't really full.

I deleted about 5Gb of old iso images from the drive to clear up space. The problem is that it is not recognised.

Is there perhaps a way I would be able to empty the KDE Trash, from CL?

---

### Post by kpkeerthi on 2009-04-29
So when you deleted the ISOs, they were actually moved to Trash?

---

### Post by wilhelm on 2009-04-29
That I cannot confirm, the trash can kept saying it was empty.
Even though I sent some file to trash.

---

### Post by wilhelm on 2009-04-29
Ok I am going to remove some more files, then I'll check what happens. 

Thanks

---

### Post by wilhelm on 2009-04-29
Well that did it. After removing another 2GB I have 64mb available.

So I am able to log in. Thanks for the help.

I will need to get an additional drive for these recovery jobs :P

---

