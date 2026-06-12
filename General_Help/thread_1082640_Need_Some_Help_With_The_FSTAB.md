---
title: "Need Some Help With The FSTAB"
date: 2009-02-28
forum: General Help
---

### Post by computermystro on 2009-02-28
I accidentally deleted some of the lines of my FSTAB, I know I am a total noob not backing it up. So I did some googleing OK a lot of googleing, this what i came up with. I would be extremely greatfull if someone could take a look at this and me know if it is right. Thanks


What Fdisk Says
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33ae8174

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb738b442

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9362    75200233+  83  Linux
/dev/sdb2            9363        9729     2947927+   5  Extended
/dev/sdb5            9363        9729     2947896   82  Linux swap / Solaris


What /etc/fstab Says

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/Data ext3 defaults 0 0
/dev/sdb1 / ext3 defaults 0 0
/dev/sdb2 / ext3 defaults 0 0
/dev/sdb5 swap swap defaults 0 0

---

### Post by Elfy on 2009-02-28
First are you in your install still ?

What did you use to edit the file - if it was gedit then it should have done a backup for you - name will be fstab~

So try to open that 

```
gedit /etc/fstab~
```

If that works and is right you can use it to overwrite fstab

```
sudo cp /etc/fstab~ /etc/fstab
```

If not you can try - comment out the lines you have at present and paste in

> /dev/sdb1 / ext3 relatime,errors=remount-ro 0  1
/dev/sdb5 none swap  sw  0   0
/dev/sda1 /media/Data ext3 user,relatime 0 2
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

If that works then I would replace all the /dev/sdxy's with the UUID, run blkid from a terminal and replace

---

### Post by computermystro on 2009-03-02
Unfortunately that didn't work do you have any other ideas? BTW i used nano as a text editor.

---

### Post by taurus on 2009-03-02
Post the outputs of these commands.

```
cat /etc/fstab
df -h
```

---

### Post by computermystro on 2009-03-02
Thanks for the replies..

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/Data ext3 defaults 0 0
/dev/sdb1 / ext3 defaults 0 0
/dev/sdb2 / ext3 defaults 0 0
/dev/sdb5 swap swap defaults 0 0


Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              71G  1.5G   66G   3% /
tmpfs                 492M     0  492M   0% /lib/init/rw
varrun                492M  832K  492M   1% /var/run
varlock               492M     0  492M   0% /var/lock
udev                  492M  2.7M  490M   1% /dev
tmpfs                 492M     0  492M   0% /dev/shm
/dev/sda1             230G  1.5G  217G   1% /media/Data

---

### Post by taurus on 2009-03-02
> **computermystro said:**
> Thanks for the replies..

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[B][COLOR="Red"]/dev/sda1 /media/Data ext3 defaults 0 0
/dev/sdb1 / ext3 defaults 0 0
/dev/sdb2 / ext3 defaults 0 0
/dev/sdb5 swap swap defaults 0 0
[/COLOR][/B]

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              71G  1.5G   66G   3% /
tmpfs                 492M     0  492M   0% /lib/init/rw
varrun                492M  832K  492M   1% /var/run
varlock               492M     0  492M   0% /var/lock
udev                  492M  2.7M  490M   1% /dev
tmpfs                 492M     0  492M   0% /dev/shm
/dev/sda1             230G  1.5G  217G   1% /media/Data

Edit /etc/fstab and replace those lines in read to

```
/dev/sdb1   /   ext3   relatime,errors=remount-ro   0   1
/dev/sda1   /media/Data   ext3   defaults   0   2
```
Save it and reboot.

You cannot mount an extended partition, /dev/sdb2.  

You already have your swap partition, /dev/sdb5, mounted using UUID so no need to mount it again.

---

### Post by computermystro on 2009-03-02
Is this right thanks
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1   /media/Data   ext3   defaults   0   2
/dev/sdb1   / ext3  relatime,errors=remount-ro   0   1

---

### Post by taurus on 2009-03-02
Personally, I would have mounted / first before those two /media entries in /etc/fstab

---

### Post by computermystro on 2009-03-03
I changed it to, but now i am getting line 5 in fstab is bad any ideas. thanks

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none swap sw $

/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sda1 /media/Data ext3 defaults 0 2

---

### Post by taurus on 2009-03-03
> **computermystro said:**
> I changed it to, but now i am getting line 5 in fstab is bad any ideas. thanks

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none swap sw **[COLOR="Red"]$[/COLOR]**

/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sda1 /media/Data ext3 defaults 0 2

Replace the $ sign with 0 0.

```

UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none swap sw **[COLOR="Blue"]0 0[/COLOR]**
```

---

### Post by computermystro on 2009-03-03
Thanks man you rock.. Does it look right now..
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

# /dev/sda5
UUID=31b38010-58cb-4e79-8074-8c4acdd3c2e6 none swap sw 0 0

/dev/sdb1 / ext3 relatime,errors=remount-ro 0 1

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sda1 /media/Data ext3 defaults 0 2

---

### Post by taurus on 2009-03-03
Looks good to me.

---

