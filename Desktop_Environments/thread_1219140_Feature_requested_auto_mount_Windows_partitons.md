---
title: "Feature requested: auto mount Windows partitons"
date: 2009-07-21
forum: Desktop Environments
---

### Post by wei_jiang on 2009-07-21
Hi,

I installed Ubuntu inside Windows XP. It is good. One feature I would like to see is to automatically mount all Windows partitions during installation.

1. A Windows partition does not show automatically: when I start Ubuntu, go to a terminal and type:
    ls  /media
I do not see my Windows partition. I have to go to Places > Computer to click the "OS", then go to terminal, then I can see one Windows partition. So I can not write anything related to Widnows partition in my .bashrc or other scripts.

The terminal of Ubuntu is not the only software which has this issue. There are many software will see this problem. For example, Netbeans (Sun's Java IDE), emacs, ...
 

2. Only drive C: of Windows can be seen when you go to Places>Computer. Actually, my XP is on drive D:. I also have other partitions which can not be seen from Ubuntu.

Ubuntu is very attractive to existing Windows users. I image many Windows user will try to install Ubuntu inside Widnows first, play it a little, then may consider finally install Ubuntu. For these users. the auto-mounted Windows partitionS will be nice.

Thanks.

---

### Post by ~sHyLoCk~ on 2009-07-21
> **wei_jiang said:**
> Hi,

I installed Ubuntu inside Windows XP. It is good. One feature I would like to see is to automatically mount all Windows partitions during installation.

1. A Windows partition does not show automatically: when I start Ubuntu, go to a terminal and type:
    ls  /media
I do not see my Windows partition. I have to go to Places > Computer to click the "OS", then go to terminal, then I can see one Windows partition. So I can not write anything related to Widnows partition in my .bashrc or other scripts.

The terminal of Ubuntu is not the only software which has this issue. There are many software will see this problem. For example, Netbeans (Sun's Java IDE), emacs, ...
 

2. Only drive C: of Windows can be seen when you go to Places>Computer. Actually, my XP is on drive D:. I also have other partitions which can not be seen from Ubuntu.

Ubuntu is very attractive to existing Windows users. I image many Windows user will try to install Ubuntu inside Widnows first, play it a little, then may consider finally install Ubuntu. For these users. the auto-mounted Windows partitionS will be nice.

Thanks.

```
sudo apt-get install ntfs-3g
sudo mkdir /windows
sudo gedit /etc/fstab
```

Add there:

```
/dev/sda1            /windows         ntfs-3g    rw,defaults,noatime  0   0  
```
Replace /dev/sda1 with your Windows partition. Do ```
fdisk -l
``` to check.

---

