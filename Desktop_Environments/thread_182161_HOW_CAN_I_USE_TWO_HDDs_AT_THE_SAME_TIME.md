---
title: "HOW CAN I USE TWO HDDs AT THE SAME TIME?"
date: 2006-05-25
forum: Desktop Environments
---

### Post by sidy on 2006-05-25
Hello there, I am confusing here!
On my PC I have one hd40 (slave, where I run ubuntu 5.10 upgraded to 6.06) and another hd80 (10gb for windows and 70 for ubuntu). In other words I have 110GB for ubuntu.
Now, because my hd40 is full, I w'd like to transfer datos to the 80hd or 70gb partition.

- I have tryed:
1-  Installed ubuntu on the 70gb partition, but wasn't displaying graphic. To sort it, I did what I had done before when I had the same problem (graphic display) ctrl+alt+F1:
'sudo dpkg-reconfigure xserver-xorg'
then I choose
'nv' , enter, then
'nv nVidia FX5200LP'  ,and the problem was suppost to be sorted, but it didn't.
(as I typed 'lspci' I've got the following information of the graphic card 'nVidia Corporation NV34 [GeForce FX5200LP] (rev a1)' , I also typed this in full didn't work either).

2-  So I rebboted and logged in to ubuntu on 40hd. On the terminal, I was meant to reach the 70gb partition. It was mounted (hda1 hda2 hda3), so I did:
'sudo mount /dev/hda2 /mnt/hda2' then enter, came up 'mount: you must specify the file system file' , then I typed 'cd hda2' enter 'ls' , did'nt show any thing, because there is nothing there, then nautilus. ... I can only open, but not alowed to copy or even delete to mount again. (by the way, the hda1 2 3 had been mountend before the 70gb partition been done).

So basically, I would like to use both hdds.
WHAT CAN I DO TO USE BOTH HDDS AT THE SAME TIME?

Rgds,

---

### Post by nalmeth on 2006-05-25
> Hello there, I am confusing here! Yes, you are a little bit...
You should mount the drives in /media rather than /mnt

and make the folder's for them to mount in.

sudo mkdir /media/hdaxx
sudo mkdir /media/hdayy

Remember that if your Windows Filesystem is NTFS you won't be able to write to it. You can only safely read from NTFS.

---

### Post by sidy on 2006-05-26
[QUOTE=nalmeth]
You should mount the drives in /media rather than /mnt

and make the folder's for them to mount in.

sudo mkdir /media/hdaxx
sudo mkdir /media/hdayy

[/QUOTE]

OK!
What to do next?

I've tryed:

sudo media /dev/hda2 /media/hda2

sudo media /dev/hdaxx /media/hdaxx

same reply 'mount: you must specify the filesystem type'  or  'sudo: media: command nor found' . I'm not good on it, so need specific commands in full, please.

tkanks again.

---

