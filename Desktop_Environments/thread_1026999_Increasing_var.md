---
title: "Increasing /var"
date: 2008-12-31
forum: Desktop Environments
---

### Post by visitnag on 2008-12-31
Dear all,

I have a 250gb, seagate sata disk. I have dedicated 25gb to ubuntu. While partitioning for ubuntu mistakenly i gave only 600mb of space to /var partition. Now when i am going to install a new software the system is not letting me to install by giving an error message like "Not enough disk pace, cannot continue the installation" or "not enough space in /var".

Can i repartition the /var partition giving more space. Acually i hav /usr3 partition of 1.3gb. I dont need this can i merge /var and /usr3 as /var? Then i can get more space for /var Guide me..thank you in advance

The following is my df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda14             9614116   2293740   6832004  26% /
tmpfs                   248612         0    248612   0% /lib/init/rw
varrun                  248612        92    248520   1% /var/run
varlock                 248612         0    248612   0% /var/lock
udev                    248612      2852    245760   2% /dev
tmpfs                   248612       388    248224   1% /dev/shm
lrm                     248612      2000    246612   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda9               186663     17789    159237  11% /boot
/dev/sda10             5763616    945668   4525168  18% /home
/dev/sda11             5763616    173068   5297768   4% /usr1
**/dev/sda15             1470492     35012   1360780   3% /usr3**
**/dev/sda12              381138    378993         0 100% /var**
varun@varun-desktop:~$

---

### Post by captain_171 on 2008-12-31
There is a program called Gparted
what works the best for me is to get the Live CD of this and boot into that and then resize the partition
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Let me know if that works

---

### Post by snova on 2008-12-31
Try cleaning out the package cache:

```
sudo apt-get clean
```

As a temporary fix. Or even a permanent one- 600 MB is about twice the size that mine takes up, that should be enough. (Well, it also depends on what you do...)

---

### Post by Rohan Kapoor on 2009-01-01
> **captain_171 said:**
> There is a program called Gparted
what works the best for me is to get the Live CD of this and boot into that and then resize the partition
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Let me know if that works

Gparted is built in to the Ubuntu 8.10 discs! System->Administration->Partition Editor is it's location.

---

### Post by visitnag on 2009-01-01
i have installed gparted in my system...but how to increase my /var?

---

### Post by Rohan Kapoor on 2009-01-01
> **visitnag said:**
> i have installed gparted in my system...but how to increase my /var?
You know the other partition that you don't need. I think you called it /usr3. You delete that and the /var partition. Then make a new partition for /var that uses up all of that space!

It's fairly straight-forward once you start using it!

---

