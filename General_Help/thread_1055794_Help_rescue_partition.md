---
title: "Help rescue partition"
date: 2009-01-31
forum: General Help
---

### Post by rhyz on 2009-01-31
i have a 20gb hdd 12-13gb ntfs with windows xp and ubuntu 8.10 and 5gb unallocated i used a partitioner to add 5gb to exsisting drive it went wrong and now nothing boots.

i used live cd and viewed gparted and it showed my partitions exactly the same but now the 12gb area has a warning sign next to it.

i turn on the computer and it show laptop logo then a flashing dash on black screen

i would like to rescue xp and files if possible (ubuntu is installed through xp add/remove progrmmes)

---

### Post by 80aless on 2009-01-31
Maybe you can try to boot with a Super Grub CD or USB: [http://www.supergrubdisk.org]("http://www.supergrubdisk.org")
You put the files in a CD/USB and you boot with those.

Or you can try to boot with the ubuntu live cd and mount you partitions. Study a bit how mount works and try to mount the files that you find in the /dev/ path.
```
ls /dev
su
mkdir /mount/partition
mount /dev/s* /mount/partition

```

I hope this helps,
Alex

---

### Post by rhyz on 2009-01-31
ill give it a go thanks

---

### Post by balaknair on 2009-01-31
Try testdisk, it's probably the best tool to repair borked partitions and recover data. It is a command line tool(no GUI) but is very easy to use.
You will need internet access to install it though(it can be installed in a LiveCD session). If you cannot access the internet while running a LiveCD session, you can remove the hard drive and connect it to a computer with Ubuntu on it and then use test disk to repair the drive.
The safest option is to use the LiveCD though.

An excellent illustrated guide can be seen here
[http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS](http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_an_accidentally_deleted_NTFS)

---

### Post by caljohnsmith on 2009-01-31
How about first posting:
```
sudo fdisk -lu
```
And please identify your existing partitions.

---

### Post by rhyz on 2009-01-31
i have a 20gb hdd on my laptop, 5gb is unallocated and the rest is formatted as ntfs.

i tryed adding the 5gb unallocated space on to windows xp drive but it went wrong 80-90% through the process. now when i boot i dont get anything:

turn on laptop-laptop logo-black screen with flashing dash

i put ubuntu 8.10 live cd in and viewed partitions with gparted the ntfs partition had a error sign on it. I set gparted to check and repair and the error results:

[http://www.bebo.com/PhotoAlbumBig.jsp?MemberId=468460337&PhotoAlbumId=9993821055](http://www.bebo.com/PhotoAlbumBig.jsp?MemberId=468460337&PhotoAlbumId=9993821055)

[http://www.bebo.com/PhotoAlbumBig.jsp?PageNbr=1&MemberId=468460337&PhotoAlbumId=9993821055&PhotoId=9993836421](http://www.bebo.com/PhotoAlbumBig.jsp?PageNbr=1&MemberId=468460337&PhotoAlbumId=9993821055&PhotoId=9993836421)

[http://www.bebo.com/PhotoAlbumBig.jsp?PageNbr=1&MemberId=468460337&PhotoAlbumId=9993821055&PhotoId=9993868336](http://www.bebo.com/PhotoAlbumBig.jsp?PageNbr=1&MemberId=468460337&PhotoAlbumId=9993821055&PhotoId=9993868336)

does anyone know how i can repair xp (programmes, tools, using terminal)

i would also still like to dual boot but i havent been using ubuntu for long so i can reinstall.

any help much appriciated thanks

---

### Post by caljohnsmith on 2009-01-31
The good news is it looks like gparted was smart enough to not try and resize your Windows partition because it detected the Windows MFT (Master File Table) has problems. You might be able to repair your Windows partition by booting your Windows Install CD, go to the "Recovery Console" and do:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Once that's done, boot your Live CD again, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt && ls -l /mnt
```
And please post the output. We can work from there if you want.

---

### Post by rhyz on 2009-01-31
i will try tomorrow fedup after whole day of doing it thanks

---

### Post by rhyz on 2009-02-01
im cant find my win xp install cd so i cant recover ubuntu 

(ubuntu installed as programme)

i cannot boot at all and i dont have xp install cd

will winPE recover the drive and allow dual boot or once drive covered how will i dual boot?

also how will i add recover console to xp
and backup ubuntu

---

### Post by overdrank on 2009-02-01
Please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by rhyz on 2009-02-01
thanks dunno how to delete a thread any ideas on xp cd?

---

### Post by balaknair on 2009-02-02
XP CD- you could ask your computer vendor for a CD, or get one from a friend. I don't think retail XP CDs are available any more.

To repair the file tables without an XP CD, you can try
1) use an Ubuntu Live CD and install testdisk, and try to repair your hard drive with it(see post #4 in this thread)

2) use SuperGrubDisk, which can be downloaded here(it's only around 400 KB)
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Write the iso to a CD and boot from it. Take a look at this page for an illustrated howto on repairing Windows installations.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

