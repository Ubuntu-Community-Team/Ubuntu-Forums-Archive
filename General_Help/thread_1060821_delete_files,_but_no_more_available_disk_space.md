---
title: "delete files, but no more available disk space"
date: 2009-02-05
forum: General Help
---

### Post by roland_j on 2009-02-05
Hi,

I am running out of disk space and deleted many files. I also emptied my trash can, but no matter how much I delete, the effect is that there is no more available disk space. "df" always tell me, that it is 100% used. How can that be?

Regards
Roland

---

### Post by maciu on 2009-02-05
post a full output of ```
df -h
```

---

### Post by hyper_ch on 2009-02-05
and did you really deleted them or just moved them to the trash bin?

---

### Post by roland_j on 2009-02-05
Hi,

here is the output from df -h

```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             134G  134G     0 100% /
tmpfs                 949M     0  949M   0% /lib/init/rw
varrun                949M  212K  949M   1% /var/run
varlock               949M     0  949M   0% /var/lock
udev                  949M  2.8M  946M   1% /dev
tmpfs                 949M  104K  949M   1% /dev/shm
lrm                   949M  2.0M  947M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
/dev/sdc1             466G  282G  184G  61% /media/disk-4

```

Regards
Roland

---

### Post by hyper_ch on 2009-02-05
check your trashbin and also the trashbin of the root user

---

### Post by bff7755a on 2009-02-05
You have no space at the root partition.

I can advise you boot from live cd and correct your partition table.

It's recommended that '/home', '/tmp', '/boot', '/usr' and '/var' dirs has his own partitions. For example, my partition table:

```
[ibm-t43][mutex]~/backup> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             1.9G  372M  1.4G  21% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  128K  251M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.9M  248M   2% /dev
tmpfs                 251M  520K  251M   1% /dev/shm
lrm                   251M  2.0M  249M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             471M   34M  413M   8% /boot
/dev/sda9              83G  7.1G   72G   9% /home
/dev/sda8             2.8G   69M  2.6G   3% /tmp
/dev/sda5              28G  4.3G   22G  17% /usr
/dev/sda6              28G 1001M   26G   4% /var
/dev/sdb1             3.9G  2.5G  1.5G  64% /media/ubuntu
/dev/loop0            676M  676M     0 100% /mnt/squash
```

---

### Post by hyper_ch on 2009-02-05
> **bff7755a said:**
> It's recommended that '/home', '/tmp', '/boot', '/usr' and '/var' dirs has his own partitions.

why and recommended by whom?

---

### Post by roland_j on 2009-02-05
Hi,

sorry, but the problem is not solved: The trash bin seems to be empty. 
I tried it with sudo rm -rf /home/roland/.trash and removed the files in local/share/Trash.
But there is still no disk space. Does it matter that this is a laptop?

Regards
Roland

---

### Post by hyper_ch on 2009-02-05
are you on the live cd?

---

### Post by bff7755a on 2009-02-05
> **roland_j said:**
> Hi,

sorry, but the problem is not solved: The trash bin seems to be empty. 
I tried it with sudo rm -rf /home/roland/.trash and removed the files in local/share/Trash.
But there is still no disk space. Does it matter that this is a laptop?

Regards
Roland

Please show the output of the command:

```
sudo du --max-depth 1 -h /
```

---

### Post by bff7755a on 2009-02-05
> **hyper_ch said:**
> why and recommended by whom?

I thinks that it's not very good idea to store all files in the root partition.

---

### Post by hyper_ch on 2009-02-05
> **bff7755a said:**
> I thinks that it's not very good idea to store all files in the root partition.
why?

---

### Post by roland_j on 2009-02-05
Hi,

no, this is a normal laptop hard disk. I use Ubuntu since one year now and it never had this problem. Maybe I made a mistake with a trash bin. Are there other places for deleted files? Maybe gnome keeps something somewhere.

Regards
Roland

---

