---
title: "SWAP lost - I need it back."
date: 2009-05-02
forum: General Help
---

### Post by marcgh on 2009-05-02
Hi,
I was playing around with GPARTED and accidentally deleted my swap file.

I reformatted that small (2.5 GIB) partition as a linux-swap but the swap is still at 0 bytes in the system monitor.

I really want this swap back.

Thanks in adavance for your assistance.

included the screenshot from gparted.

Marc

---

### Post by taurus on 2009-05-02
If you deleted and created it again, the UUID for swap in /etc/fstab is wrong.  You need to modify it in /etc/fstab.

```
sudo blkid
```

---

### Post by marcgh on 2009-05-02
Wow! that's fast! Thanks Taurus.

this is the result from sudo blkid :

user@user-ubuntu:~$ sudo blkid
[sudo] password for user: 
/dev/sdb1: UUID="0288CFAF88CF9F91" TYPE="ntfs" LABEL="DATA 020508" 
/dev/sdc1: UUID="60A46B76A46B4E1A" LABEL="DATA" TYPE="ntfs" 
/dev/sdd1: UUID="7A08E5C308E57F0F" LABEL="FILMS_500" TYPE="ntfs" 
/dev/sdb5: UUID="4816d8cd-7b18-4569-a0ce-50a17af58d01" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="e8681932-8d27-4050-8876-c98b216fc661" 
/dev/sdc2: UUID="D4687E4B687E2C7C" LABEL="MUSIC" TYPE="ntfs" 
/dev/sde1: UUID="FC7C91187C90CF30" LABEL="GP" TYPE="ntfs" 
user@user-ubuntu:~$ 

what should be my next move?

---

### Post by Yellow Pasque on 2009-05-02
```
gksudo gedit /etc/fstab
```
Find line for the swap partition and paste in the new UUID so it looks like:
```
UUID=**e8681932-8d27-4050-8876-c98b216fc661** none            swap    sw              0       0
```
Reboot and run free -m to make sure it worked.

---

### Post by marcgh on 2009-05-02
Thanks guy's, both of you.

It's working perfectly !

---

### Post by hyperdude111 on 2009-05-02
@marcgh

Off topic but its the first time i have seen someone from Ghana o the forums, being half-Ghanaian i am pleased to see there are others using ubuntu.

---

