---
title: "Grub 2 hard drives, Ubuntu - Windows XP"
date: 2006-07-06
forum: Desktop Environments
---

### Post by spy1325 on 2006-07-06
i have 2 hard drives, a 200gb ubuntu , fresh install no partitioning, and a 250 gb harddrive with windows xp installed on it, and all my files. i installed ubuntu on the 200gb hard drive that i had laying around and just threw it into my comptuer to try it, and i like it very much , but i dont want to have to open my case and replug IDE cables to get XP to boot up, at the moment both HD's are on Cable Select and ubuntu is master at the end of the chain. WHen booting i can access the grub menu, but it does not recoginize Xp on the other hard drive. i have mounted the windows partition in ubuntu so i know it works. but how do i get Grub to recognize and give the the option of booting in my XP hard drive?

Btw , my fdisk -l reads

> Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       24415   196113456   83  Linux
/dev/hdc2           24416       24792     3028252+   5  Extended
/dev/hdc5           24416       24792     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       30400   244187968+   7  HPFS/NTFS


---

### Post by simonn on 2006-07-06
Is that the entire output of fdisk -l?

In /boot/grub/menu.lst, after:

```

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

```

Add the following:

```

title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

```

If that does not work, replace the ? in root (hd?,0)  with 0, 2 and 3 until one of them works. If it still does not work. Let me know.

---

### Post by spy1325 on 2006-07-06
thanks. does the spacing/tabbing matter for the format of 
> title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1

im off to try it now..

---

### Post by spy1325 on 2006-07-06
i just tried it with (hd1,0)

it failed to boot. adn was prompted with a black screen with

> Root (hd1,0)
filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

should i try with (hd2,0)??
or is there a certin way to find which hd?,0 itshould be?

EDIT:
iv tired Hd2,0 and hd3,0 and both respond with
> error 21: selected disk does not exist

---

### Post by simonn on 2006-07-06
If that does not work, replace the ? in root (hd?,0) with **0**, 2 and 3 until one of them works. If it still does not work. Let me know.

---

### Post by spy1325 on 2006-07-06
ok i have tired all possible combinations of (hd?,0)

the output of my menu.lst is 

> ## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST


that has what i added (i used hd0,0 that time. and it did not work it gave me an error about it being ext3 format nad not being bootable

---

### Post by simonn on 2006-07-06
Now we know that windows is on (hd1,0)

Try changing the chainloader line to 

```

chainloader (hd1,0)+1

```

---

### Post by spy1325 on 2006-07-07
that didnt work eather.. but i just figured out i can just use my BIOS boot manager (press ESC while booting) and select the windows hd. thanks for all the work. but iv found a much easier solution. iv gotten grub to work on a single hard drive with multiple partitions, but oh well thanks alot anyway for sticking with me

SPy

---

