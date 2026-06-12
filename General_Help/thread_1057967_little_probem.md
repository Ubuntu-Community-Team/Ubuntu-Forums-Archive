---
title: "little probem"
date: 2009-02-02
forum: General Help
---

### Post by hajbal92 on 2009-02-02
I have also a question. My system is works fine except one thing. I have ubuntu 8.04. The app, wich shows the HDD (I dont know its name because i hava a hungarian ubuntu). Its name can be disk usage checker... IDK.
So this tool sees exactly the double sizes of the partitions. I just dont know how could I fix it.

Its the same with english version also. Before this distro I i had ubuntu 8.10 , and in 8.10 this app worked fine.

Thank you for your help.

Ps. sorry for my english + I will link in the screenshot of the app.

---

### Post by taurus on 2009-02-02
Looks like you are, $HOME, using a big chunk of disk space!  If you have removed stuff with nautilus, make sure you also empty the trash bin to reclaim the space.

Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by hajbal92 on 2009-02-02
> **taurus said:**
> Looks like you are, $HOME, using a big chunk of disk space!  If you have removed stuff with nautilus, make sure you also empty the trash bin to reclaim the space.

Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
df -h
```
It seems that you have misunderstood me. My problem is that this partition is 143GByte and the used space is 26GByte. But the app shows that my partition is 256 GByte, and the used space is 52 GByte... This is the only partition on my HDD

---

### Post by taurus on 2009-02-02
Then why don't you post the outputs of these commands then?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by hajbal92 on 2009-02-02
> **taurus said:**
> Then why don't you post the outputs of these commands then?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

sorry, I am a bit beginner with linux. I dont run them from terminal. I just dont see any outputs. I made a picture of it. In my first post.


Now I've run your commands:
```

hajbal92@hajbal92-laptop:~$ sudo fdisk -l
[sudo] password for hajbal92: 

/dev/sda lemez: 160.0 GB, 160041885696 bájt
255 fej, 63 szektor, 19457 cilinder
Egység: cilinderek 16065 * 512 = 8225280 bájt
Lemezazonosító: 0xf57bf57b

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Kiterjesztett
/dev/sda5           18701       19457     6080571   82  Linux lapozó / Solaris
hajbal92@hajbal92-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5f693087-4694-40dc-b804-dc736214e0c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e9674e50-21ce-41e3-9c38-2b8ffb1e6eb5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
hajbal92@hajbal92-laptop:~$ df -h
Fájlrendszer            Méret  Fogl. Szab. Fo.% Csatl. pont
/dev/sda1             143G   26G  110G  19% /
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M   24K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      143G   26G  110G  19% /home/hajbal92/.gvfs
hajbal92@hajbal92-laptop:~$ 


```

---

### Post by taurus on 2009-02-02
> **hajbal92 said:**
> sorry, I am a bit beginner with linux. I dont run them from terminal. I just dont see any outputs. I made a picture of it. In my first post.


Now I've run your commands:
```

hajbal92@hajbal92-laptop:~$ sudo fdisk -l
[sudo] password for hajbal92: 

/dev/sda lemez: 160.0 GB, 160041885696 bájt
255 fej, 63 szektor, 19457 cilinder
Egység: cilinderek 16065 * 512 = 8225280 bájt
Lemezazonosító: 0xf57bf57b

  Eszköz Indítás   Eleje         Vége      Blokkok  Az  Rendszer
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Kiterjesztett
/dev/sda5           18701       19457     6080571   82  Linux lapozó / Solaris
hajbal92@hajbal92-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5f693087-4694-40dc-b804-dc736214e0c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e9674e50-21ce-41e3-9c38-2b8ffb1e6eb5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
hajbal92@hajbal92-laptop:~$ df -h
Fájlrendszer            Méret  Fogl. Szab. Fo.% Csatl. pont
**[COLOR="Blue"]/dev/sda1             143G   26G  110G  19% /[/COLOR]**
varrun               1014M  104K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   52K 1014M   1% /dev
devshm               1014M   24K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon      143G   26G  110G  19% /home/hajbal92/.gvfs
hajbal92@hajbal92-laptop:~$ 


```

Your harddrive is only 160GB so there is no way you can squeeze out 256GB out of it.  So, you can believe the output from "disk usage checker" if you wish.

---

### Post by hajbal92 on 2009-02-02
> **taurus said:**
> Your harddrive is only 160GB so there is no way you can squeeze out 256GB out of it.  So, you can believe the output from "disk usage checker" if you wish.

Yeah i know thatmy HDD is 160GB but the application i was speaking above, shows that the full size is 250+GByte so this is my problem the app is not working as it should ... If you check the Screenshot you can see...

---

### Post by taurus on 2009-02-02
I saw that from your first post.  That's why I told you that you can either believe the output of **df -h** or you can believe the "Disk Usage Analyzer."

---

### Post by hajbal92 on 2009-02-02
Thanks for your help!
ok theres no way to repair the analyzer-?

---

### Post by plucky on 2009-02-02
Could this [link](http://ubuntuforums.org/showthread.php?t=748778) be your problem and workaround for Hardy?

and

Checkout this [bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)?


Good Luck

---

### Post by Neural oD on 2009-02-02
why don't u try another app? look for gdmap or gtkdiskfree might do the trick for you

---

### Post by hajbal92 on 2009-02-02
> **plucky said:**
> Could this [link](http://ubuntuforums.org/showthread.php?t=748778) be your problem and workaround for Hardy?

and

Checkout this [bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/211789)?


Good Luck
 Thanks man you solved my Mystery:d =D>=;

---

