---
title: "Cannot run off usb"
date: 2018-01-22
forum: Desktop Environments
---

### Post by pmbergin on 2018-01-22
I recently decided to try Ubuntu-Studio on my 64 bit HP-15 laptop. I created an iso boot on a flash drive, and used the "try it out" mode to see if I liked it. I was unable to enable wifi (couldn't turn on the wifi button) and decided against an install. I later attempted to try various other flavors of Linux... Mint, desktop etc... but when I booted from the flash with the new iso, the system reverted to back Ubuntu-Studio. I reformatted the flash drive and recreated the install numerous times, and keep getting the same result.

This only happens on the HP laptop, I boot from the usb on other machines and get the correct install.

Any ideas?

---

### Post by TheFu on 2018-01-22
Welcome to the forums.

I have no idea how a flash drive written with 1 OS is somehow, magically, running a different OS.  All I can ask is "are you sure?"  How are you writing the ISO files to the flash drive?  dd?  mkusb?  Something else?  Could you have left a flash drive connected to the HP and it is booting from that?

---

### Post by pmbergin on 2018-01-23
Nope! :P

I just now redid the usb with Linux Mint so I'd immediately recognize a different presentation. I booted from the usb on my laptop and, sure enough Ubuntu Studio. I booted from the same usb drive on a different and, sure enough, Linux Mint. I'm using "Universal USB Installer," and I see no reason why that should be an issue since everything is fine everywhere else. BTW, this laptop has NEVER had a Linux installation on it so there's no existing Linux partition.

I don't get it.

---

### Post by sudodus on 2018-01-23
I think you have written Ubuntu Studio to a drive in the 'stubborn computer'. Otherwise it would not boot into it. Please boot from the USB pendrive and run the following commands,

```

df
sudo lsblk -f
sudo lsblk -m
sudo parted -ls

```

-o-

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

This will help us help you.

---

### Post by pmbergin on 2018-01-23
I was thinking along those lines myself, but the bios is set to boot to the usb first. At any rate I'll give that a shot.

---

### Post by pmbergin on 2018-01-23
```

Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1950132         4   1950128   1% /dev
tmpfs             393216      6308    386908   2% /run
/dev/mmcblk0p1  61079548  29770376  31309172  49% /cdrom
/dev/loop0       2787456   2787456         0 100% /rofs
aufs             1966072      4668   1961404   1% /
tmpfs            1966072         0   1966072   0% /dev/shm
tmpfs               5120         0      5120   0% /run/lock
tmpfs            1966072         0   1966072   0% /sys/fs/cgroup
tmpfs            1966072         8   1966064   1% /tmp
tmpfs             393212        20    393192   1% /run/user/999
/dev/sda3      467732796 228927088 238805708  49% /media/mint/Windows

~$ sudo lsblk -f
NAME    FSTYPE  LABEL    UUID                                 MOUNTPOINT
loop0   squashf                                               /rofs
sda                                                           
&#9500;&#9472;sda1  vfat             1CED-E77B                            
&#9500;&#9472;sda2                                                        
&#9500;&#9472;sda3  ntfs    Windows  DAA284C8A284AA99                     /media/mint/Window
&#9500;&#9472;sda4  ntfs             C6EEB392EEB378EF                     
&#9492;&#9472;sda5  ntfs    RECOVERY 84C83A29C83A1A3E                     
sdb                                                           
&#9492;&#9472;sdb1  vfat    UUI      72BA-4A7E                            
sr0                                                           
mmcblk0                                                       
&#9492;&#9472;mmcblk0p1
        ntfs    UUI      0EC86563C86549D3                     /cdrom

sudo lsblk -m
NAME          SIZE OWNER GROUP MODE
loop0         2.7G root  disk  brw-rw----
sda         465.8G root  disk  brw-rw----
&#9500;&#9472;sda1        260M root  disk  brw-rw----
&#9500;&#9472;sda2        128M root  disk  brw-rw----
&#9500;&#9472;sda3      446.1G root  disk  brw-rw----
&#9500;&#9472;sda4        976M root  disk  brw-rw----
&#9492;&#9472;sda5       18.4G root  disk  brw-rw----
sdb           7.5G root  disk  brw-rw----
&#9492;&#9472;sdb1        7.5G root  disk  brw-rw----
sr0          1024M root  cdrom brw-rw----
mmcblk0      58.3G root  disk  brw-rw----
&#9492;&#9472;mmcblk0p1  58.3G root  disk  brw-rw----

 sudo parted -ls
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  274MB  273MB   fat32        EFI system partition          boot, esp
 2      274MB   408MB  134MB                Microsoft reserved partition  msftres
 3      408MB   479GB  479GB   ntfs         Basic data partition          msftdata
 4      479GB   480GB  1023MB  ntfs                                       hidden, diag
 5      480GB   500GB  19.7GB  ntfs         Basic data partition          hidden, diag


Model: Kingston DataTraveler 160 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8011MB  8007MB  primary  fat32        boot, lba


Model: SD SD64G (sd/mmc)
Disk /dev/mmcblk0: 62.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.8MB  62.6GB  62.5GB  primary  ntfs         boot

```

---

### Post by pmbergin on 2018-01-23
The pathology is as follows:

I boot to the usb, I choose to run Mint
I get the Mint splash screen
When the computer starts, its starts to Ubuntu Studio

When I do the same on a different machine it runs Mint

---

### Post by pmbergin on 2018-01-23
Never mind, I got it. I had inadvertently written an iso to the sd card I use for backup. I pulled the card out and she booted right to Mint.

Thanks, if I hadn't seen that readout I never would have thought of that.

---

### Post by sudodus on 2018-01-23
> **pmbergin said:**
> Never mind, I got it. I had inadvertently written an iso to the sd card I use for backup. I pulled the card out and she booted right to Mint.

Thanks, if I hadn't seen that readout I never would have thought of that.

Yes, you got it :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by TheFu on 2018-01-23
My laptop has USB and SDHC ports. I sometimes forget to pull the SD card out after copying new photos off it.  An inserted SD card is flush with the case, so it is easy to miss. 
The system BIOS is stupid. It tries to boot off any external device and won't look at the internal disk even if there isn't any OS. Usually takes me 10+ minutes to check the SD slot when the boot fails.  I check everything else - power cord, battery levels, flash drives, but the SD card is first in the boot lineup, so none of the other things work either.

My point is that everyone does stuff like this. ;)

---

### Post by pmbergin on 2018-01-26
What I don't get is, since there's a full implementation on the usb (obviously,) why does it initially run off that, but switch to the SD card?

Doesn't make sense at all.

---

### Post by TheFu on 2018-01-26
BIOS controls that.  They probably figured 99.99999999999% of the people would boot from internal storage and didn't worry about the order for USB or SDHC boot much.  Too many choices is confusing to many people. Just ask any of the over-simplified UI makers.

---

