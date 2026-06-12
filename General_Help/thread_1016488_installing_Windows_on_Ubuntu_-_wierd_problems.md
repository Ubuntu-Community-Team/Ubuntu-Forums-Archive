---
title: "installing Windows on Ubuntu - wierd problems"
date: 2008-12-20
forum: General Help
---

### Post by smartsmokey on 2008-12-20
Used partition editor to create a partition of about 5gb so I'd have room to install Windows. I went back and booted the Windows disc, and it keeps telling me there are no hard drives. WTF? So I'm seeing this nice clean and open unallocated partition on the drive...yet Windows install disc doesn't even see the drive at all.

---

### Post by Slim Odds on 2008-12-20
Windows is not as forgiving as linux.

It needs a PRIMARY partition that is marked BOOTABLE.

It might even need to be the FIRST partition (not sure about that one).

---

### Post by Maelgwyn on 2008-12-20
From what I understand, Windows *does* need to be the first partition...

---

### Post by monkeyking on 2008-12-20
is it winxp og vista.

Newer computeres that have sata, cant be used on xp without som hacking.

a trick is to set harddrive driver mode in bios to compability mode/ide mode.

good luck

---

### Post by logos34 on 2008-12-20
> **monkeyking said:**
> is it winxp og vista.

Newer computeres that have sata, cant be used on xp without som hacking.

a trick is to set harddrive driver mode in bios to compability mode/ide mode.


yep, that's my guess too--if it's XP you're trying to install it's not seeing the disk because the Bios is in AHCI Sata mode rather than IDE legacy/emulation (vista by contrast has the drivers included).  The partition must be an active/bootable PRIMARY as mentioned above (but not necessarily first), and if you by chance had two or more disks it would also have to be set as the first/boot disk.

Or is this ide connected to pci card?  USB? (windows cannot be installed to latter without serious hack)

---

### Post by smartsmokey on 2008-12-20
okay I went back and changed the formatting of this newly created space called that was unallocated to FAT32. That should help. Now I'm wondering if WIndows NEEDS to be first on the list, would I go back with the livecd and gparted program and resize/make another partition from the main one, like i had done originally, but this time make this new fat32 space of 5gb or so in FRONT of the Ubuntu partition?
I'm running an IBM t60 that originally ran XP. I'm currently on Hardy 8.04

---

### Post by smartsmokey on 2008-12-20
here's a screenshot of where it is now...

---

### Post by logos34 on 2008-12-20
i'm saying it doesn't have to be first/at front of disk...the problem is something else  IMO.. What does 

sudo fdisk -l 

show?

edit: ok, I see you posted gparted screenshot...trying to look at it

---

### Post by logos34 on 2008-12-20
sda is the only disk?  and you've checked the Bios hdd settings?  sata or ide drive?

You could try flagging it as active/bootable in gparted (>right click on sda3>manage flags>boot)

---

### Post by smartsmokey on 2008-12-20
> **logos34 said:**
> 
sudo fdisk -l  show?


smartsmokey@smartsmokey-laptop:~$ sudo fdisk -l 
Password or swipe finger: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02910291

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11107    89216946   83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda3           11108       11784     5438002+   b  W95 FAT32
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
smartsmokey@smartsmokey-laptop:~$

---

### Post by smartsmokey on 2008-12-20
> **logos34 said:**
> sda is the only disk?  and you've checked the Bios hdd settings?  sata or ide drive?

You could try flagging it as active/bootable in gparted (>right click on sda3>manage flags>boot)
I'll try and flag it as bootable...but I want to flag the fat32 one as bootable, correct? Bios hdd settings/sata/ide drive....I don't really understand that.

---

### Post by logos34 on 2008-12-20
> **smartsmokey said:**
> but I want to flag the fat32 one as bootable,

yes
> 
correct? Bios hdd settings/sata/ide drive....I don't really understand that.

go into the Bios and look for section with hard disk settings--if you have sata then it could be the settings mentioned above

what does 

sudo lshw -C disk 

show?

---

