---
title: "How to see &quot;My Computer&quot; as Ubuntu"
date: 2009-05-17
forum: General Help
---

### Post by quangtrung1789 on 2009-05-17
I have installed Xubuntu, but I only see "File System", I want to see "My computer" as Ubuntu or see other partitions (because i had install Ubuntu before).
Can you help me???

---

### Post by Legace on 2009-05-17
> **quangtrung1789 said:**
> I have installed Xubuntu, but I only see "File System", I want to see "My computer" as Ubuntu or see other partitions (because i had install Ubuntu before).
Can you help me???

I don't think XFCE (or Xubuntu) has "My Computer".
All the drives should be in **/media**, though.

---

### Post by quangtrung1789 on 2009-05-17
> **Legace said:**
> I don't think XFCE (or Xubuntu) has "My Computer".
All the drives should be in **/media**, though.

oh, my "/media" only has "cdrom" and "cdrom0" :(

---

### Post by Legace on 2009-05-17
> **quangtrung1789 said:**
> oh, my "/media" only has "cdrom" and "cdrom0" :(

Type **blkid** in Terminal and post output here..

---

### Post by quangtrung1789 on 2009-05-17
> **Legace said:**
> Type **blkid** in Terminal and post output here..

it here :)

> /dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="508CA8CF8CA8B140" LABEL="WIN_XP" TYPE="ntfs" 
/dev/sda3: UUID="23102F0A063D2FF6" LABEL="MULTIMEDIA" TYPE="ntfs" 
/dev/sda4: UUID="5106337942F243C8" LABEL="DOCUMENT" TYPE="ntfs" 
/dev/sda5: UUID="7b3f8124-c628-4631-97d6-2d1437b7282a" TYPE="ext4" 
/dev/sda7: UUID="1c4d77e3-798a-4c22-882c-89431ea2edb4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="e6e87475-cff8-4006-a649-1eccc2cb3bf3" TYPE="swap" 


---

### Post by Legace on 2009-05-17
Sorry, I asked for the wrong thing..

I am not sure weather Xubuntu has gedit. If it does not, replace gedit with a text editor that Xubuntu has..

```
sudo gedit /etc/fstab
```

Copy the contents of that file here.

---

### Post by quangtrung1789 on 2009-05-17
> **Legace said:**
> Sorry, I asked for the wrong thing..

I am not sure weather Xubuntu has gedit. If it does not, replace gedit with a text editor that Xubuntu has..

```
sudo gedit /etc/fstab
```

Copy the contents of that file here.

it here :)

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b3f8124-c628-4631-97d6-2d1437b7282a /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e6e87475-cff8-4006-a649-1eccc2cb3bf3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       

---

### Post by Legace on 2009-05-17
The other drives haven't been mounted.
You need to mount them in order for them to appear in /media.

-> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by quangtrung1789 on 2009-05-17
> **Legace said:**
> The other drives haven't been mounted.
You need to mount them in order for them to appear in /media.

-> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

oh, it is very complex :(
can you help simple for me ? :)

---

### Post by blackened on 2009-05-17
> **Legace said:**
> Sorry, I asked for the wrong thing..

I am not sure weather Xubuntu has gedit. If it does not, replace gedit with a text editor that Xubuntu has..

```
sudo gedit /etc/fstab
```

Copy the contents of that file here.

You don't need a text editor to view and/or copy & paste some text. Also, you needn't use sudo if you only plan on viewing the file without changing it. In fact, I would propose that you risk accidentally editing that file by issuing sudo. The correct way to go about it would be

```
cat /etc/fstab
```

which will print the contents of /etc/fstab to standard output.

---