### Post by Ramses de Norre on 2006-05-26
Could you post the output of sudo fdisk -l and the contents of /etc/fstab.
Your situation will be easier to understand then.
As for using both you could set / on one and /home on another drive, nice guide for doing that [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").

---

### Post by sidy on 2006-05-26
[QUOTE=Ramses de Norre]Could you post the output of sudo fdisk -l and the contents of /etc/fstab.
Your situation will be easier to understand then.
As for using both you could set / on one and /home on another drive, nice guide for doing that [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").[/QUOTE]


From 'sudo fdisk -l' came up:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders do 16065 * 512 = 8225280 bytes

      Device Boot           Start                End            Blocks       Id     System
/dev/hda1     *                    1              9592      77047708+     83     Linux
/dev/hda2                     9593              9964        2988090         5    Extended
/dev/hda3                     9593              9964        2988058+     82Linux swpa/ Solaris

Disk /dev/hdb: 40.0 GB, 400206644320 bytes
255 heads, 63 sctors/track, 4865 cylinders
Unitis = cylinders of 16065 * 512 = 8225280 bytes

      Device Boot           Start                End            Blocks       Id     System
/dev/hdb1     *                    1              4664      37463548+     83    Linux
/dev/hdb2                     4665              4865        1614532+       5    Extended
/dev/hdb3                     4665              4865        1614501+     82Linux swpa/ Solaris


From '/etc/fstab' came up:

'permission denied'

I don't know how to set ' /' on one and '/home' on another drive, as you said.

I still need help please.

---

### Post by Ramses de Norre on 2006-05-26
less /etc/fstab should work, otherwise sudo less /etc/fstab.

Have you looked at the guide I gave you for moving /home?

---

### Post by sidy on 2006-05-28
[QUOTE=Ramses de Norre]less /etc/fstab should work, otherwise sudo less /etc/fstab.

Have you looked at the guide I gave you for moving /home?[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/mnt/hdb1	ntfs	defaults	1	1
/dev/hdb2	/mnt/hdb2	ext3	defaults	1	1
/dev/hdb3	/mnt/hdb3	vfat	defaults	1	1

(I've added the last 3 lines)
(and I don't know a lot about the above info)

I've looked the guide you gave me, '/home', and I'm still looking because there is a lot of information.

I just need to copy, or transfer or drag datos from hdb1 to hda2 or hdd.

rgds

---

### Post by kanzelsberger on 2006-05-28
[QUOTE=sidy]OK!
What to do next?

I've tryed:

sudo media /dev/hda2 /media/hda2

sudo media /dev/hdaxx /media/hdaxx

same reply 'mount: you must specify the filesystem type'  or  'sudo: media: command nor found' . I'm not good on it, so need specific commands in full, please.

tkanks again.[/QUOTE]

You are missing filesystem type parameter for mount. Try adding -t ext3 like ... mount -t ext3 /dev/hda2 /mnt/hda2

---

### Post by Sutekh on 2006-05-28
[quote=sidy]From 'sudo fdisk -l' came up:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders do 16065 * 512 = 8225280 bytes

      Device Boot           Start                End            Blocks       Id     System
/dev/hda1     *                    1              9592      77047708+     83     Linux
/dev/hda2                     9593              9964        2988090         5    Extended
/dev/hda3                     9593              9964        2988058+     82Linux swpa/ Solaris

Disk /dev/hdb: 40.0 GB, 400206644320 bytes
255 heads, 63 sctors/track, 4865 cylinders
Unitis = cylinders of 16065 * 512 = 8225280 bytes

      Device Boot           Start                End            Blocks       Id     System
[B] /dev/hdb1     *                    1              4664      37463548+     83    Linux
/dev/hdb2                     4665              4865        1614532+       5    Extended
/dev/hdb3                     4665              4865        1614501+     82Linux swpa/ Solaris[/B]
[/quote] 
[quote=sidy]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[B] /dev/hdb1    /mnt/hdb1    ntfs    defaults    1    1
/dev/hdb2    /mnt/hdb2    ext3    defaults    1    1
/dev/hdb3    /mnt/hdb3    vfat    defaults    1    1[/B]

(I've added the last 3 lines)
(and I don't know a lot about the above info)
[/quote] 
Based on that information, I don't think those last lines are correct.  At all.

 - To start you already have a line for /dev/hdb1 and /dev/hdb5.  They are correct ones, you don't need duplicates, especially when they are contradictory.  

 - /dev/hdb2 is an extended partition and can't be mounted (same goes for /dev/hda2 you can't mount that partition).   

 - The format you have chosen for them in the fstab is incorrect too, there are no NTFS or VFAT partitions.


I don't understand what you are trying to, but you should remove those lines completely.  

It should look like this
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
``` 

If you need to mount the other hard drive /dev/hda1, then you should use these commands
```
sudo mkdir /mnt/hda1
sudo mount /dev/hda1 /mnt/hda1 -t ext3 -o defaults
```

---

### Post by sidy on 2006-05-29
Hello again.

A have deleted the extra 3 lines I hab been added on '/etc/fstab'

At the same time a friend of mine gave same extra information on how to use both HDDs at the same time or been able to copy datos from and to hdds.

On terminal instead of just 'nautilus' I did 'sudo nautilus', so I was on root, there I'd been able to change permissions, I changed on 'file group and users' to my name, so now, I AM ABLE TO COPY DATOS FROM AND TO BOTH HDDs.

But I have onother concerne.

I WOULD LIKE TO BOOT DIRECT ON THE HD OF 80GB, NOT THROUGH THE 40GB.
But when I try to do so all what I have is a black screen with a dash on the top-left-corner.

No graphic graphic displaying, so ctrl+alt+F1:
' sudo dpkg-reconfigure xserver-xorg '
then I choose
' nv ' , enter, then
' nv nVidia FX5200LP '
' /etc/init.d/gdm stop '
' /etc/init.d/gdm restart '

And I was suppost to have graphic displaying , but it didn't.

WHAT CAN I DO NOW?

rgds!

---

### Post by Ramses de Norre on 2006-05-29
What do you mean by booting on a hd?? 
I guess you want to boot the operating system installed on one of your hd's. How did you try to 'boot on another hd'? I think you're misunderstanding something.

---

### Post by sidy on 2006-05-29
[QUOTE=Ramses de Norre]What do you mean by booting on a hd?? 
I guess you want to boot the operating system installed on one of your hd's. How did you try to 'boot on another hd'? I think you're misunderstanding something.[/QUOTE]

Basically when I switch on the PC I have three options.

1)Ubuntu (I've installed ubuntu on 65gb of the 80hd, which is the master, so hda)

2)Ubuntu (I've installed ubuntu on the entired hd of 40gb, which is the slave, so hdb1)

3)Windows XP (I've installed windows xp on 15gb of the 80gb hd).

If I choose option 3 I go windows.
If I choose option 2 I go ubuntu on the hd of 40gb.
If I choose option 1 I am suppost to go to ubuntu on the 65gb of the 80 hd, the hda.

But in option 1, instead going to the graphic display, it goes to a black is screen with a dash on the top-left-corner. The only thing I can do is ctrl+Alt+F1 and Trying to work some commands there.

The ones I've tryed are:
' sudo dpkg-reconfigure xserver-xorg '
then I choose
' nv ' , enter, then
' nv nVidia FX5200LP '
' /etc/init.d/gdm stop '
' /etc/init.d/gdm restart '

Then come up  ' GNOME MANAGER Can not display'

So, no success.

SO, CAN YOU GIVE SAME DIRECTION ON HOW TO HAVE GRAPHIC SCREEN DISPLAYING?

rgds.

---