### Post by hyper_ch on 2009-02-05
can you run:

```

cd /
sudo apt-get clean
sudo du --max-depth=5 > output.txt
sudo chmod USER.USER output.txt

```
then you will have an output.txt file in the root ("/") dir and it's chmodded to your username. Use your username instead of "USER". Check then where all the space is needed (you could import it into OOo Calc) as CSV file that is separated with a tab [I think]) and then have it sorted to directory size. It will then tell you what directory uses how much space or you could attach the file here.

---

### Post by bff7755a on 2009-02-05
> **hyper_ch said:**
> why?

At first, for security reasons. For example, /tmp partition can be mounted without executable flag. Are you trolling?

---

### Post by hyper_ch on 2009-02-05
> **bff7755a said:**
> At first, for security reasons. For example, /tmp partition can be mounted without executable flag.
Can you elaborate that? Does it really need to be on a seperate partition to accomplish that? What is the effect of the executable flag?

> **bff7755a said:**
> Are you trolling?
Are you?

---

### Post by bff7755a on 2009-02-05
> **hyper_ch said:**
> What is the effect of the executable flag?

Usually /tmp has 777 perms. So anyone can write to it.

---

### Post by hyper_ch on 2009-02-05
> **bff7755a said:**
> Usually /tmp has 777 perms. So anyone can write to it.
and the problem of that is....?

anyway, this has gone long enough and has nothing to do with the TOs question and problem.

---

### Post by abn91c on 2009-02-05
sudo apt-get autoremove  will get rid of some uneeded junk

---

### Post by roland_j on 2009-02-05
Hi,

here is the output:

```
~$ sudo du --max-depth 1 -h /
5.3M	/lost+found
24G	/var
14M	/etc
87G	/media
6.1M	/bin
12M	/boot
2.9M	/dev
du: cannot access `/home/roland/.gvfs': Permission denied
11G	/home
4.0K	/initrd
127M	/lib
4.0K	/mnt
2.7G	/opt
du: cannot access `/proc/18688/task/18688/fd/4': No such file or directory
du: cannot access `/proc/18688/task/18688/fdinfo/4': No such file or directory
du: cannot access `/proc/18688/fd/4': No such file or directory
du: cannot access `/proc/18688/fdinfo/4': No such file or directory
0	/proc
16M	/root
6.8M	/sbin
6.5G	/srv
0	/sys
20K	/tmp
3.3G	/usr
133G	/

```

I also removed several packages with Synaptic (it said that 500 MB was freed), but all I've got is 100% disk usage.

Regards
Roland

---

### Post by hyper_ch on 2009-02-05
not quite the command I've given... but 

/media is 87 GB --> check this

and

/var is 24 GB --> check this also

I used depth of 5 so that at least you will get a few levels down...

---

### Post by roland_j on 2009-02-05
Hi,

here is the output:
```

$ sudo du --max-depth 1 -h /
5.3M	/lost+found
24G	/var
14M	/etc
87G	/media
6.1M	/bin
12M	/boot
2.9M	/dev
du: cannot access `/home/roland/.gvfs': Permission denied
11G	/home
4.0K	/initrd
127M	/lib
4.0K	/mnt
2.7G	/opt
du: cannot access `/proc/19774/task/19774/fd/4': No such file or directory
du: cannot access `/proc/19774/task/19774/fdinfo/4': No such file or directory
du: cannot access `/proc/19774/fd/4': No such file or directory
du: cannot access `/proc/19774/fdinfo/4': No such file or directory
0	/proc
16M	/root
6.8M	/sbin
6.5G	/srv
0	/sys
20K	/tmp
3.3G	/usr
133G	/

```
It is unbelievable: I removed so many packages with Synaptic, but all I get is 100% used space.

Regards
Roland

---

### Post by bff7755a on 2009-02-05
> **roland_j said:**
> Hi,

here is the output:

