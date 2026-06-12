---
title: "Forced Hard Drive Check VERY Slow"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by samurailink3 on 2007-06-24
Every 29 times I boot up my PC (Dell 1505N - Ubuntu Preinstalled), it runs a Hard Drive check (via fsck I believe...). My desktop running Feisty did this as well, but the check only took a couple minutes or so. This one takes a little over an hour, same hard drive size (160GB), but it takes FOREVER! Is there any way I can speed this up or just turn the checks off completely. I don't want to need my compy real quick and get stuck at an fsck progress bar. Thanks!

---

### Post by AtrejuT on 2007-06-24
I don't know why it is slow but its easy to turn off:
In a console enter
```

sudo tune2fs -c 0

```

However I don't find this particularly recommendable if you have valuable data on that drive - 
on my computer I set the number of mounts before checking to 70 instead of 30 and I can live with that quite well. the command is the same:
```

sudo tune2fs -c 70

```

---

### Post by HermanAB on 2007-06-24
Hmm, be careful.  What kind of file system are you using?  The command 'mount' will tell you.  The best file systems are Ext3 and JFS.  Ext2 can be converted to Ext3.

---

### Post by fjgaude on 2007-06-24
> **samurailink3 said:**
> Every 29 times I boot up my PC (Dell 1505N - Ubuntu Preinstalled), it runs a Hard Drive check (via fsck I believe...). My desktop running Feisty did this as well, but the check only took a couple minutes or so. This one takes a little over an hour, same hard drive size (160GB), but it takes FOREVER! Is there any way I can speed this up or just turn the checks off completely. I don't want to need my compy real quick and get stuck at an fsck progress bar. Thanks!

You can use:  sudo tune2fs -c 0  /dev/sda where sda is your boot partition to stop it from checking.

But likely your new Dell is just fixing the disk after all the files have been put onto it. fsck can do automatically a lot of good things to make your disk run better. So, set the tune2fs to 100 or less. The next time the check occurs see how much faster it goes.

frank

---

### Post by isionous on 2007-08-11
> **fjgaude said:**
> 
But likely your new Dell is just fixing the disk after all the files have been put onto it. fsck can do automatically a lot of good things to make your disk run better. So, set the tune2fs to 100 or less. The next time the check occurs see how much faster it goes.


My fsck forced check at bootup is ALWAYS extremely slow and always gets stuck for minutes at the same percentages.  This problem is only on my Dell E1505 with Ubuntu preinstalled.  I think there is something else going on than just fsck doing "automatically a lot of good things".  Is it possible that how they've partitioned the machine is contributing to this problem?  This problem is unique to my Dell E1505 laptop that came with Ubuntu preinstalled.  My other machines have much much faster fsck check times.

Here's some info from the df command:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             144G   50G   87G  37% /
varrun                502M  240K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  128K  502M   1% /proc/bus/usb
udev                  502M  128K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
/dev/sda3             193M   37M  147M  20% /boot
tmpfs                 502M   33M  469M   7% /lib/modules/2.6.20-16-generic/volatile

```

And the mount command:

```

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda3 on /boot type ext3 (rw)
tmpfs on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

I'd love to hear any theories on how to fix the long fsck times.

---

### Post by timseal on 2007-08-24
my 1420N is the same, it's 28% through a 10GB partition and it's taken 15 minutes so far.

---

