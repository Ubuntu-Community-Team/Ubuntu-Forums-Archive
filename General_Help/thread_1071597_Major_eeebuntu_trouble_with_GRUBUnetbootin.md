---
title: "Major eeebuntu trouble with GRUB/Unetbootin"
date: 2009-02-15
forum: General Help
---

### Post by D_one on 2009-02-15
I have a similar but slightly different problem, 

I have an eee 900ha, I had installed eeebuntu with unetbootin with no problems, I then had the brilliant idea to use remastersys to create a bootable iso image of my system then use unetbootin to make a bootable sd card from that image.  Great in principal but I made a fatal error, my sd card came up as sda2 in my system (I have since learned that it must have been an sdb), so I chose to show all file systems in unetbootin and proceeded to make  the bootable disk.  Now, I can boot into my system, but only the one on sda2, my bootmenu has been replaced with the one from unetbootin and has no options for Windows.  Further, it is not my original filesystem but the re-created one by unetbootin.  
 
How can I recreate the boot options I had before?

What was originally on my sda2 that may have been re-written?

Thanks to anyone who can help here!

---

### Post by bapoumba on 2009-02-16
Move to its own thread, and bump.

---

### Post by D_one on 2009-02-16
Re: Howto: Create LiveUSBs from Windows using a GUI (UNetbootin)

I have looked at a few other places for some help here but I will try here.

I used remastersys to create a custom iso image of my ubuntu install then used unetbootin to put it on an sd card and make it bootable, works great, (the second time for me unfortunately) It is a great combo of tools to create a bootable restore of your system on an sd card.

So here is where I made my mistake: The first time around My sdb1 (sd card) was coming up under sda2 (wha t I thought was my sd card, but was actually some other file system, possibly related to windows).

Now I have a custom install of my original system (eeebuntu filesystem was originally on sda6, and is still there) and the boot loader installed with unetbootin replaced my old one that let me choose between windows and eeebuntu. Now I cant boot into either. Lucky for me, my backup version works almost as well as the original and I sucessfully made the bootable sd card the second time around.

Has anyone else encountered this?

So my questions:

Idealy I just want it back the way it was.
1.Can I install another boot loader that will recognize my windows (hopefull it still works since I dont have a cd drive)?

2. I cant seem to find my origina menu.lst in my original file system, is it gone? I dont see such a file in the unetbootin version, Where does it choose it's boot options? Can I edit that to my old configurations?

3. Is there any other changes that I would have to do in order to get my other two systems to be bootable?

Asus eee 900ha,

$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e4538c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3188 25607578+ 7 HPFS/NTFS (windows)
/dev/sda2 18432 19452 8201182+ b W95 FAT32 (where I accidentally used unetbootin to install the iso image)
/dev/sda3 19453 19457 40162+ ef EFI (FAT-12/16/32) (?not sure here)
/dev/sda4 3189 18431 122439397+ f W95 Ext'd (LBA) (?not sure here)
/dev/sda5 3189 3218 240943+ 7 HPFS/NTFS
/dev/sda6 3219 6405 25599546 83 Linux
(my original eeebuntu install)
/dev/sda7 6406 17808 91594566 b W95 FAT32
/dev/sda8 17809 18431 5004216 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8199 MB, 8199864320 bytes
255 heads, 63 sectors/track, 996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000888c4

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 996 8000338+ b W95 FAT32


Help
Thanks in advance!

OK, so I was easily able to boot back into windows by using partition editor to change the boot flag. However, after trying to change the boot flag to all the other partitions, I think that I erased the partition that had my boot list on it. Thus I still have only 3 options, boot into windows, boot into a live version on sd card (by holding esc) or boot to the copy of my system on sda2. So, my question is really the same, how do I either get my old menu.lst back, or edit the existing one that was installed with unetbootin to work with my system (allow for options to boot into my original system or windows).

Help, anyone?

	
Re: Howto: Create LiveUSBs from Windows using a GUI (UNetbootin)
And, before a reply I solved it

I downloaded and installed supergrubdisk and it basically found my old grub and re-installed it on the original partiition that my system was on!

I am amazingly impressed with these tools. It seems that whatever I want to do, someone has thought of and done it (except found a way for me to print on my lexmark printer which is really the only reason that I would keep xp on).

So: for all those other eee users out there or anyone without an optical drive (the netbooks are coming....)

**Remastersys**: a tool to create a bootable iso of your system as is now, combined with;
**Unetbootin**: to put that .iso on your sd card is more or less a must have. Do not choose to "show all drives" here if you sd card doesnt come up, just reformat your sd card and it should come up just fine (that was my mistake). If you do by accident replace your working os with the unetbootin version, get
**supergrubdisk**: put it on another sd card (or the same one if you dont need to boot into the card) and choose the install of linux that you want grub to be in.

I am now more or less completely worry free with my eee since I can always boot from the sd card into my exact system with all my tools to fix ..... almost' anything, or so it seems.

:popcorn:my computers back baby!

Im no longer sure if these posts are relevant here, feel free to move them somewhere else if needed.

---

