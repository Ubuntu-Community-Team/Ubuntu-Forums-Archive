---
title: "GRUB and booting problems"
date: 2009-07-13
forum: Desktop Environments
---

### Post by michellez on 2009-07-13
Hi,

I've been meaning to do this for a while and found an old 128MB pen drive the other day so have got round to it. I run 2 hard drives in a striped RAID, which is why I've only had Ubuntu on my laptop! ;) I've never sussed out how to get linux to boot straight off a striped RAID.

/dev/sda = 250GB HD (part 1 of striped RAID)
/dev/sdb = 250GB HD (part 2 of striped RAID)
/dev/sdc = 128MB USB pen stick

sda+sdb have 4 partitions
1=Windows
2=Data
3=Swap
4=Linux /

sdc has 1 partition
1=/boot

Using the Ubuntu 9.04 Desktop 64bit CD.

I boot on to the CD..
I install mdraid so my raid gets mapped as follows:
/dev/mapper/isw_cjfgbdcfe_Volume0 .. then 1/2/3/4 as applicable on the end

First off I just tried the normal installer and told it where to put the /boot parition.
This results in "Missing operating system" when booting off the USB stick afterwards.

Redid it but then did grub myself and:
root (hd0,0)
setup (hd0,1)

This now gets grub loading from the pen drive but it just sits there on "Boot from (hd0,0) ext3 ..."

Not sure why it is hd0? Surely sdc should be hd2?
Never touched RAID+Grub before so generally confused :(

menu.lst has (not sure if there is any thing else in it that is useful?):
```
# kopt=root=/dev/mapper/isw_cjfgbdcfe_Volume04 ro

# groot=11b768df-bad2-446c-bdb2-b5af8a552e88

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            11b768df-bad2-446c-bdb2-b5af8a552e88
kernel          /vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_cjfgbdcfe_Volume04 ro quiet splash
initrd          /initrd.img-2.6.28-11-generic
```

Any help appreciated! I would really like to get Ubuntu going on this desktop PC finally!

Thanks,
Michelle

---

### Post by michellez on 2009-07-21
Has no one any ideas? Would I be better posting this in the server forum?

Found the "Advanced" button at the end of the installer the other day and used the option in there to install the boot loader on the pen stick, but I got the exact same upon boot. Grub started but then just sat there, just got like when I did it manually "Boot from (hd0,0) ext3 <lots of random chars>"

---