### Post by smartsmokey on 2008-12-20
[QUOTE=logos34;6404101
what does 

sudo lshw -C disk 

show?[/QUOTE]
smartsmokey@smartsmokey-laptop:~$ sudo lshw -C disk
Password or swipe finger: 
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-4083N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.08
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: ST910021AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 4.06
       serial: TOPSECRET
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=02910291
Also, went into gparted, flagged fat32 partition as "boot" but no luck with install again.

---

### Post by logos34 on 2008-12-20
yep, sata (seagate Momentus)

so you need to check the bios next

---

### Post by smartsmokey on 2008-12-20
> **logos34 said:**
> yep, sata (seagate Momentus)

so you need to check the bios next

okay. Logos I'm not sure what I'm looking for in BIOS...and by BIOS I assume you're talking about the BIOS in the very beginning and not GRUB...right? I have to look back at the sata info and see what that was all about

---

### Post by logos34 on 2008-12-20
yes, at startup where you press F2 or F12 or whatever the key for your machine...What model notebook?  I can help you quickly google the user manual with Bios info

---

### Post by smartsmokey on 2008-12-20
wow! Logos I went into the BIOS and where the hard drive thing mentioned by someone earlier in this thread was, I changed it to "compatibility mode" and Windows XP is succesfully installing on the partition I created. We'll have to see if it actually installs, and if it does how will it effect my access to Ubuntu. If the latter is a problem, I found this -
[http://forums.techarena.in/guides-tutorials/1044180.htm](http://forums.techarena.in/guides-tutorials/1044180.htm)
which seems to get everything nice and neat under GRUB...so XP will be a boot option under GRUB. This is crazy stuff man! I'm like a computer programmer!

---

### Post by smartsmokey on 2008-12-20
> **monkeyking said:**
> is it winxp og vista.

Newer computeres that have sata, cant be used on xp without som hacking.

a trick is to set harddrive driver mode in bios to compability mode/ide mode.

good luck

arigato

---

### Post by logos34 on 2008-12-20
> **smartsmokey said:**
> wow! Logos I went into the BIOS and where the hard drive thing mentioned by someone earlier in this thread was, I changed it to "compatibility mode" and Windows XP is succesfully installing on the partition I created. We'll have to see if it actually installs, and if it does how will it effect my access to Ubuntu. If the latter is a problem, I found this -
[http://forums.techarena.in/guides-tutorials/1044180.htm](http://forums.techarena.in/guides-tutorials/1044180.htm)
which seems to get everything nice and neat under GRUB...so XP will be a boot option under GRUB. This is crazy stuff man! I'm like a computer programmer!

great to hear...I thought that might be the cause...'compatibility', 'ide legacy', 'ide emulation'-- goes byu diff names depending on machine/manufacturer.  Post back with the results...You'll have to change the Bios settings, though, before booting xp...and you'll need to add windows boot entry to menu.lst manually like this:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

Then add fstab entry so you can access windows from linux:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by smartsmokey on 2008-12-20
uh oh. XP install went fine until winlogon.exe failed because shell32.dll was nt found. Then, many "setup could not register OLE control c/Windows/system32/whatever" alerts. Went back to load Ubuntu with the livecd, because now Ubuntu seems to be gone. Then I need to run some stuff in sudo grub. What the heck, it never ends. Maybe I might try a better download of XP. It was XP essential SP2. Hope to GOd I can get back to my system.
  Also, why do I have to change the BIOS settings before booting WIndows? I cna't keep it on compatibility mode? Does it need to be changed back to the original one?

---

### Post by logos34 on 2008-12-20
ubuntu should be ok--all windows did is overwrite grub on the mbr.  You can restore grub using the live cd (see link in my signature).

Not sure about xp problem.  (edit: might try formatting as NTFS instead)

BTW, you can slipstream the sata drivers into a new cd image of xp using nLite, as shown here:
[http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1](http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C1)

---

### Post by smartsmokey on 2008-12-20
logos when u mention trying to format as ntcs or whatever it's called, do you mean do that in gparted or when the windows setup is running?

---

### Post by smartsmokey on 2008-12-20
I used the sudo grub commands you have in your sig using my livecd and it worked great. Only thing is it doesn't give the WIndows XP as an option...I know it wasn't installed all the way, but before when I loaded the computer without the livecd it started booting into Windows XP everytime and continued trying to setup
EDIT: in another tutprial on getting back GRUB it says find /boot/grub/stage2, not 1. Does that have anything to do with being able to see Windows as an option under GRUB?

---

### Post by logos34 on 2008-12-20
I gave you the link in post # 19 -- you have to manually add xp entry to menu.lst (in your case you want 'root (hd0,2)' 

no, stage1 is what you commonly search for; not the issue here

you might try running fixboot from the windows install cd (>recovery console>type fixboot at the prompt)

---

