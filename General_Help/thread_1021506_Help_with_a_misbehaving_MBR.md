---
title: "Help with a misbehaving MBR"
date: 2008-12-25
forum: General Help
---

### Post by nathockens on 2008-12-25
Hello Wbui friends. I got sent over here from the installation forum.

Just installed 8.10 over (under?) XP with the Live CD inside of the OS.

Now, I want to get Windows' MBR to put Ubuntu first. Can't seem to beat the MBR into submission though.

Right now it reads:
> [boot loader]
timeout=10
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect 

I tried putting "c:\wubildr.mbr="Ubuntu" above the other operating system and also put it as:
default=c:\wubildr.mbr="Ubuntu"

But putting it above doesn't matter (default still goes to XP) and changing the default as written just creates an error.

I also went through the above guide but on typing "find /grub/stage1" or "find /boot/grub/stage1" I stll get Error 15.

Running fdisk -l only shows an NTFS partition.

Here are the contents of my wubildr.mbr file on the c: root:
> scrambled crap
---
Press space bar
Press to start GRUB, any other key to boot previous MBR ...
Timeout : 
Invalid previous MBR. Press any key to start GRUB ...
Cannot find GRLDR. to hold the screen, any other key to boot previous MBR ...
Error while reading MBR of drive (hd0 )
Invalid boot indicator in partition table of
Invalid sectors_per_track in partition table of
Invalid start_sector in partition table of
Invalid end_sector in partition table of
No boot signature in partition table of
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart.
Try (hd0,0 ) : EXT2: NTFS4: NTFS5: NTFS5p: FAT32: FAT16: FAT12: non-MS: skip Extended: invalid or null This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there. hot-key  GRUª 

Also, under System Properties | Startup and Recovery the default OS is set to "Ubuntu"

Any ideas? I'm really irritated.

---

### Post by caljohnsmith on 2008-12-25
How about changing your boot.ini to:
```
[boot loader]
timeout=10
[COLOR="Blue"]default=C:\wubildr.mbr[/COLOR]
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect 
```
I believe that works, but how about giving it a shot and let me know how it goes.

---

### Post by nathockens on 2008-12-25
That did it. :)

You have my most gracious thanks



Nat

---

### Post by caljohnsmith on 2008-12-25
Glad that did the trick; cheers, have fun with Windows and Ubuntu, and Merry Christmas. :)

---

### Post by wackenedgar on 2011-04-30
Hello , 
I have the same above problem exceot with a windows 7 pc. Windows 7 does not have a boot.ini file.
How does windows 7 do it ?
Thanks
Edgar

---

