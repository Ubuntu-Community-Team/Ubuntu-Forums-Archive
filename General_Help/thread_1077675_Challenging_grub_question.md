---
title: "Challenging grub question"
date: 2009-02-22
forum: General Help
---

### Post by theb3s7 on 2009-02-22
Hello!
I had installed several operating systems (four - Ubuntu 8.10, Windows XP x64, Windows Vista Business x64 and Windows 7 x64). The tricky part is the following: I want to keep the layout of the partition table as follows:
[[IMG]http://img294.imageshack.us/img294/1473/gpartedtox.th.png[/IMG]](http://img294.imageshack.us/img294/1473/gpartedtox.png)
The question is... Can I boot Windows XP, Vista and Windows 7 ?
Currently I can only boot Ubuntu :)

More info:
 - Grub is installed in MBR
 - sda1,sda3 = primary partitions
 - sda2 = extended partition
 - sda5 to sda8 = logical partitions


Thanks for any help!

---

### Post by kestrel1 on 2009-02-22
Can you post your current menu.lst file```
gedit /boot/grub/menu.lst
```

---

### Post by theb3s7 on 2009-02-22
Sure, here it is:

```

splashimage (hd0,6)/boot/grub/splashimages/97109-bam.xpm.gz
default 0
timeout 5

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista (loader)
root (hd0,0)
chainloader +1
makeactive

title Windows 7 (loader)
root (hd0,5)
chainloader +1

title Windows XP (loader)
root (hd0,4)
chainloader +1

```

I added manually the last three entries.

---

### Post by kestrel1 on 2009-02-22
Not sure this will work, but try the below ```
splashimage (hd0,6)/boot/grub/splashimages/97109-bam.xpm.gz
default 0
timeout 5

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=a2d6b50f-26a7-4dfa-85e3-672e0a64ced9 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Microsoft Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           Windows 7 (loader)
root            (hd0,2)
savedefault
makeactive
chainloader +1

title          Windows XP (loader)
root           (hd0,1)
savedefault
makeactive
chainloader +1 
```

---

### Post by theb3s7 on 2009-02-22
Well the results aren't good.. probably because every windows bootloader is messed up.. (it's been a more complicated process I guess that's why)..
So.. 
Neither of the three Windowses booted :p
Vista froze with a black screen and the keyboard was inoperable,
Windows 7 tried to load something - I'll try to repair it, I think this one is my best chance,
and finally XP said that the partition doesn't exist or something like that :D

I guess now I have to search for the DVD's for each one of them so that I can repair their boot files...
Cheers and  thanks for your help

---

### Post by caljohnsmith on 2009-02-22
So what happens when you boot the first Windows entry in your menu.lst:
```
title Windows Vista (loader)
root (hd0,0)
chainloader +1
makeactive
```
Does that boot Vista, and if not, what exactly happens? Since you have Windows 7 and Windows XP both installed to logical partitions, most likely their boot files are in your Vista sda1 partition. If you want to boot all three Windows separately from Grub, you will probably have to put their boot files back in their respective partitions and reconfigure them. I think it would help to get a clearer picture of your setup, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, and then do the following:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post. That will help clarify your setup.

---

### Post by theb3s7 on 2009-02-22
That's the thing.. :)
At first, I installed (in this order) the operating systems, on three different ACTIVE partitions: XP (wich stopped working after installing Vista), Vista, Win7.
After that I made a backup for each with Parted Magic, changed the partitions (so that it looks like the picture attached), restored Vista and Win 7, installed XP, installed Ubuntu :)

So.. it's a bit more complicated, but I'll try the bootinfoscript. Thanks for your suggestion.

LE: I listed you the history but forgot to answer your question - no, it does not boot Vista. A black screen appears and the keyboard is frozen (for example when I press on caps lock, the led doesn't light up). I'll try to recover the Vista boot files somehow..

---

### Post by kestrel1 on 2009-02-22
If you had previously installed each OS then taken an image & restored the image to a different part of the drive, that will be your problem. The Windows boot loaders do not like being arranged in a different manor.
For instance, if XP was originally on part1 of disk1 (hd0.0) & you then move it to part3 of disk1 (hd0,3) it will not load. You could try finding the files that make Windows boot. In XP's case that is Boot.ini. Not sure about Vista & Win 7 butI am sure there will be something on the net. You should be able to edit them from Ubuntu.

---

### Post by caljohnsmith on 2009-02-22
If you want to go through enough trouble, I think you can still get all three of your Windows installations to boot, but it would take quite a bit of work. But since they are all fresh installs, I would set up your partitions carefully and reinstall them if I were you. Yet if you want to keep them and try and get them booting, I think you will find all the answers you need in meierfra's [tutorial on booting XP/Vista/Win7]("http://ubuntuforums.org/showthread.php?t=813628") (even from logical partitions). Let me know if you decide to try that tutorial.

---

### Post by theb3s7 on 2009-02-22
That's exactly what I want to do, preserving the old installs :)
They're not fresh installs.. that's why I want to use the backups.

I will follow the tutorial tomorrow since I have to wake up in 5 hours and I didn't even fell asleep yet :p

Thank for your help!
I'll keep you posted with my progress.

L.E.: I've tried to get XP working but there are some anomalies.. I'm reinstalling it and after that I'll try to see what can I do next.. I'll be back in about an hour

L.L.E.: Experiencing a very strange problem with three different Windows XP X64 CDs: a black screen and system freezes, the installation (text-mode) doesn't start. I'll try fixing Win 7 and Vista..

L.L.L.E.: Great succes! Vista is now operable - I'm guessing this was the easy part since it's installed on an primary partition..

---

### Post by theb3s7 on 2009-02-23
I reinstalled Windows XP (taking care first of hiding the Vista partition so that it won't mess with that bootloader) and everything boots OK. -> rootnoverify  (hd0,2) chainloader +1. It actually installed the bootloader on the primary partition, sda3 (Data) that's why hd(0,2).
Vista booted fine, as I was saying, the only problem remained Windows 7, the operating system residing on a logical partition, with no other active partition to spare for installing its bootloader on. So I made a trick. A dirty trick I might say. Since I don't know how to map the partitions in such a way that Windows 7 should think it's residing on a primary partition, I entered EasyBCD (it was already installed, couldn't help it), installed the EasyBCD bootloader (that also overwritten the MBR but I fixed that with a SuperGrub disk very easily, reinstalling my good ol' grub) and added an entry for the Windows 7 partition. Magic! It worked! GRUB -> Easy BCD on hd(0,0) -> Vista or Win7 :)

Anyway I can't really say I'm happy with this, I still want to be able to access the Win7 directly from GRUB without having to enter EasyBCD bootloader first. If anyone has suggestions for achieving that.. please post them here :)

I also attached the new "RESULTS.txt" from the "boot_info_script27.sh", script if anyone is curious.

Best regards,
Alex

---

