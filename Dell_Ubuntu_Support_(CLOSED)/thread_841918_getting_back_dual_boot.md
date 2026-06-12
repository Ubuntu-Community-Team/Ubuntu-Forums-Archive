---
title: "getting back dual boot"
date: 2008-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chubbtech on 2008-06-26
HI, I have a brand new Dell Inspiron 530 (core 2duo 3MB ram 250G HD) that came with Vista Home Basic.  After installing Hardy Heron Vista got corrupted somehow so I reintalled.  I know my ubuntu partition is still there but I want to get my boot menu back....is there an easy way?

thanx

---

### Post by Ptero-4 on 2008-06-26
You can use easybcd to boot ubuntu from the vista bootloader, or you can use the ubuntu liveCD to get to a cli, mount your HD, navigate to the mount point and type
```
chroot .
```
to change root (required)
then type
```
update-grub
```
to reinstall grub
and then
```
exit
```
to get out of the chroot.
And then reboot.

---

### Post by chubbtech on 2008-06-26
Actually my ubuntu cd didn't have the live option so I installed within windows, and guess what???  Ubuntu is trully amazing, it analyzed my disk and rebuilt the whole grub menu without me lifting a finger,  (or maybe this is just usual ubuntu behavior)
;)
thanx again

---

### Post by Law506 on 2008-06-26
Alright, change to all that I have said before.
I mounted my drive and navigated to the mount point and typed in update-grub, after the "chroot ." command.

I typed sudo to get all of those to work and it began working but came back with an error of permission denied with /dev/null.

I put sudo in front. "sudo update-grub" and got the permission denied error.  Is there something I missed in there?  I am on the LiveCD.

Thanks.

---

### Post by Ptero-4 on 2008-06-28
Hmm. If it failed, type 
```
sudo chroot .
```
that way you transfer the root credentials to the chroot.

---