```
~$ sudo du --max-depth 1 -h /
5.3M	/lost+found
24G	/var
14M	/etc
87G	/media
6.1M	/bin
12M	/boot
2.9M	/dev
du: cannot access `/home/roland/.gvfs': Permission denied
11G	/home
4.0K	/initrd
127M	/lib
4.0K	/mnt
2.7G	/opt
du: cannot access `/proc/18688/task/18688/fd/4': No such file or directory
du: cannot access `/proc/18688/task/18688/fdinfo/4': No such file or directory
du: cannot access `/proc/18688/fd/4': No such file or directory
du: cannot access `/proc/18688/fdinfo/4': No such file or directory
0	/proc
16M	/root
6.8M	/sbin
6.5G	/srv
0	/sys
20K	/tmp
3.3G	/usr
133G	/

```

I also removed several packages with Synaptic (it said that 500 MB was freed), but all I've got is 100% disk usage.

Regards
Roland

Ok. Now try `--max-depth 2` :)

---

### Post by drs305 on 2009-02-05
Part of the problem may lie in your /media and /var folders. If you don't have anything currently mounted in media this folder and subfolders should be of minimal size. Unmount all your non-system partitions and check the size of /media again. If it is still large, you may have a backup file that was supposed to be written to another drive or non-system partition.

For the /var folder, you may have some very large "log" files that are taking up a great deal more space than necessary. You can use Disk Usage Anaylzer (baobab) to look at the folder sizes: Applications, Accessories, Disk Usage Analyzer.

Here is a link to to tutorial I wrote about how to find and delete trash throughout your system, but there are also methods for finding large files and folders as well:

[How To: Disk Full? - Check Your Trash]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by roland_j on 2009-02-05
Hi,

I think I found the problem: I configured Simple Backup for automatic backup. It tried to backup on the local disk. I deleted the backup files and stopped the program. Now I have enough disk space. Puh! 

Thank you very much for your extreme fast responses!

Regards
Roland

---

### Post by drs305 on 2009-02-05
Simple Backup (sbackup) is one of the most frequent causes of large files mistakenly ending up in /media.  Glad you found the cause.

---

### Post by Martin Smith on 2009-02-05
Try reinstalling it, or, use a live cd of parted magic and see what it says about the hard drive

---

### Post by roland_j on 2009-02-05
Hi,

> Try reinstalling it,

reinstalling is obviously not necessary. See: 
[http://ubuntuforums.org/showthread.php?t=1010875](http://ubuntuforums.org/showthread.php?t=1010875)

Regards
Roland

---

### Post by hyper_ch on 2009-02-05
why do you advice to reinstall???

---

### Post by abn91c on 2009-02-05
> **hyper_ch said:**
> why do you advice to reinstall???
It's the Windows, AOL way of thinking, "when stuck in a program Reinstall"

---

### Post by mistypotato on 2010-10-16
This may throw some people....it threw me at first.....

If you use the Ubuntu --> System --> Adminstration -->  System Monitor 
tool to view the _Available_ and _Free_ space on your Ubuntu PC, you may see that you have **FREE** space but no **AVAILABLE** space.

This is because ubuntu will reserves 5% of the disks total space for root.   I won't go into the explanation...just trust me.

So, you can delete all the files you want but you will STILL have ZERO "available" space until you delete enough files so that there is 5% of the disk as FREE SPACE.   Once you reach that point, deleting additional files will start giving you "available" space.

So let's assume you have a 100GB hard drive.   Ubuntu (or many Linux systems), require 5% to always be available to root so 5% of 100GB = 5GB

So on a 100GB hard drive (let's assume only 1 drive for now).....you MUST HAVE 5GB minimum of FREE SPACE before you can have ANY "Available" space.

So, if right now your system has for exmple 1GB of "Free" space, you will need to delete 4GB of files in order to get Free space to the point where there is enough "reserved" free space for root.   From there, deleting any additional files will give you "Available" Space (that you can use).

Hope this helps. :)

---

