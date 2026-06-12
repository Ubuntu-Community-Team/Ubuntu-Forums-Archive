---
title: "Dual Boot Issue with Ubuntu 9.04 and Windows 7"
date: 2009-06-21
forum: General Help
---

### Post by IAmNotAUser on 2009-06-21
I own a laptop with 2 seperate hard drives, 160gb each. Previously the laptop was running a dual boot Win Vista / Kubuntu 8.10. Hard drive A was a full 160gb partition with Windows Vista. Hard drive B was partitioned with 80gb NTFS as a share between the 2, 3gb Swap and the remaining space as Kubuntu.
I have now wiped hard drive A and installed Windows 7 RC, build 7100. I kept the first partition on the second hard drive, and spilt the other partition into 2, for a separate home drive, and then Ubuntu 9.04 with the remaining space as swap.

I installed Win 7 first, and then Ubuntu after, knowing I would have to correct Grub after in order to successfully dual boot.

However, after reinstallation, I have done the following steps using the Ubuntu LiveCD and still the grub menu does not show, and I boot straight into Win 7 without options.

On LiveCD:

```
sudo grub

find /boot/grub/stage 1 
root (hd1,4)
setup (hd1)
quit
```Where find /boot/grub/stage1 returns (hd1,4) and all complete successfully when I type the setup commend.

Any ides?

---

### Post by synapsys on 2009-06-21
You're installing grub to the second hard drive and booting of the first hard drive. In programming/computers we start counting at 0. Try changing hd1(2nd hard drive) to hd0(first hard drive). 

setup (hd0)

---

### Post by IAmNotAUser on 2009-06-21
EDIT: Thanks very much, I hadn't realised I needed to install to (hd0) when all the guides I found said use x where x,y were the values returned from find /boot/grub/stage1. I guess I am just difficult installing Windows 7 to the 1st HD and Ubuntu to the second, not the other way round.

---

