---
title: "dual boot with 2 hard drives ?"
date: 2007-05-25
forum: Desktop Environments
---

### Post by rweaver4 on 2007-05-25
I have 2 hard drives and used to run windows xp on both in dual boot mode. I have formatted both and put xp on one and ubuntu on the other. I now find that I do not get the option to select which operating system to boot. Both drives are set to 'cable select'. 
If I connect the xp disk to the first position (master) - then windows boots but doesn't recognise the other disk. If I swap their positions on the cable then ubuntu boots.
How do I set up dual booting?

---

### Post by adza on 2007-05-26
this one was quite easy for me to achieve... these steps were those that i followed ...

1) Download ubuntu distribution
2) burn iso
3) open BIOS, change boot order to cd, HDD, USB (or whatever)
4) still in BIOS changed boot priority of HDD to Linux drive first (this happened to be secondary IDE), then followed by Windows drive (primary SATA)
5) Started ubuntu in live cd mode
6) Fixed partitions on linux drive first
7) Installed ubuntu using installer
8) confirm installation of grub boot loader
9) Re-boot and then select operating system to boot into&#8230;

i think you need to change the boot priority on in BIOS to the linux HDD first, then GRUB will recognise the windows operating system.... you can leave the disk config the same (ie windows drive master etc), just make the change in bios....

---

### Post by rweaver4 on 2007-05-26
Thanks but changing the boot priority doesn't make any difference. Grub does not recognise the windows OS and Windows does not recognise the Linux OS. 
I think I will remove Ubuntu and reload it, maybe my installation missed the GRUB boot loader somehow.
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by s1mple_M4N on 2007-05-26
Hi rweaver4, try the forum thread below - it helped me in the same situation...

[http://ubuntuforums.org/showthread.php?p=677880#post677880]("http://ubuntuforums.org/showthread.php?p=677880#post677880")

Hope it helps,

RoyJ

P.S. I had this setup and when I upgraded from Dapper to Feisty, the installer detected my slave Windows OS and configured GRUB as dual-boot.

---

### Post by CarVac on 2007-05-26
I set my Windows hard drive to slave and (future) Ubuntu hard drive to master, then install it on the master hard drive. Ubuntu automatically configures the bootloader to recognize the Windows hdd. To get Windows to read your Linux hard drive you must use the program Explore2fs.You can use Automatix to configure your machine to automatically mount the Windows hard drive.

---

### Post by ugm6hr on 2007-05-26
If it still doesn't work - you can tell Windows bootloader to access GRUB somewhere else.  I had a setup like that with 2 partitions - but it should (theoretically) work with 2 separate MBR entries.  Have a look at this:

[http://ubuntuforums.org/showthread.php?t=453703&page=2](http://ubuntuforums.org/showthread.php?t=453703&page=2)

My (ugm6hr) post - Option 2 should be what you're looking for - but as mentioned there too - I've not tried it out myself.  Nevertheless, it will not do your system any harm - since it doesn't do anything to either OS - it just edits boot.ini for Windows (which is easy to correct).  staf4t5 seemed to solve his problem, but I'm not certain which route he tried - maybe you should ask him!

---

### Post by screaminj3sus on 2007-05-26
I have XP on my main SATA drive, and on my IDE drive I have ubuntu, I just hit f12 (or whatever loads your bois's boot menu) and select the drive that has ubuntu on it, it then loads grub and I can select ubuntu, not excatly gracefull but it works.

---

### Post by rweaver4 on 2007-05-26
Thanks guys for your suggestions, but I'm still left with no boot options.

I have re-installed Ubuntu on the master drive and it boots up OK, but at no stage do I get any option to dual boot. It behaves as if the second drive is not there even though the device manager lists both hard disks.

Pressing escape gets me a menu with no dual boot options.

I attempted to edit the menu.lst as suggested :

title Windows XP
root (hd1,0)
make active
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

but received the message that  'chainloader +1' was an invalid parameter.

Any more solutions?
rweaver4

---

### Post by ugm6hr on 2007-05-27
Worth trying my suggestion above if you're stuck.  It will require the Windows drive to be Master and 1st boot device though.

---

### Post by logos34 on 2007-05-27
> title Windows XP
root (hd1,0)
**make active**
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

try:

title        Windows XP
root        (hd1,0)
savedefault
**makeactive**  
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


Make sure /boot/grub/device.map lists your windows disk:

(hd0) /dev/hda
**(hd1) /dev/hdb**

---

### Post by rweaver4 on 2007-05-27
Thanks for your help ugm6hr and others, I'm still struggling with some concepts though, particularly editing and finding the linux files that need editing.
rweaver4

---

### Post by ugm6hr on 2007-05-27
> **rweaver4 said:**
> Thanks for your help ugm6hr and others, I'm still struggling with some concepts though, particularly editing and finding the linux files that need editing.
rweaver4

Maybe just use the other thread from now - I think it's confusing to have 2 running on the same problem.

[http://ubuntuforums.org/showthread.php?t=453703&page=2](http://ubuntuforums.org/showthread.php?t=453703&page=2)

---

