---
title: "Here is my dmesg. Care to improve my setup?"
date: 2011-02-01
forum: Desktop Environments
---

### Post by ploft on 2011-02-01
Hello, community!

I don't have an issue per se, but am here looking to improve my setup.

I run an ASUS eeepc _[1201N]("http://www.engadget.com/2009/12/18/asus-eee-pc-1201n-review/")_, dual booting Ubuntu and win7, and it was installed as 10.04 (made the Upgrade (not reinstalled) to 10.10)
I use it mainly for Mathematica/random web use/research(pdf/djvu/whatnot library)/ssh'ing to my box at home.

This is my second Ubuntu machine/install, but I still find things to customize/upgrade almost everyday, as I guess is common place amongst Linux users. Therefore, I reckon I might have a lot of 'trash' lying around the machine, slowing it down and taking up unecessary space.

Probably the most common solution is reinstalling it from scratch, and I will eventually do it once I have less work to do.
Care to guide me through the process of cleaning it up? Any common tips?

Here is the output of _[dmesg]("http://pastebin.com/SKTPA1Yi")_. Some warning I am not paying attention to? Some obvious process I can tweak to improve boot time?
```

<user>@<host>:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1759       1452        306          0        299        703
-/+ buffers/cache:        450       1309
Swap:         3071          0       3071

```
I use gnome and am only running pidgin, chrome and terminal (two tabs (one is ssh, other where I got this output)) and am connected using wifi. Why the 450MB of used memory?
I followed _[this page](https://help.ubuntu.com/community/SwapFaq)_ to set up a swap file, seeing as I had not made a separate swap partition. However, it never gets used and I cannot hibernate (don't remember being able to, previously)

```
<user>@<host>:~$ fdisk -l
(...)
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7956    63897600    7  HPFS/NTFS
/dev/sda2           13055       30399   139323712+   7  HPFS/NTFS
/dev/sda3            7957       13054    40949685   83  Linux

```
sda1: win7; sda2: storage; sda3: ubuntu

```
<user>@<host>:~$ nano /etc/fstab
# /etc/fstab
# <file system>         <mount point>   <type> <options>                                               <dump>  <pass>

proc                    /proc           proc   nodev,noexec,nosuid                                     0       0
/swapfile               none            swap   sw                                                      0       0

#/dev/sda3:
UUID=<UUID>   /         ext4      errors=remount-ro                      0       1
#/dev/sda2:
#UUID=<UUID>  /media/store    ntfs   defaults,noauto,user,nls=utf8,umask=0222,exec,rw,sync   0       0
#/dev/sda1:
#UUID=<UUID>  /media/win7     ntfs   defaults,noauto,user,nls=utf8,umask=0222,exec,rw,sync   0       0

```


What other info can I provide? Feel free to redirect me to the proper community to find what I seek.

Thank you for your feedback.

---

### Post by kn0w-b1nary on 2011-02-01
To clean up install bleachbit to remove old data
sudo apt-get install bleachbit
and install ubuntu tweak to clear cache and old packages
[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb)

Hope this helps!

---

