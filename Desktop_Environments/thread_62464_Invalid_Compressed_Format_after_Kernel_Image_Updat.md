---
title: "Invalid Compressed Format after Kernel Image Update"
date: 2005-09-04
forum: Desktop Environments
---

### Post by smeager on 2005-09-04
I just recently updated my sys with the lastest security releses from ubuntu and everything went fine (can't remember what the newest kernel image is but I know it the newest one) until I turned it off and tried to reboot it. Well not so good.  During the boot process this is what I get.

LILO 22.6.1 Loading Linux .....................................(yes I'm using LILO waht can I say)

BIOS data check successful
Uncompressing Linux.....

invalid compressed format   (err=1)

- - System halted


I have never recieved anything like this before (or atleast nothing that I couldn't figure out myself). Any help on this would be greatly appreciated. Thanks in advance.

COMPUTER SPECS:  Dell Inspiron 9300
                               Pent M 1.6
                               DDR2 SDRAM 533mhz 1gb
                               80gb HD
                               Nvidia Geforce 6800 Go

---

### Post by smeager on 2005-09-04
Ok I figured it out shortly after posting. It seems that after updating the kernel image (via Synaptic) it did not run lilo like it is supposed to. This is what I did to fix it:

I downloaded Knoppix 3.9 ( had to use this version becuase it was th only live cd that would recoginize my hd as /dev/sda, all the rest saw it as /dev/hda which I could not use)

Booted into KNoppix and opened up a terminal.

I did this to get my system fixed:

1:   I had to mount my root partition so I typed -- mount /dev/sda6 (hd root part) /mnt
2:  Then I had to chroot into my root -- chroot /mnt
3:  Then I had to run lilo:  lilo

This ran LILO and reconfigured it for the updated image.

Since I have a dual boot system (and I' still using windows bootmgr as my main one) I had to copy my boot sector of my root partiton so I could update my bootmgr. This is what I did.

1:  After I ran LILO and got the new configuration I ran this:
   dd if=/dev/sda6 of=bootsect.lnx bs=512 count=1

This created a boot sect img that I could use.  I added this updated file to my bootmgr, rebooted my system (crossed my fingures) and selected Ubuntu from my boot menu and it booted into it without any problems.

Hope this helps out anybodye else that might be having the same problems.

(now starting on rebuilding my wireless drivers for the new image. wish me luck)

---

