---
title: "How to access a partition"
date: 2008-03-20
forum: Desktop Environments
---

### Post by member2002us on 2008-03-20
I am new with Linux and Ubuntu. I have partitioned my hard disk installed Ubuntu and everything work great. The only problem is that I can mount a partition (disk) but can not write any data to it. When I look at the properties it tells me that I haev no permission. I was used to windows where you can just start to use the partition and now I am lost. Can somebody help me please. Thanks

John

---

### Post by Sef on 2008-03-20
What file system is that partition?

If you are not sure then do this:

Applications > Accessories > Terminal

then type or copy this command:

```
 sudo fdisk -l 
```  small L, then copy and paste the results here

---

### Post by member2002us on 2008-03-20
I have used gpartion and have format with ex3.
I can mount and see lost + found file but can not create another file

---

### Post by member2002us on 2008-03-20
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fc847b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2354    18908473+  83  Linux
/dev/sda2            4904        9729    38764845   83  Linux
/dev/sda3   *        2355        4791    19575202+  83  Linux
/dev/sda4            4792        4903      899640    5  Extended
/dev/sda5            4792        4903      899608+  82  Linux swap / Solaris

Partition table entries are not in disk order

I hope this help I am lost

---

### Post by x1a4 on 2008-03-20
Hi,

There are two reasons why that's happening: 
1) Like your error says, you don't have permissions.
2) The partition is mounted read-only

Unmount it then mount again with the **-w** option like so:
```
mount -w /dev/sd#
```
where # is the appropriate partition number

If you can write after mounting it this way, add the **rw** option for that partition in your **/etc/fstab file**. 

Let me know if this doesn't work, along with the content of your /etc/fstab file. Also let me know which partition is the troublesome one.

---

### Post by logos34 on 2008-03-20
> **member2002us said:**
> I have used gpartion and have format with ex3.
I can mount and see lost + found file but can not create another file

After creating the partition you should have added it to /etc/fstab, and set the permissions+owenership:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by member2002us on 2008-03-24
Thanks for you support in this matter.
I did manage to mount my sda1 and sda2.
Bought two big books about linux and ubuntu and spend the weekend reading and try to understand it. The problem was that once mounted the partion had as owner and user root. So when I logged in under my normal user name I had no access. I changed with the chown command owner ship of the directory,  mounted the partion and did allowed me to access the partion.

 I also look at the advice to use the chmod -R 755 /directory but as I am not sure what this will add I didn't use this.
If hope that I have done the things correctly.

Oce again thank you all to point me in a direction:)

---

### Post by x1a4 on 2008-03-24
You can add the **users** option in /etc/fstab to allow regular users to mount a file system. Typically though, only root should be allowed to mount a file system and it should be mounted at boot.

---

### Post by member2002us on 2008-03-24
> **x1a4 said:**
> You can add the **users** option in /etc/fstab to allow regular users to mount a file system. Typically though, only root should be allowed to mount a file system and it should be mounted at boot.

I have done adding the user in the fstab file and indeed I can mount and dis mount. This worked perfect but did not give me as user access to the filing system. I could not create files and or folders. As the folder media which is used as the standard mounting point is owned by root and user was root. Therefore I created a new folder which I called storage under my home directory. Even than when I mounted the sda1 somehow root became owner. Only after I used the change owner command I was able to access the folder and create and delete files. I hope what I did was correct

John

---

