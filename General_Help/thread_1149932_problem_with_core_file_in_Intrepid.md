---
title: "problem with core file in Intrepid"
date: 2009-05-05
forum: General Help
---

### Post by Heliooos on 2009-05-05
Hi all,
I have problem with huge kcore file in my /proc folder. In fact it makes me many problems because it is blocking the rest of the system partition (8.4 GB) and I cannot delete it. I tried sudo nautilus, but nautilus does not show the folder (it seems to work but without success). The file is not deletable via root MC and I also have no idea to prevent generating such files. 

It is a HP 550 laptop with Intel Celeron and Intel GMA graphics running Vinux 1.4 (Ubuntu Intrepid with additional packages for visually impaired. My sister uses it at school, I only do the IT support. There is also OpenSuse 11.1 in dualboot. 

Any advice would be helpful.:confused:

---

### Post by ddrichardson on 2009-05-05
How much memory do you have? The files in /proc don't really exist as normal files and /proc/kcore is an alias for the amount of memory you have.

---

### Post by Heliooos on 2009-05-05
The laptop has 1GB memory and the kcore file is approx. 1GB. But I cannot do anything with Synaptic and the system often fails to load correctly due no space on disk. I checked it in nautilus and the disky really seems to be full which is strange because I used separate partition for /home and do not have much software installed.

---

### Post by ddrichardson on 2009-05-05
That file isn't actually 1 Gb - its [reporting the amount]("http://www.unixguide.net/linux/faq/04.16.shtml") of memory you have. If you post the output of```
sudo fdisk -l
```From a terminal, I'll have a better idea of the drive's layout.

---

### Post by Heliooos on 2009-05-06
so,
here is the output:
```
petrahele@petrahele-laptop:~$ sudo fdisk -l
[sudo] password for petrahele: 

Disk /dev/sda: 160,0 GB, 160*041*885*696 bajt&#367;
hlav: 240, sektor&#367; na stopu: 63, cylindr&#367;: 20*673
Jednotky = cylindry po*15120 * 512 = 7*741*440 bajtech
Identifikátor disku:&#8239;0xce2276b7

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/sda1               1        1083     8187448+  83  Linux
/dev/sda2   *        1084       20673   148100369    5  Rozší&#345;ený
/dev/sda5            1084        1624     4089928+  82  Linux swap/Solaris
/dev/sda6            1625       15168   102392608+  83  Linux
/dev/sda7           15169       16523    10243768+  83  Linux
/dev/sda8           16524       20254    28206328+  83  Linux
/dev/sda9           20255       20673     3167608+  82  Linux swap/Solaris
petrahele@petrahele-laptop:~$ 

```

it is in czech so I translate it to english:
```
petrahele@petrahele-laptop:~$ sudo fdisk -l
[sudo] password for petrahele: 

Disk /dev/sda: 160,0 GB, 160*041*885*696 bajt&#367;
heads: 240, sectors on track: 63, cylinders: 20*673
units = cylinders after*15120 * 512 = 7*741*440 bytes
Disc identificator:&#8239;0xce2276b7
Device Load   Start       End    Blocks    Id  Systém
/dev/sda1               1        1083     8187448+  83  Linux
/dev/sda2   *        1084       20673   148100369    5  Extended
/dev/sda5            1084        1624     4089928+  82  Linux swap/Solaris
/dev/sda6            1625       15168   102392608+  83  Linux
/dev/sda7           15169       16523    10243768+  83  Linux
/dev/sda8           16524       20254    28206328+  83  Linux
/dev/sda9           20255       20673     3167608+  82  Linux swap/Solaris
petrahele@petrahele-laptop:~$ 

```

It is strange that there are so many partitions. I previously had there dualboot - Pclinuxos Gnome 2009 and Opensuse 11.1 on 4 partitions - 1 for suse, one for pclinuxos, one for home and one for swap. As I installed ubuntu, I chose for home the same partition as for suse and for / the one with pclinuxos (which was formatted).

---

### Post by ddrichardson on 2009-05-06
Can you post /etc/fstab too?

---

### Post by Heliooos on 2009-05-07
> **ddrichardson said:**
> Can you post /etc/fstab too?

Ok,
it is here:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3cbfb824-ab7f-45dd-b4f7-ca181b29efeb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=45505682-eda5-44dc-a18b-172a172b8f46 /home           ext3    relatime        0       2
# /dev/sda5
UUID=1637be6f-9663-4f55-a009-738fd996fe89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ddrichardson on 2009-05-07
Are you currently dual booting?

---

### Post by Heliooos on 2009-05-07
Yes,
the opensuse is still there (I do not plan to remove it) and my sister used it sometimes when ubuntu had problems. But in fact I was not able to solve problems between Orca + voice synthesis and PulseAudio while in Vinux this worked out of box. This was the only reason to move to Ubuntu.

Recently I use the Opensuse installation sometimes for some admin work (Ubuntu has a little bit strange behavior of root - no "normal" root account, no "su" in console etc.). 

I am primarily Pclinuxos and Opensuse user, so Ubuntu is a little bit different for me.

---

### Post by ddrichardson on 2009-05-07
Ubuntu's root behaviour is fairly straight forward, if you want a command ran with elevated privileges then put sudo in front, if you want to enter lots of commands then sudo -s.

You can't delete files in /proc because they are generated by the kernel and don't actually exist on the filesystem as such, the example you give is a representation of memory and doesn't occupy a gigabyte on the drive it occupies a gigabyte in RAM - it is RAM.

What does df say? If you do```
df
```Then we can see if the drive is full but this will only tell you the Ubuntu mounted drives - sda1, 5 and 6.

You don't need multiple swap partitions, you can use one for all because not all three are running simultaneously. If you have 1Gb memory, 4Gb is too much swap space IMHO, 2 to 2.5 times RAM is a fair rule of thumb but in most systems its not used too much anyway.

What I don't follow is why you have two operating systems installed and three Linux partitions in extended partitions - oviously the primary partition sda1 is your Ubuntu / mount and the second logical partition is your /home in Ubuntu but that leaves the third and forth logical partitions - have you got seperate /home and / in SuSe as well?

---

### Post by Heliooos on 2009-05-07
> **ddrichardson said:**
> What I don't follow is why you have two operating systems installed and three Linux partitions in extended partitions - oviously the primary partition sda1 is your Ubuntu / mount and the second logical partition is your /home in Ubuntu but that leaves the third and forth logical partitions - have you got seperate /home and / in SuSe as well?

I always use separate partitions for / and for /home which makes it more secure when reinstalling the system. I know that after Suse installation I had only 4 partitions:

1) pclinuxos
2) home for pclinuxos and suse
3) opensuse
4) swap both for suse and pclinuxos

the partitions were created in gui tool called Diskdrak:
[http://wiki.pclinuxos.cz/lib/exe/detail.php?id=instalace%3Apruvodce_instalaci&cache=cache&media=instalace:snapshot06.png](http://wiki.pclinuxos.cz/lib/exe/detail.php?id=instalace%3Apruvodce_instalaci&cache=cache&media=instalace:snapshot06.png)

I also cannot understand it. I thought I set ubuntu installer to format and use the partition 1) for / and use existing partition 2) for /home (and I really have all the user home folders there) and use existing swap partition. Now I am little bit confused how the other partition could appear.

I will try the df command to see how is it with the disk :)

---

### Post by Heliooos on 2009-05-08
Ok,
here is the DF output:
```
petrahele@petrahele-laptop:~$ df
Souborový systém 1K blok&#367; Použité Volné Uži% Mounted on
/dev/sda1 8058856 8058440 0 100% /
tmpfs 512568 0 512568 0% /lib/init/rw
varrun 512568 108 512460 1% /var/run
varlock 512568 0 512568 0% /var/lock
udev 512568 2840 509728 1% /dev
tmpfs 512568 652 511916 1% /dev/shm
/dev/sda6 100784336 10062944 90721392 10% /home
overflow 1024 12 1012 2% /tmp
petrahele@petrahele-laptop:~$

```

And I have one more question- I tried to make there some free space annd deleted some files from usr/share/icons - some cursor themes which I added and my sister did not use. I deleted them with DEL key but then I remembered the fact, that the files were only moved to trash and no space was freed. I tried to get to root trash bin but Nautilus (started with sudo) was not able to show it. Is there any way to do it, or can you tell me, where the trash is located? For me it is also possible to mount the ubuntu partition from suse as root and delete the files.

---

### Post by ddrichardson on 2009-05-08
Roots is in /root/.local/share/Trash

---

### Post by Heliooos on 2009-05-12
thank you,
I successfully removed the files from roots trash but after few days the system did not start again and said that no space on the drive. I absolutely cannot understand it because I freed 300MB on the drive (used Shift + Del) and my sister did not download any updates or files from internet.

how is this possible?

---

