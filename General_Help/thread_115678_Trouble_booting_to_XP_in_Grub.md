---
title: "Trouble booting to XP in Grub"
date: 2006-01-11
forum: General Help
---

### Post by Hitchhiker427 on 2006-01-11
Hello, this is the scenario.  I installed Windows XP on a 160 GB hard drive, and got all of this set up, and working fine.  Then, I chose to install Ubuntu on a 60 GB hard drive.  I set the 60 GB as the master and the 160 GB as the slave via cable-select.  Alright, then, Grub managed to locate the XP installation, and when I restarted my computer, I was able to boot into either Ubuntu or XP flawlessly.  

Now, recently, I decided to give Windows XP x64 a shot to try things out.  Now, since my hard drives are connected via cable-select, all I had to do was unplug the linux hard drive, and I could deal solely with the Windows hard drive.  Using partition magic, I took 40 GB off of the original 160 GB and made a new partition in FAT32 (my main XP installation is in NTFS).  I managed to install x64 on this installation, and get everything working.  When I restart my computer, it lets me choose between XP x86 and XP x64, and it works fine.  

So, I opened up the computer, and plugged the linux hard drive back in.  When I restart the computer, I get the same grub menu I got before, which lets me boot into XP or Ubuntu.  If I select XP, it then takes me to a second menu (XP's boot loader) that lets me select my XP version.  I figured ti would be easier to just choose between x86 and x64 on the grub menu, instead of going through two seperate boot loaders, so I removed the x64 entry from boot.ini in XP, and this works fine.  

But, I'm having trouble adding the new partition to Grub.

This is my fdisk -l result:

```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14357   115322571    7  HPFS/NTFS
/dev/hdb2           14358       19457    40965750    f  W95 Ext'd (LBA)
/dev/hdb5           14358       19457    40965718+   b  W95 FAT32

```

Also, my current menu.lst:
```
title		Windows XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


title		-------
root

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7-smp
savedefault
boot

title		Ubuntu (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-k7-smp
boot

title		-------
root

title		Memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

```

Now, if I try to copy the current XP entry and just change (hd1,0) to (hd1,1), it doesn't work right, and won't boot.

I'm pretty new at this, so if someone could help that'd be great.

edit:  my device.map file:

```
(hd0)	/dev/hda
(hd1)	/dev/hdb
```

---

### Post by rune on 2006-01-11
Is it an NTFS partition you're trying to boot? then "rootnoverify" is the command you have to use instead of "root".

Also try to write down the commands to use and hit "c" when grub loads. Then try to boot it manually, and see what works, alot faster than booting, editing, rebooting.

---

### Post by spd106 on 2006-01-11
Not sure about this as i've never tried anything this complex but you could try hiding the first  windows partition. Have a look at the grub docs.
[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by dabang on 2006-01-11
Both "Windowses" use the same boot Partition, which ist the NTFS WinXP x86 partition. Trying to boot directly from your WinXP x64 partition will not work. If you like to boot both Win's directly with a non MS bootloader, I guess you have to hide the two Win-partitions from each other during the installation of WinXP x86 and x64. Sounds logical to me, but I'm not sure about this...

---

### Post by maqi on 2006-01-11
I have 2 XP installs on 1 HD and my Ubuntu install on another HD. I have never had to hide any partitions or anything to get it to work. If booting from hda alone brings up the list of XP installations to choose from then the M$ bootloader is working fine. I boot from the HD with the XP installs by running grub-install and installing GRUB to (hd0) and making sure that (hd0) is set as the boot disk in BIOS.

AFAIK GRUB just starts the standard XP bootloader and normally this works fine, as it did for you. By removing your x64 XP install from boot.ini XP can no longer "see" the x64 install and GRUB can't see it because the partition it is on is not mentioned in a separate Windoze entry in menu.lst. 

The easy fix is to replace the x64 entry in boot.ini ... you DID back it up didn't you? 

The harder fix is to give the x64 install its own entry in menu.lst, however, doing this will require finding out how to manually add a correct entry for that install. You will also need to write a boot.ini file for that install and have it sitting on the top level of your x64 install (ie, same place as it is on your normal install but on the new partition). And this is assuming that this will work from a logical partition - I am not sure that it will and tend to think that it won't! IIRC you can't boot from a logical partiton, and the Windoze bootloader will not look anywhere but C: for boot.ini - so ...

This would be a learning experience, but quite frankly a total PITA. Go with the easy fix and deal with the added step in the boot process would be my recommendation. When you get used to it you can use the arrow keys and "Enter" to boot your desired OS **before** the menus are visible on screen anyway. Very fast.

Hope this helps :)

---

### Post by dabang on 2006-01-11
> I have 2 XP installs on 1 HD and my Ubuntu install on another HD. I have never had to hide any partitions or anything to get it to work. If booting from hda alone brings up the list of XP installations to choose from then the M$ bootloader is working fine.

That's the point. Using grub to start the MS bootloader is no problem, but booting each Win with grub directly would require, that each Win has it's own "ntldr" in its root. Installing two WinXPs without hiding them from each other let's the second WinXP overwrite the first "ntldr". That's like installing WinNT and Win2000/XP together. The latest Win-version hast to be installed second or else it won't work because of incompatibility of the "ntldr". Please correct me if I'm wrong...

So I think maqi is right: just add the entry for WinXP x64 to boot.ini again...

---

### Post by Hitchhiker427 on 2006-01-11
oh well, that's annoying.  Yeah, I did back up my boot.ini, and can easily fix this using the "easy way".  However, I had it this way the whole time, and was trying to get it to work the "hard way", but it seems that won't work so well.

Thanks for your help everyone!

Also, rune, I'm confused.  You said that if I'm trying to mount an NTFS partition I have to use 'rootnoverify' instead of 'root'.  Well, this drive I'm trying to mount is in FAT32 (for easy transfer between Ubuntu and XP), however, the x86 version of Windows I already have installed IS in NTFS, and the grub bootloader works fine using 'root' instead of 'rootnoverify'.  Is there any reason why I should change this, if it's working fine?  thanks.

---

