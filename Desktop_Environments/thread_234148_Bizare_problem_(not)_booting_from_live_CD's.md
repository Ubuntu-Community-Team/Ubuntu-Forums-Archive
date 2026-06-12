---
title: "Bizare problem (not) booting from live CD's"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Doctoxic on 2006-08-11
Hi all

I am having problems booting from some live live CD's - history is as follows:

Ubuntu breezy Live CD used to work fine
i think i then installed a new hard drive
Live CD no longer worked
however Knoppix 4.02 live CD did boot fine
Dapper live CD does NOT boot
Knoppix 5.0 live CD does not boot (it boots ok on my other PC)
but Knoppix 4.02 live CD still boots ok

whats going on here?

What i think may be the problem is as follows (though who knows!)

I think it was after i installed an extra hard drive that i had big problems everytime there wa a kernal update in that my /boot/grub/menu.lst file would get updated to boot from sda whereas my boot drive is sdb - so i always have to remember to manually edit the file before i reboot - a bit of a pain if you forget!!!

I am thinking that some live CD's try to boot from sda only and others will keep looking until they find a real boot drive????

Is there anyway to make linux think that the sdb drive that it curently boots from is sda?

I have tried changing this:
title Ubuntu, kernel 2.6.15-26-k7
root (hd0,1)
kernel /vmlinuz-2.6.15-26-k7 root=/dev/sdb4 ro quiet splash
initrd /initrd.img-2.6.15-26-k7
savedefault
boot

To (hd1,1) - but it couldn't find a root partition

OR

Do you have any other ideas about what may be going on here?

Many thanks
Diss

---

