---
title: "Inactive Swap"
date: 2009-01-23
forum: General Help
---

### Post by Mr Fredrick on 2009-01-23
Hi All,

I recently used GParted to resize both my XP partition and the size of my swap file. However since then the System Monitor reports that my swap size is 0bytes and if I check with GParted it reports its status as inactive. If I click swapon then it once again becomes active, but I doesn't maintain that status as it always reverts to inactive whenever I reboot.

How can I prevent this from happening?

Thanks in advance.

MrFred.

---

### Post by taurus on 2009-01-23
When you resized your swap partition, you change the UUID of it.  Therefore, you need to replace the old one in /etc/fstab with the new one.

```
sudo blkid
```

---

### Post by Mr Fredrick on 2009-01-23
I ran the code as suggested. Here is the output:
```
mrfred@mrfred-laptop:~$ sudo blkid
[sudo] password for mrfred: 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0818" TYPE="vfat" 
/dev/sda2: UUID="40ACD4A2ACD493AE" TYPE="ntfs" 
/dev/sda3: UUID="a50754d8-3591-4365-9ae4-c9bc603ef829" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="efc78d4d-c9de-4659-acdc-ce037ccb89c5" 
mrfred@mrfred-laptop:~$ 
```

I don't know if doing the above was supposed to fix the problem but when I rebooted the swap was again inactive. Have I missed something?

---

### Post by taurus on 2009-01-23
You need to edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the old UUID for swap with the new one.

```
UUID=efc78d4d-c9de-4659-acdc-ce037ccb89c5   none   swap   sw   0   0
```
Save it and exit gedit window.  Then, run

```
sudo mount -a
free -m
```

---

### Post by Mr Fredrick on 2009-01-23
I did what you said, but with fear and trepidation, and IT WORKED !!

So thanks.

PS. This forum is great.

---

### Post by rplantz on 2009-01-23
I'm sorry if I'm hijacking this thread, but I wish to move my swap partition. Taurus, will moving it work if I follow the procedures you give in this thread?

I need to move it because I want to install OpenSolaris in a dual boot configuration, and they say that the solaris partition needs to come before the swap.

---

