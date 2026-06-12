---
title: "/tmp... no space left on device"
date: 2009-04-28
forum: General Help
---

### Post by lnajt on 2009-04-28
Does anyone know how to fix this error:


mdl.y:795: fatal error: error writing to /tmp/ccRmZ4fF.s: No space left on device
compilation terminated.

Firefox and Seamonkey have been giving me similar errors when I try to download files by left clicking on hyperlinks (rightclick>save-as works fine.)

I'm running Jaunty, and there's plenty of space on my drive.

---

### Post by taurus on 2009-04-28
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
df -h
```

p.s.  Did you have a separate partition for /tmp?

---

### Post by lnajt on 2009-04-28
/dev/sda1             107G   99G  2.4G  98% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  232K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  176K 1006M   1% /dev
tmpfs                1007M  112K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  864K  160K  85% /tmp
/dev/sdb1             299G  296G  2.6G 100% /media/OneTouch 4_
/dev/sda3             2.6G  2.3G  115M  96% /media/disk

No, to my knowledge I don't have a seperate partition. 

Is 1 Megabyte a particularly small size for /tmp?

---

### Post by taurus on 2009-04-28
> **lnajt said:**
> **[COLOR="Red"]/dev/sda1             107G   99G  2.4G  98% /[/COLOR]**
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  232K 1006M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  176K 1006M   1% /dev
tmpfs                1007M  112K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  864K  160K  85% /tmp
/dev/sdb1             299G  296G  2.6G 100% /media/OneTouch 4_
/dev/sda3             2.6G  2.3G  115M  96% /media/disk

No, to my knowledge I don't have a seperate partition. 

Is 1 Megabyte a particularly small size for /tmp?

You are about to max out your root partition--/.  You need to do some house cleaning.  

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Also, look in /var to make sure you don't have anything big, especially /var/backups.

```
sudo du -h /var
```
Don't forget to empty your trash bin to reclaim the space and delete files that you don't need anymore in your $HOME.

---

### Post by lnajt on 2009-04-29
The output of df -h didn't change substantially after cleaning up, but after restarting my computer this problem fixed its self, and I can compile my code.

Thanks for your help anyway.

---

