---
title: "Adding XP to the boot loader/partitioning issue"
date: 2008-12-07
forum: General Help
---

### Post by pr1mal on 2008-12-07
[IMG]http://i239.photobucket.com/albums/ff58/Primal0ne/Screenshot--dev-sdb-GParted.png[/IMG]

[http://i239.photobucket.com/albums/ff58/Primal0ne/Screenshot--dev-sdb-GParted.png](http://i239.photobucket.com/albums/ff58/Primal0ne/Screenshot--dev-sdb-GParted.png)

Link to the gparted screen shot that i am talking about.  My XP install in the highlighted one sdb5

I am trying to add it to my grub bootloader.  It already contains working Vista and Ubuntu code pasted below incase you need it

title		Ubuntu3 8.04.1, kernel 2.6.24-21-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=8f12289e-88d7-4d35-b330-de552490c3ce ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I have tried many different codes for XP. but none of them work.  Here is the shell of what i have tried

title		Windows XP1
root		(hd0,X)
makeactive
chainloader	+1

where x has been every number 1-6

none of them load XP  numbers 4-6 all return "no such partition"

any ideas on how to get this XP into my bootloader code or asto why it is such a weird partition??

---

### Post by falcon61102 on 2008-12-07
Sorry, but I'm at work and can't view your photo bucket link.  Could you post the results of:
```
sudo fdisk -lu
```

That will list the partitions.

---

### Post by abrussak on 2008-12-07
Try 3....it looks like it lowers the number because it's loading your sdb1 as (hd0,0) and your sdb4 as your (hd0,3)

....so try 3. that MAY work, and if it doesn't....it's not like it can do anything.

---

### Post by mikewhatever on 2008-12-07
From what I heard, Windows always writes the files needed to boot to the first partition on the disk, the Vista partition, in your case. Try looking for an option to load XP while booting Vista.

---

### Post by falcon61102 on 2008-12-07
> **mikewhatever said:**
> From what I heard, Windows always writes the files needed to boot to the first partition on the disk, the Vista partition, in your case. Try looking for an option to load XP while booting Vista.

While having two boot-loaders would be a bit combersome, that just might work.  If you use Vista's boot loader to start XP that may be a good work around.  That being said, it should be possible to get XP to boot directly from the GRUB, it's just a matter of getting the settings right.

Do you receive any other errors besides the partition not found one?

And have you attempted to use the Super Grub Disk ( [www.supergrubdisk.org](www.supergrubdisk.org) )?

---

### Post by pr1mal on 2008-12-07
this is what fdisk -lu outputs

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b9bcef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   411160566   205580252    7  HPFS/NTFS
/dev/sdb2       435795255   466591859    15398302+   f  W95 Ext'd (LBA)
/dev/sdb3       466604032   488390655    10893312    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *   411167610   435795254    12313822+  83  Linux
/dev/sdb5       435795318   466591859    15398271    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by pr1mal on 2008-12-07
when I try and boot (hd0,3) it gives me

Error 13: invalid or unsupported executable format

That should be my linux partition so that is understandable

When I boot (hd0,2) it boots my special HP installed Vista recovery thing so i know that is not it
and (hd0,0) is vista

so this leaves (hd0,1) and (hd0,4+)

(hd0,1) and (hd0,4) returns

error 12:  invalid device requested

(hd0,5+) returns 

error 22: no such partition

If you look back at the picture provided it is weird that sdb5 is a sub of sdb2 and sdb2 is a "extended partition"  why is this and what does it mean,  also what does the flag LBA mean at the end

thanks for the quick replies
BTW this is on my SATA laptop drive

---

### Post by TeXtonyx on 2008-12-07
> **falcon61102 said:**
> While having two boot-loaders would be a bit combersome, that just might work.  If you use Vista's boot loader to start XP that may be a good work around.  That being said, it should be possible to get XP to boot directly from the GRUB, it's just a matter of getting the settings right.

Do you receive any other errors besides the partition not found one?

And have you attempted to use the Super Grub Disk ( [www.supergrubdisk.org](www.supergrubdisk.org) )?

I had that idea too, of booting XP with SGD and copying those
settings to menu.lst. But I don't think it will work. Vista 
really screws with the XP booting ability. I've seen the Vista
boot files, bootmgr etc. on the XP partition and the XP boot files, 
boot.ini ntldr etc have disappeared. (boot.ini may be hidden) 

Boot to Vista and look at the boot files contained in C:\ and 
then change over in Computer to probably D:\, sdb5, and look at 
the boot files. I strongly suspect the XP boot files are gone. 


So download free Easybcd and add XP to the boot menu. It might
not already be there if you installed XP after Vista. This won't
mess with grub so should be no problem. There is a limit of 4
primary partitions per drive, but I think your recovery partition
is "hidden" so that shouldn't interfere, otherwise you'd have 5.
It's not exactly easy to install XP to a fat32 partition. I think 
you can forget using grub for XP, I doubt there are boot files there.

---

### Post by caljohnsmith on 2008-12-07
If you installed XP to the sdb5 logical partition, XP would have put its boot files in some primary partition, most likely sdb1, but maybe even on your sda drive if it has a primary FAT/NTFS partition. Look for the following three XP boot files in your sdb1 or other partitions:
```
boot.ini
ntldr
NTDETECT.COM
```
I won't be around for another 8 hours, so if you don't have it sorted out by then, I can help out if you want.

---

### Post by falcon61102 on 2008-12-07
The 2nd partition in your list is called and Extended Partition and the partitions under it are called logical and LBA is a abbreviation for that.

In short, you HD can be partitioned a number of ways but can only have a max of 4 Primary partitions.  To be able to partition the drive more, an Extended partition is created and all the partitions within the Extended partition are called Logical partitions.

This also may be part of the problem.  Windows does not like to be installed in anything other than the first partition of the first drive.  It really doesn't like being installed on a Logical partition.  While this may be an issue, I don't think it's the only one here.

---

### Post by TeXtonyx on 2008-12-07
> **caljohnsmith said:**
> If you installed XP to the sdb5 logical partition, XP would have put its boot files in some primary partition, most likely sdb1, but maybe even on your sda drive if it has a primary FAT/NTFS partition. 

I didn't know this could happen. How does one go about installing
XP to a logical partition? I thought it was Vista which concealed
the files which XP used to boot with. How could you tell that
sdb5 was a logical partition rather than XP installed on a fat32
primary partition; because it is unlikely/difficult to do? Those
Gparted key icons mean that the partition is mounted, not primary,
so how do you tell from the fdisk report which partitions are primary
or logical, other than the one marked with an * ? [Herman?]

---

### Post by pr1mal on 2008-12-07
OK so i think you are right in stating that XP is on a FAT32 Logical Partition

Im not sure why this happened because it is the only logical partition on the Primary partition sdb2, but i dont think i can change this with out install XP all over again, and givent hat it is tablet XP this would not be fun.

So i am off to see where all those XP boot files are, in the mean time feel free to suggest anything, i tried getting Vista to have a bootloader to boot XP but it isnt working yet.

By the way the order all this happned in is  My laptop came with Vista and recovery partition.  I added XP, and XP took over the boot loader so i didnt see vista for a while.  Then Ubuntu came over and got installed.  Using grub i set up the bootloader and added all the other partitons in.  Now all three work besides XP

---

### Post by pr1mal on 2008-12-07
OK so ya there are no boot.ini or NTLDR or NTDETECT on my F: XP partition

so can i get those from another working XP(i've got plenty) or from the CD?  and do these files need to be changed or just straight copied over??

---

### Post by falcon61102 on 2008-12-07
Those files are the equivilant to your GRUB files so they are specific to that install.  Like caljohnsmith said, they may be on another partition.

---

### Post by TeXtonyx on 2008-12-07
> **falcon61102 said:**
> The 2nd partition in your list is called and Extended Partition and the partitions under it are called logical and LBA is a abbreviation for that.

In short, you HD can be partitioned a number of ways but can only have a max of 4 Primary partitions.  To be able to partition the drive more, an Extended partition is created and all the partitions within the Extended partition are called Logical partitions.

This also may be part of the problem.  Windows does not like to be installed in anything other than the first partition of the first drive.  It really doesn't like being installed on a Logical partition.  While this may be an issue, I don't think it's the only one here.

TeX: Perhaps I'm about to learn something else tonight and make 
me glad I stayed home from the movies. ... From the Wiki:

"Logical block addressing (LBA) is a common scheme used for 
specifying the location of blocks of data stored on computer 
storage devices, generally secondary storage systems such as 
hard disks.
C-H-S tuples can be converted to LBA addresses using the 
following formula: LBA = (C * heads * spt) + (H * spt) + (S - 1)"

So in the good ole days there was an 8GB or 32GB limitation 
which was in the bios. Then they invented LBA for modern bios
(32GB+>)so that one no longer has to put Linux boot partition at 
the front of the drive. I just mean that LBA is not an abbreviation 
for logical partitions, it's turned on in the bios.

I've seen an extended partition marked as primary. However, I
agree that you can put logical partitions within the extendedness
and I agree that it works best for Windows to be first but there's
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Mostly I posted about this because I couldn't tell from fdisk
or Gparted which were the primary and which the logical partitions. 
Take a look at this fdisk report,

Device Boot Start End Blocks Id System
/dev/sdb1 63 411160566 205580252 7 HPFS/NTFS
/dev/sdb2 435795255 466591859 15398302+ f W95 Ext'd (LBA)
/dev/sdb3 466604032 488390655 10893312 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4 * 411167610 435795254 12313822+ 83 Linux
/dev/sdb5 435795318 466591859 15398271 b W95 FAT32
Partition table entries are not in disk order 

It says /dev/sdb2 435795255 466591859 15398302+ f W95 Ext'd (LBA)
but what logical partition were created within the Extended? I 
doubt /dev/sdb4 which is his boot Linux partition and likely primary.

---

### Post by TeXtonyx on 2008-12-07
> **pr1mal said:**
> OK so i think you are right in stating that XP is on a FAT32 Logical Partition

Im not sure why this happened because it is the only logical partition on the Primary partition sdb2, but i dont think i can change this with out install XP all over again, and given that it is tablet XP this would not be fun.

So i am off to see where all those XP boot files are, in the mean time feel free to suggest anything, i tried getting Vista to have a bootloader to boot XP but it isnt working yet.

By the way the order all this happned in is  My laptop came with Vista and recovery partition.  I added XP, and XP took over the boot loader so i didnt see vista for a while.  Then Ubuntu came over and got installed.  Using grub i set up the bootloader and added all the other partitons in.  Now all three work besides XP

Well, Herman told me that XP can happen on a logical partition
but I think it takes a partition editor. But anyway, we have a
bigger kettle of fish to fry. 

I like to boot from XP and Vista stole the bootloading hammer.
So I reinstalled XP and Vista stole it again, after booting
Vista just once, afterward.

Did you try downloading Easybcd? It is not that hard to add
XP to the boot menu. I doubt that you can boot XP because the
XP boot files are likely hidden. No, it won't do any good to
copy them back or fixmbr fixboot bootcfg/rebuild (for boot.ini).
I think the first time you boot Vista, all that will be undone. Try 
Easybcd rather than manually adding to the database with bcdedit.

---

### Post by pr1mal on 2008-12-08
Thanks for the detail TEX
and yes sdb5 is a logical partition on the primary partition sdb2

im not sure why this happened, but i think i am correct in saying that i cant make sdb5 a primary partition (deleting sdb2) without messing up the XP install worse than it is.  
Would reformatting to make my drive straight 4 primary partitons and then reinstalling XP fix this?  but if I do that I am worried it will mess up my linux install and all because its partition number might change.

And before i go to bed tonight i will try out EasyBCD
what exactly am i trying to do with this??

---

### Post by TeXtonyx on 2008-12-08
> **pr1mal said:**
> OK so ya there are no boot.ini or NTLDR or NTDETECT on my F: XP partition

so can i get those from another working XP(i've got plenty) or from the CD?  and do these files need to be changed or just straight copied over??

The idea that those boot files are on your first hard drive on
another Windows partitition is outside my experience and I'm

[First of all, how do you install XP to a logical partition? May
be with a partition editor and some backup software, not likely.]

skeptical of it. But, it doesn't hurt to look. Do you have any
Windows partitions on the first drive? Also, which drive is set
to boot in your bios, hd0 (sda) or hd1 (sdb)? Like I said, I
don't think copying those files over is going to help since
Vista and XP are both installed on the same drive, sdb. I've
got XP on first drive and Vista on second drive, but Vista
doesn't reach across the void and subsume XP, stifling XP's
piteous cries, of: boot me, boot me, I'm next. 

But you may want to demonstrate this to yourself about trying
the copying of the boot files. Here is my boot.ini,

--------------------------------

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT
c:\UbuntuB.bin="Ubuntu"
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS
c:\linux.bin="Debian"

-----------------------------------------

TeX: You see where it says, " ;Warning ..."
Vista put that there when it devoured my XP; so I punished Vista.

multi(0)disk(0)rdisk(0)partition(1)

You can boot XP on a second drive from the first drive by
adding another line much like the one above to your boot.ini

multi(0)disk(0)rdisk(1)partition(1) 
change the rdisk value and/or change partition number if not 1.

So I boot both Ubuntu first disk, and Debian second disk from
XP's boot.ini using 512 byte boot sector fragments. If I had
Vista still installed on my second drive, I could boot it from
Ubuntu's menu.lst as I have done before on my other computer. 

This involved putting XP in the MBR. I don't think this would
work for you because I had XP and Vista on different drives 
where Vista doesn't interfere with XP, not like in your case.

Finally, if you found your XP files (which will make me look dumb)
on your first drive in a Windows partition, I would leave them
there and change your menu.lst to (hd0,X) where X is usually 0.
Again, I think your best shot is Easybcd. One thing you can try
under Manage Bootloader is to reinstall the Vista bootloader.
This might add XP. But then you have to reinstall grub or add
the *nix to Vista's bootloader. Under Add/Remove Entries you
choose Windows, Type and Drive have dropdown boxes, with options,
and as shown in the screenshot the name for XP is Earlier Version
of Windows. Btw, the SystemRescueCD is nice and useful.

---

### Post by caljohnsmith on 2008-12-08
Pr1mal, I have a bash script from forum member meierfra that will help us sort your problem out a lot easier. Please download the attached file of this post to your desktop and do:
```
sudo sh ~/Desktop/boot_info.sh.txt
```
And please post the results. If all goes well, that program will tell us where your Windows XP boot files are, and just as importantly, it will also tell us if Windows XP modified the boot sector of any of your other FAT/NTFS partitions. That's critical to know in order to effectively sort out your problem in case XP modified your Vista boot sector.

P.S. Many thanks to meierfra for putting together a bash script to do all the hard work so you won't have to do all the commands by hand. :)

---

### Post by caljohnsmith on 2008-12-08
> **TeXtonyx]The idea that those boot files are on your first hard drive on
another Windows partitition is outside my experience and I'm
[First of all, how do you install XP to a logical partition? May
be with a partition editor and some backup software, not likely.]
skeptical of it. But, it doesn't hurt to look.[/QUOTE]
I can understand you are skeptical, but here's two examples of Windows putting its boot files on the master drive when Windows was installed to the slave drive:  :)

[http://ubuntuforums.org/showthread.php?t=998327](http://ubuntuforums.org/showthread.php?t=998327)
[http://ubuntuforums.org/showthread.php?t=982933](http://ubuntuforums.org/showthread.php?t=982933)

Note the second example is especially noteworthy because the user had sdb configured as the master drive, so even though Vista was installed to sda, Vista put its boot files on the sdb drive. Some people assume that sda is the master drive, but that isn't always true. 

[QUOTE=TeXtonyx said:**
> I didn't know this could happen. How does one go about installing
XP to a logical partition? I thought it was Vista which concealed
the files which XP used to boot with. How could you tell that
sdb5 was a logical partition rather than XP installed on a fat32
primary partition; because it is unlikely/difficult to do? Those
Gparted key icons mean that the partition is mounted, not primary,
so how do you tell from the fdisk report which partitions are primary
or logical, other than the one marked with an * ? [Herman?]
One easy way to know if a partition is logical or not is just to go by its number; all logical partitions start at sdX5 (e.g. sda5, sda6, sda7, etc.), while all primary/extended partitions will use sdX1-sdX4 (e.g. sda1, sda2, sda3 and sda4). You can confirm it checking the partition table, for instance:
```

/dev/sdb1 63 411160566 205580252 7 HPFS/NTFS
/dev/sdb2 [COLOR="Blue"]435795255[/COLOR] [COLOR="Blue"]466591859[/COLOR] 15398302+ f W95 [COLOR="Blue"]Ext'd[/COLOR] (LBA)
/dev/sdb3 466604032 488390655 10893312 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4 * 411167610 435795254 12313822+ 83 Linux
/dev/sdb5 [COLOR="Blue"]435795318[/COLOR] [COLOR="Blue"]466591859[/COLOR] 15398271 b W95 FAT3
```
So note sdb2 is the extended partition, and it begins at sectors 435795255 and stops at 466591859. sda5 starts at 435795318 and stops at 466591859, which is inside that range, just as we expect; all logical partitions must be inside the extended partition. Also, from Pr1mal's gparted screenshot in post #1, notice how it shows sda5 indented and underneath the sda2 partition; all logical partitions will be shown that way for clarity to imply that the logical partitions are actually inside of the extended partition.

So the bottom line is it is possible to install Windows to a logical partition (even on a slave drive), but only if you have a primary NTFS/FAT partition on the master drive where Windows can put its boot files; if no partition like that is available, Windows will refuse to install to a logical partition. Windows does that because its boot code in the MBR has no brains and can only boot whichever primary partition is marked bootable on the master drive. If you use Grub though, you can put Windows boot files back in its own partition (even if it is a logical partition), and if you reconfigure boot.ini (XP) or BCD (Vista) to point to the correct logical partition, then you can boot Windows entirely from the logical partition. :)

P.S. All credit goes to forum member meierfra who took the time to figure out how to boot Windows XP/Vista from a logical partition in the manner I briefly describe above.

---

### Post by TeXtonyx on 2008-12-08
Originally Posted by TeXtonyx
"The idea that those boot files are on your first hard drive on
another Windows partitition is outside my experience and I'm
[First of all, how do you install XP to a logical partition? May
be with a partition editor and some backup software, not likely.]
skeptical of it. But, it doesn't hurt to look."
---------------------------------------------------

caljohnsmith responded:

> **caljohnsmith said:**
> I can understand you are skeptical, 
but here's two examples of Windows putting its boot files on the 
master drive when Windows was installed to the slave drive:  :)

[http://ubuntuforums.org/showthread.php?t=998327](http://ubuntuforums.org/showthread.php?t=998327) 
[http://ubuntuforums.org/showthread.php?t=982933](http://ubuntuforums.org/showthread.php?t=982933)

Note the second example is especially noteworthy because the 
user had sdb configured as the master drive, so even though 
Vista was installed to sda, Vista put its boot files on the 
sdb drive. Some people assume that sda is the master drive, 
but that isn't always true. 

One easy way to know if a partition is logical or not is just 
to go by its number; all logical partitions start at sdX5 (e.g. 
sda5, sda6, sda7, etc.), while all primary/extended partitions 
will use sdX1-sdX4 (e.g. sda1, sda2, sda3 and sda4). You can 
confirm it checking the partition table, for instance: 
```

/dev/sdb1 63 411160566 205580252 7 HPFS/NTFS
/dev/sdb2 [COLOR="Blue"]435795255[/COLOR] [COLOR="Blue"]466591859[/COLOR] 15398302+ f W95 [COLOR="Blue"]Ext'd[/COLOR] (LBA)
/dev/sdb3 466604032 488390655 10893312 7 HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sdb4 * 411167610 435795254 12313822+ 83 Linux
/dev/sdb5 [COLOR="Blue"]435795318[/COLOR] [COLOR="Blue"]466591859[/COLOR] 15398271 b W95 FAT3
```
So note sdb2 is the extended partition, and it begins at sectors 435795255 and stops at 466591859. sda5 starts at 435795318 and stops at 466591859, which is inside that range, just as we expect; all logical partitions must be inside the extended partition. Also, from Pr1mal's gparted screenshot in post #1, notice how it shows sda5 indented and underneath the sda2 partition; all logical partitions will be shown that way for clarity to imply that the logical partitions are actually inside of the extended partition.

So the bottom line is it is possible to install Windows to a 
logical partition (even on a slave drive), but only if you have 
a primary NTFS/FAT partition on the master drive where Windows 
can put its boot files; if no partition like that is available, 
Windows will refuse to install to a logical partition. Windows 
does that because its boot code in the MBR has no brains and can 
only boot whichever primary partition is marked bootable on the 
master drive. If you use Grub though, you can put Windows boot 
files back in its own partition (even if it is a logical 
partition), and if you reconfigure boot.ini (XP) or BCD (Vista) 
to point to the correct logical partition, then you can boot 
Windows entirely from the logical partition. :)

P.S. All credit goes to forum member meierfra who took the time to 
figure out how to boot Windows XP/Vista from a logical partition in 
the manner I briefly describe above.

----------------------------------------------------

Yes, his posts are very often educational. And that script is a
very clever idea for something to do, not just in the writing of it.

You deserve credit for very generously sharing this script. I have
a book of scripts called Tips & Tricks so really appreciate this.
Also I like some theory to come into play especially when there
is a practical problem to resolve in this case like pr1mal has.

----------------------------------------

[http://ubuntuforums.org/showthread.php?t=998327](http://ubuntuforums.org/showthread.php?t=998327)

/dev/sda4   *   297491670   312576704     7542517+   7  HPFS/NTFS

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS

----

cjs: "So is Windows on sda4 or sdb1? Please post the output of 
the following:"

---------------

[http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=250470&messageID=2557363](http://forums.cnet.com/5208-12546_102-0.html?forumID=133&threadID=250470&messageID=2557363)

"Hidden folders now showing (forgot to uncheck the "Hide protect
OS Files" - but I don't think I can delete any of these. Here's 
what I got: USER system file (0 bytes), protect.ed (106 KB), 
master.log (712 bytes), folder.htt (7.94 KB), desktop.ini (117 
bytes), bootmgr (428 KB), block.rin (9 bytes), automode (340 
bytes), then recovery files for Windows (224kb), Tools(128kb), 
Sources (204 mb),"

---------------------------

TeX: Post #26 of that thread laren@Matilda:~$ ls -l /mnt/sda4 

-rwxrwxrwx 1 root root        0 2008-08-12 07:50 AUTOEXEC.BAT
-rwxrwxrwx 1 root root      340 2005-09-12 01:18 AUTOMODE
-rwxrwxrwx 1 root root       14 2008-08-07 17:49 BLOCK.RIN
drwxrwxrwx 1 root root     4096 2007-11-15 03:50 boot
-rwxrwxrwx 1 root root      321 2008-12-02 11:58 boot.ini
-rwxrwxrwx 1 root root   438328 2006-10-04 09:02 bootmgr
-rwxrwxrwx 1 root root        0 2008-08-12 07:50 MSDOS.SYS
-rwxrwxrwx 1 root root    47564 2006-10-01 12:00 NTDETECT.COM
-rwxrwxrwx 1 root root   250032 2006-10-01 12:00 ntldr

-----
/mnt/sdb1:
total 5239288
drwxrwxrwx 1 root root 4096 2008-12-02 12:26 Documents and Settings
drwxrwxrwx 1 root root          0 2008-12-02 12:06 EXP_INST
-rwxrwxrwx 1 root root 3219574784 2008-12-02 23:39 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-12-02 22:57 Intel
-rwxrwxrwx 1 root root 2145386496 2008-12-02 23:39 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-12-02 23:40 Program Files

-----------------------------------------


------------------------------------------------

Originally Posted by causticburning 
"Sweet, XP booted up! What happened?"

caljohnsmith replied:
"Well, when you install Windows to a slave drive (and it looks 
like sdb could be configured that way), Windows insists on 
putting its boot files on the master drive in some primary 
NTFS/FAT partition; that's why your XP boot files ended up in 
sda4. So we just moved the boot files to sdb1, corrected 
boot.ini to use the correct drive, and then all is well in 
Windows Land again."

----------------------------------------------

I took a lot of time reading that first linked reference.
It did appear to me that XP had put its boot files on Vista.
The only problem is that he did a reinstall along the way.
Those odd files seem to come from HP Recovery.

----------------------------------------------------

[http://ubuntuforums.org/showthread.php?t=982933](http://ubuntuforums.org/showthread.php?t=982933)

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 4498745
-rwxrwxrwx 1 root root         24 2006-09-18 21:43 autoexec.bat
-rwxrwxrwx 2 root root         10 2006-09-18 21:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:00 Documents and Settings

[TeX: Indicates Vista, but it has no boot files.]

menu.lst:
title        Windows Vista/Longhorn (loader)
root        (hd1,0)

-----------------------------
caljohnsmith wrote:
"OK, I see better what is happening now; from your first post, 
your Vista partition is missing its necessary boot files, which 
means most likely they are on the other drive in the sdb1 
partition."

TeX: This example was less convincing. I already mentioned that
Vista copies installation files to an XP partition (I'm doubting
that XP does this). So Vista sd4, had no boot files and you thought
that sdb1 would likely have them, since it did boot. But I don't
think we ever found out that sdb1 was Vista and not XP. If it
was Vista, OP could have been booting Vista all along from sdb1,
Vista installed on sdb1.and never sd4. Now after you had OP repair
install Vista to sd4, it should have boot files. You had him post
the output of fdisk, and ls -l /mnt/sdb1, ls -l /mnt/sda4

/dev/sda4   *      63   153597464    76798701    7  HPFS/NTFS

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *      63   312576704   156288321    7  HPFS/NTFS
-----------------

knut@Knut-PC:~$ ls -l  /mnt/sdb1
total 621
drwxrwxrwx 1 root root   4096 2008-11-02 16:59 ACER
drwxrwxrwx 1 root root   4096 2008-05-09 21:20 ANALOGT FOTOGRAFI
drwxrwxrwx 1 root root   4096 2008-10-14 18:04 BILDER
drwxrwxrwx 1 root root   4096 2008-11-02 14:50 Boot
-rwxrwxrwx 1 root root 443912 2008-11-02 13:59 bootmgr
-rwxrwxrwx 1 root root   8192 2008-10-30 07:54 BOOTSECT.BAK

----------------------------

TeX: Since I see no remnant of XP boot files, this must have
been a Vista partition. So you are saying that when OP installed
Vista on sd4, that it copied its install files over to sdb1?
sd4 was a primary partition and could be booted from, but Vista
wanted its boot files on sdb1 also primary and bootable, because
it like being on the first partition, or what? sd4 was installed
after sdb1, so that means according to your explanation that it
had to be a primary partition, not logical, or Windows would've
balked at the installation because there was no alternate primary
partition to install the boot files to? And if you copy Vista boot
files to another Vista partition (drive) how do they both display
on the bootloader menu options? OP in that thread made no mention
of having two Windows booting systems available to him. Both sd4
and sdb1 are marked as primary and bootable and have boot files,
why don't or can't they both boot? I'm just not very sure that
this example illustrated your point, since the question is about 
XP. Your idea is that XP or Vista they both put their boot files 
on the master drive. I never noticed anything odd before with XP.

--------------------------

OK, onto current matters. Thanks for the information about how to
tell what is logical and what is primary. 

caljohnsmith wrote:
"So the bottom line is it is possible to install Windows to a 
logical partition (even on a slave drive), but only if you have 
a primary NTFS/FAT partition on the master drive where Windows 
can put its boot files; if no partition like that is available, 
Windows will refuse to install to a logical partition." 

Then you think pr1mal must have a Windows partition on first drive
sda, because he does have XP installed to a logical drive, and
sdb5 has no boot files. 

OP wrote;
title Windows XP1
root (hd0,X)
makeactive
chainloader +1

where x has been every number 1-6

TeX:  Shouldn't the root be (hd1,4) since its sdb5?
Anyway, it seems to me that pr1mal ought to know if he has any
Windows partition on sda. And that he could use My Computer to
see if there were any boot files on that partition and do a
copy and paste, though I think the script is cool too?

---

### Post by TeXtonyx on 2008-12-08
[http://neosmart.net/forums/showthread.php?t=1360](http://neosmart.net/forums/showthread.php?t=1360)
The Moderator wrote:
"Yes XP and all Windows partitions that you install Windows 
onto MUST be Primary. Only Linux can be installed to a logical 
partition as far as i know. But Windows must be Primary." 

If my belief is folklore, then it is a well-spread belief. [active?]
I think it might be possible by doing a backup/clone into a ^logical
partition of a system that was originally installed to a primary
partition. Then using grub might work. I googled for this and am
trying to get some confirmation of your idea from other sources.

Computer Guru said:
Actually, versions of Windows XP post-SP2 can be installed to logical 
partitions, but you might have some problems getting it there. 

But, for instance, you can change a primary partition to logical and 
still get the XP on it to boot if you update boot.ini as well. 

The only requirement is that all the bootloader files be on a Primary, 
Active NTFS or FAT32 partition." 

TeX: I mentioned changing the partition to logical from primary after
installation with a partition editor. But I don't think that is in
OP's box of tools yet, so I discounted it as a possibility.

"To install Windows NT to a logical partition, 
1 Decide which primary partition you want to have the Windows NT boot 
files located. 
2 Make that primary partition active using PartitionMagic, PQBoot or 
PQBoot32 from Windows 95/98/NT. 
3 Insert the Windows NT installation disk and reboot the computer. 
4 Proceed with the installation as normal."

OK, I believe this, and its called an installation, although it has
a couple of extra steps required, so it seems you are right. I just
wonder if the primary partition is already active with boot files,
how both partitions are still able to boot. I guess just make an
entry in boot.ini with the drive and partition number as usual, or
with Easybcd (or bcdedit) just add the newly installed partition
to the Vista data store. Which is already the advice given to pr1mal,
add the new partition with Easybcd. Or if there is a Windows primary
on sda, to that boot.ini or bcd. pr1mal should be reporting success any 
moment now. Though its going to need its own boot files like you have
suggested to work from Ubuntu I guess. (hd1,4) after boot files are
put there. So I'm onboard with your solution if Easybcd doesn't work.

---

### Post by caljohnsmith on 2008-12-08
> **TeXtonyx said:**
> 
So Vista sd4, had no boot files and you thought
that sdb1 would likely have them, since it did boot. But I don't
think we ever found out that sdb1 was Vista and not XP. If it
was Vista, OP could have been booting Vista all along from sdb1,
Vista installed on sdb1.and never sd4.
I think you might be getting a little mixed up about [Knut100's thread]("http://ubuntuforums.org/showthread.php?t=982933"), because he only had Vista, not XP, so I'm not sure why you mention XP in his case. Knut100 mentioned in his original post that after installing Vista, he booted just fine into Vista; but he wanted his Grub menu back. Note that I had him install Grub to the MBR of sda, and then he changed his BIOS so that he booted the sda drive and successfully got the Grub menu. But before I asked him to try doing a Vista Repair, I had him fix the Vista partition sda4 boot sector with the "bootrec /fixboot" command, and then he said Vista booted just fine from the Grub menu. But note that the Grub menu entry he was using for Vista used (hd1,0) (see his post #4), not (hd0,3), so that clearly shows he was booting Vista from sdb1, not sda4. That's also corroborated by the fact that Vista marked his sdb1 partition as bootable, while the sda4 partition was not.

> **TeXtonyx said:**
> 
TeX: Since I see no remnant of XP boot files, this must have
been a Vista partition. So you are saying that when OP installed
Vista on sd4, that it copied its install files over to sdb1?

Yes, that's exactly what happened in his case; even though sda4 is a primary partition, Vista put its boot files in sdb1, so that means sdb had to be the master drive. If sda was the master drive, Vista would have been just fine about installing only to sda4 and not touching any other partitions since sda4 is a primary partition. The bottom line is always that Windows will put its boot files in a primary NTFS/FAT partition on the master drive if you install Windows to a slave drive and/or a logical partition.
> **TeXtonyx said:**
> 
And if you copy Vista boot
files to another Vista partition (drive) how do they both display
on the bootloader menu options? OP in that thread made no mention
of having two Windows booting systems available to him. Both sd4
and sdb1 are marked as primary and bootable and have boot files,
why don't or can't they both boot? I'm just not very sure that
this example illustrated your point, since the question is about 
XP. Your idea is that XP or Vista they both put their boot files 
on the master drive. I never noticed anything odd before with XP.

sda4 did not originally have Vista's boot files, as he showed in his very first post; sdb1 contained all his Vista boot files as he showed in post #38. And again, XP had nothing to do with knut100's example, since he only had Vista. :)

> **TeXtonyx said:**
> OK, onto current matters...
Then you think pr1mal must have a Windows partition on first drive
sda, because he does have XP installed to a logical drive, and
sdb5 has no boot files. 

It's not clear yet whether sdb or sda is the master drive, so we don't know for sure that Windows XP would have put its boot files on sda. If sdb is the master drive (like knut100's case), then XP would have put its boot files in sdb1, which is a primary NTFS partition.

> **TeXtonyx said:**
> 
OP wrote;
title Windows XP1
root (hd0,X)
makeactive
chainloader +1

where x has been every number 1-6

TeX:  Shouldn't the root be (hd1,4) since its sdb5?
Anyway, it seems to me that pr1mal ought to know if he has any
Windows partition on sda. And that he could use My Computer to
see if there were any boot files on that partition and do a
copy and paste, though I think the script is cool too?
In his original post, pr1mal showed that Ubuntu is using "root (hd0,3)" in the Grub menu; that means if he can boot Ubuntu OK, then sdb must be the first boot drive or (hd0). And since Windows XP is on the same drive in sdb5, then Windows should be using (hd0,4) in the menu.lst, not (hd1,4), which would be the 2nd boot drive, 5th partition. Also, one of the big keys in helping him boot from a logical partition is to make sure he omits the "makeactive" line in his XP entry, because Grub cannot set a logical partition as active (i.e. set the boot flag). So his XP entry should be:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
But first we need to help him with his boot file problem. :)

**Pr1mal**, don't worry about finding your XP boot files, I've attached the three boot files you need to this post. Please download the "WinXP_boot_files.zip" to your Ubuntu desktop and do:
```
sudo mount /dev/sdb5 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
I modified the boot.ini file that's in the attached WinXP_boot_files.zip file so that it should be correctly configured for your sdb5 partition. Be sure to change your Grub menu to use the entry I give above for XP, reboot, and let me know exactly what happens when you try and boot XP from Grub. It might be we will have to do some work on the sdb5 boot sector, but maybe not. :)

---

### Post by TeXtonyx on 2008-12-08
"I think you might be getting a little mixed up about Knut100's 
thread, because he only had Vista, not XP, so I'm not sure why you 
mention XP in his case."

Because you couln't know wheter sdb1 was XP or Vista until post #38
TeX: "Since I see no remnant of XP boot files, this must have been 
a Vista partition." It was just commentary, that you came to this
conclusion before there was evidence.  

"bootrec /fixboot" yes in post #22 and #23 reported it worked.
But I'm wondering whether the fixboot could fix sdb1 since that
is where the boot files are. Because in #27 you tell him to boot
sd4 in grub and in #28 it fails "BOOTMGR is missing". So #31
says the sda4 Vista repair failed because of the usb stick. At
this point, why doesn't it look like Vista on sdb1 is booting.
After all it was installed before Vista on sda4? #34 EDIT: 
"Vista boots :S And Vista Startup Repair couldn't find anything"
TeX: I don't know what that means. And you wrote: #35 "Ummm, I 
don't understand--you say Vista boots now? While you have sdb1 
unhidden, how about posting:" 
TeX: Does it make sense if it is sdb1 booting Vista?
Well, in #38 it doesn't look like there is a Windows partition.
But sdb1 existed before sda4. So how did that sdb1 partition
get created? Formatted to ntfs, and with system volume and a
Recycle bin. That is not something you can do with Gparted, yes
a logical partition for ntfs data, but Gparted doesn't create
those other files. And if sdb1 were installed from a Windows cd,
you can't make a logical partition install of Windows, without
a pre-existing Windows installation. But not from a cd. 
So this example left me with too many questions, because for one
think, the OP was not very advanced to do something clever.

cjs wrote:
"so that clearly shows he was booting Vista from sdb1, not sda4."

Ok, I would agree with this even though I didn't see a C:\Windows
directory in #38. And that's fine about XP, but I don't think
that became clear till #38. But sda4 is now supposed to be fixed
and you already said sdb1 booted; you didn't answer my question:

"Both sd4 and sdb1 are marked as primary and bootable and have 
boot files, why don't or can't they both boot?"

TeX: I just didn't see anything in his posts that indicated he
had both Vistas on some boot menu and they both worked. But I
did see where you had him copy the files from sdb1 to sda4.
One of the reasons I mention XP, is that pr1mal has XP. And I
[So I was looking for an XP example to prove your point, not Vista.]
know that Vista has written its files to the XP partition in
the past. I could no longer find ntldr or boot.ini. I had to
reinstall or Repair XP to get them back. And then the next time
I boot Vista it overwrote them again. That is what I'm concerned
about, and we still don't know if there is Windows on his sda.

caljohnsmith wrote:
"If sdb is the master drive (like knut100's case), then XP would 
have put its boot files in sdb1, which is a primary NTFS 
partition."

But I thought pr1mal already reported no XP boot files, I think
he said on F: I thought he meant sdb1. Maybe not. 

I see that pr1mal has made a post with some reports. I haven't
read them yet. Reading knut100's progress reports has made me tired.

---

### Post by caljohnsmith on 2008-12-08
> **TeXtonyx said:**
> 
"Both sd4 and sdb1 are marked as primary and bootable and have 
boot files, why don't or can't they both boot?"
If you look in knut100's first post, you will see that sda4 is not marked as bootable; only sdb1 is. It wasn't until post #11 that I gave him directions for setting the boot flag on sda4. 
> **TeXtonyx said:**
> 
One of the reasons I mention XP, is that pr1mal has XP. And I
[So I was looking for an XP example to prove your point, not Vista.]
know that Vista has written its files to the XP partition in
the past. I could no longer find ntldr or boot.ini. I had to
reinstall or Repair XP to get them back. And then the next time
I boot Vista it overwrote them again. That is what I'm concerned
about, and we still don't know if there is Windows on his sda.

That's why I decided to post the Windows XP boot files for him in my last post. :)

---

### Post by TeXtonyx on 2008-12-09
Originally Posted by TeXtonyx  
"Both sd4 and sdb1 are marked as primary and bootable and have
boot files, why don't or can't they both boot?"

caljohnsmith replied:
"If you look in knut100's first post, you will see that sda4 is 
not marked as bootable; only sdb1 is. It wasn't until post #11 
that I gave him directions for setting the boot flag on sda4." 

TeX: The reason I'm asking about evidence that both OS's booted
at the completion of the troubleshooting, is that the proof is
in the pudding. I don't think he reported sdb1 booting after sda4.

For instance, here is a step that could possibly matter. cjs:
"OK, I think the easiest way is to "hide" your sdb1 partition so 
that Vista can't see it, and then simply do a "Vista Repair" from 
your Vista DVD; that should put Vista's boot files back in sda4.

After that reboot, and see if you can boot Vista from Grub. 
Once you are sure that works, you can go ahead and unhide 
your sdb1 partition so you can access it again: Post #27"

TeX: Now you might know that if the Windows OS are on two different
drives then unhiding is safe. I didn't know this could be an
issue when I wrote my first post, re esp. 'seeing both Win OS work'.

But after reading your pointers to booting Windows from a logical
partition, I found Herman's explanation.
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)  where Herman says,

"You use GRUB's 'hide' command to change your partition table 
so the new Windows won't recognize your previous, existing 
Window installation. The new installation will go in as per 
normal, and it will retain it's vital boot loader files.

Now when you want to boot your old Windows, you 'unhide' it, 
and 'hide' the new one. When you want to boot your new Windows, 
you 'hide' your old one, and 'unhide the new installation."

TeX: That makes me think pr1mal will have to take Herman's remark
into account since pr1mal has sdb1 and sdb5 on the same drive.

-----------------------------

More than one Windows on the same disk
title     Vista
hide      (hd1,4)
unhide    (hd1,0)
root      (hd1,0)
savedefault
makeactive
chainloader +1

title      Windows XP
unhide     (hd1,4)
hide       (hd1,0)
root       (hd1,4)
savedefault
makeactive
chainloader +1 

-----------------------------------------

Well, this might not be exactly right since you tried to explain
to me how hdb = hd0, but if so, hd1 can be changed to hd0.

Also I tried to look at File Type: gz  	WinXP_boot_files.gz 
which you said you made some changes to. I couldn't open it as
it seemed to large for boot.ini and a mix of code and text.
Maybe that's just me. But I could open a similar meierfra file 

[http://backports.ubuntuforums.com/showthread.php?t=813628](http://backports.ubuntuforums.com/showthread.php?t=813628) 
Archive.tar.gz

Maybe pr1mal thinks that too much chitchat went on and not enough
concentration on his problem, but maybe you didn't know that hide
and unhide had to be part of the grub menu.lst entries when there
were two Windows installations on the same drive. I didn't know
it at first either. So ultimately our discussion may have benefited
pr1mal especially in the case if the hide/unhide options are useful.

For others reading this thread, meierfra's explanation and links,
Herman's explanation and links (in meierfra -> Backports/(Archive)
and other explantions (esp. grub) by caljohnsmith are very informative.

---

### Post by caljohnsmith on 2008-12-09
> **TeXtonyx said:**
> 
Maybe pr1mal thinks that too much chitchat went on and not enough
concentration on his problem, but maybe you didn't know that hide
and unhide had to be part of the grub menu.lst entries when there
were two Windows installations on the same drive. I didn't know
it at first either. So ultimately our discussion may have benefited
pr1mal especially in the case if the hide/unhide options are useful.

For others reading this thread, meierfra's explanation and links,
Herman's explanation and links (in meierfra -> Backports/(Archive)
and other explantions (esp. grub) by caljohnsmith are very informative.
From the many times I've helped others boot Windows XP and Windows Vista from the same drive, I have found that hiding/unhiding the partitions in the menu.lst is not necessary once you have Vista and XP successfully installed (which makes sense I think). Hiding/unhiding can be useful for when you install Windows XP/Vista, and there is all ready another Windows installation on the same drive; if you hide the existing Windows partition before installing the other Windows, then it is easy to keep them separate. If you don't hide the currently installed Windows, then the newly installed Windows will often put its boot files in the current Windows' partition and take over the booting process for both Windows installations. But once you've installed both versions of Windows, you do not have to hide them from each other to keep them separate. Here is one example:

[http://ubuntuforums.org/showthread.php?t=932727](http://ubuntuforums.org/showthread.php?t=932727)

Note in my last post to that thread, I helped Houchy unhide both his Vista and XP partitions and also remove the hide/unhide lines in his menu.lst; in his last post he said "it worked like a charm", so obviously it worked. If you want more examples, feel free to search the threads I've responded to and you'll find more. If you still have doubts, you could ask meierfra if he thinks it is necessary to use the hide/unhide lines in the menu.lst on a permanent basis for both Windows entries in order to use Vista/XP on the same drive, and I think he will tell you it isn't necessary. 

P.S. Thanks for letting me know about the problem with the Windows files that I attached; somehow I messed up zipping them together, so I corrected it and reattached the zipped file. Let me know if you still have problems with it, but I think it might be a moot point now as Pr1mal hasn't responded in a few days. :)

---

### Post by TeXtonyx on 2008-12-09
caljohnsmith wrote;
"But once you've installed both versions of Windows, you do not 
have to hide them from each other to keep them separate. Here is 
one example:

[http://ubuntuforums.org/showthread.php?t=932727](http://ubuntuforums.org/showthread.php?t=932727) "

TeX: I thought that was a splendid example, even including how he
installed XP into a logical partition in the first place. I see
that you are right. Do you know why hda1 is marked active, * ,
under Boot, but in next section, sda1 was not marked active, * ?


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5028    40382460   17  Hidden HPFS/NTFS
/dev/hda2            5029        9963    39640387+   f  W95 Ext'd (LBA)
/dev/hda5            5029        7578    20482843+   7  HPFS/NTFS

---------

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31871   256003776    7  HPFS/NTFS
/dev/sda3           58252       60801    20482875    5  Extended

------------------

Herman, I think, mentioned using Gparted to mark the logical
parition active. This seems to be an advantage of grub; when 
Vista is in control, it can boot XP. But when XP is in control
of the boot menu/bootloader, I don't know a way to have XP boot
Vista, I resort to doing it indirectly through grub. And neither
Windows can boot the other, if the other is on a logical partition,
which gives advantage to grub. This hiding of partitions reminds
me of unplugging a drive cable for installs involving two drives.

Oh, your new file for Windows booting works fine. Somebody else 
might want it in the future, and it's good to apply the finishing touch. :-)

---

### Post by caljohnsmith on 2008-12-09
> **TeXtonyx said:**
> 
[http://ubuntuforums.org/showthread.php?t=932727](http://ubuntuforums.org/showthread.php?t=932727) "

TeX: I thought that was a splendid example, even including how he
installed XP into a logical partition in the first place. I see
that you are right. Do you know why hda1 is marked active, * ,
under Boot, but in next section, sda1 was not marked active, * ?


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5028    40382460   17  Hidden HPFS/NTFS
/dev/hda2            5029        9963    39640387+   f  W95 Ext'd (LBA)
/dev/hda5            5029        7578    20482843+   7  HPFS/NTFS

---------

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31871   256003776    7  HPFS/NTFS
/dev/sda3           58252       60801    20482875    5  Extended


When you install Windows, Windows is careful to mark its boot partition as bootable so that a Windows MBR can boot it; and since Vista was installed to hda1, that is why Vista set the boot flag on that partition. sda1 was merely his "partage" folder (that's french), which means "sharing" in english, so I assume that's just a partition for his personal files; therefore Windows wouldn't mark sda1 as bootable. :)

---

### Post by pr1mal on 2008-12-09
Wow thanks for all the help.  This si much more than expected.  I will try and claify a few things before i say what im going to do about this problem.

Even though my harddrive is being reported at sdbX, it is the only hard drive on my laptop.  There is no sda to worry about, there are no other harddrives to boot from, and all mention of "(hd1,X)" should not be relavent.  It shows up as sdbX in gparted because i am working on this all from my desktop, but when it is in my laptop, it is the only HDD.  All the partition numbers should stay the same though.

You where right in stating that Vista moved XPs boot files( or maybe XP moved them itsself when it realized it was on a logical partition) to another primary partition.  I found all three associated boot files on my vista partition, and they dont belong there.  

I moved the files back to XP so now it should be good to boot, and i currently have it set up so that Grub can load linux or vista, and when vista loads it pops up another boot manager that lets me start Vista or XP.  this works

I can start Vista, or i can start XP,   The downfall is XP fails shirtly after.  I get the mesage  
C:\WINDOWS\system32\hal.dll is missing or corrupt

this means it is seeing windows XP though and that means that this forum has succeded.

As for me personally, i am going to start over on a clean slate.  Im reformating so XP is on a primary partition in hopes  everything works easier.
thank you much

---

### Post by caljohnsmith on 2008-12-09
> **pr1mal said:**
> 
I can start Vista, or i can start XP,   The downfall is XP fails shirtly after.  I get the mesage  
C:\WINDOWS\system32\hal.dll is missing or corrupt

this means it is seeing windows XP though and that means that this forum has succeded.

As for me personally, i am going to start over on a clean slate.  Im reformating so XP is on a primary partition in hopes  everything works easier.
thank you much
That missing "hal.dll" is most likely a result of your boot.ini file being misconfigured for the wrong partition, and thus Windows thinks that file is missing when it really isn't; that's a common problem in a situation like yours. If you are willing to download the boot files I provided and use that boot.ini file instead of your current boot.ini, I think you can get your Windows XP booting just fine. It's up to you though if you instead want to reformat.

---

### Post by TeXtonyx on 2008-12-10
> **caljohnsmith said:**
> That missing "hal.dll" is most likely a result of your boot.ini file being misconfigured for the wrong partition, and thus Windows thinks that file is missing when it really isn't; that's a common problem in a situation like yours. If you are willing to download the boot files I provided and use that boot.ini file instead of your current boot.ini, I think you can get your Windows XP booting just fine. It's up to you though if you instead want to reformat.

Actually this post is to pr1ma1 also. Since you pr1ma1 already have 
the ntdetect and ntldr in the XP partition (still there I hope) the 
new boot.ini file is now the key file which you could copy and paste 
or just hand edit after unhiding and changing from read only permission.
Or replace your current boot.ini file with caljohnsmith's boot.ini file.

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn

caljohnsmith thinks your boot.ini is using the wrong partition 
number. He thinks it should be 3. (1)sdb1, (2)sdb3, (3)sdb5, = 3)

On this computer XP is installed to the first partition:

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" 

This is an easy thing to try before you reinstall. I'm not sure how he 
figured out that the correct partition number entry was 3, here's a link
which explains how he did it:  [http://www.terabyteunlimited.com/kb/article.php?id=159](http://www.terabyteunlimited.com/kb/article.php?id=159)

[http://www.terabyteunlimited.com/downloads-free-software.htm](http://www.terabyteunlimited.com/downloads-free-software.htm)
"EditBINI Version 1.01.1 Updated 12/09/2002 (Click here for FTP Download)
This utility will allow you to edit \BOOT.INI in an NTFS partition from 
DOS or Win9x.

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)
UBCD has EditBini, Super Grub Disk, and TestDisk on it among many others.


The Super Grub Disk will let you boot Linux or Windows if
the boot files are there. It displays the drive and partition
used, so you can make a note of that. Also lets you see that
everything else is working (the boot files/first sector) if and
when it boots. The amended boot.ini idea is quick and caljohnsmith
has convinced me that a logical partition is not a huge barrier.

Finally, there was some discussion about hiding/unhiding Vista and XP.

"If you've been booting XP on a system where it can see Vista, then 
you've got no Vista recovery points. XP thinks Vista recovery folders 
are corrupt (they're a new format) and resets them to be XP folders." 
So apparently it would be best to hide Vista from XP, or take a risk.

[http://windowssecrets.com/2008/02/21/02-Dual-booting-XP-deletes-Vista-restore-points](http://windowssecrets.com/2008/02/21/02-Dual-booting-XP-deletes-Vista-restore-points)

"But booting to XP on a dual-boot system has the negative 
side-effect of deleting any Vista restore points, in addition 
to all but its latest backup file, and a Registry workaround 
is required to prevent this.

Unfortunately, the are not limited to system restore points. If 
you boot into Windows XP after using Vista's so-called Complete PC 
Backup feature, XP deletes all but the most recent backup file. 

Although there is no perfect solution, Microsoft recommends two 
different workarounds. Both of the techniques involve preventing 
XP from accessing the Vista partition. This means you won't be 
able to use your Vista hard drive when you've booted into XP. 
However, when you boot into Vista, you will be able to access 
all your drives, including the partition holding Windows XP. For 
details on the two workarounds, see Knowledge Base article 926185."

-----------------------

[http://support.microsoft.com/kb/926185](http://support.microsoft.com/kb/926185)
Method 1
To keep Windows XP from deleting restore points of the volume 
in Windows Vista, add the following registry entry under the 
HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices\Offline registry subkey
in Windows XP:

Value name: \DosDevices\D:
Type: REG_DWORD
Value data: 1

Note If the HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices\Offline 
registry subkey does not exist, you must manually create this 
registry subkey. Create this registry entry when you have 
installed Windows Vista on the "D" partition in Windows XP." 

TeX: Method 2 (Bitlocker) only works for Vista Ultimate or Enterprise. 
Easybcd, a free GUI, is much easier than bcdedit. I think this System 
Restore problem applies to having both Windows OS on one drive, not two.

[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Tips on how to share same profile is using Firefox and Thunderbird
on both Windows and Ubuntu.

---

### Post by SageInBlack on 2008-12-18
Hi, This will be my first post on the ubuntu forums.... so I still need quite a bit of help understanding thing...

I have been reading this post to try getting all three system (XP,Vista,and Ubuntu) from one grub screen... (and I want to hide Vista and XP from each other)

Before the Ideas however: Question (after reading the discussions that has happened)

1. Is it that vista always steals the bootloader files of earlier versions of windows and puts it into vista's drive?

[CENTER]OR[/CENTER]

Does it, by default, just stuffs the Vista bootloader files in the first drive?

2. If I kept the two systems hidden from each other, there would be no chance that one system would steal the bootloader files form the other right?



Back to my Idea and Procedure

From reading through the discussion.. I have sort of formulated these steps to get my computer to do what was stated above..

My Configuration:

I have only one hard disk...
hd(0,0): Vista
hd(0,1): XP
rest is Ubuntu and swap...

Right now it's first grub then Vista bootloader (which boots to vista and xp)


OK this is how I am thinking it will work for me

The General procedure and concept:

1. Look for the bootloader files
2. Put them back in to their original OS's folder 
3. Configuring Bootloader file (XP,Vista, and Ubuntu)

Specific Steps:
(My guess I will need to boot into Ubuntu and it all has to be done on one go?)

1.Look for the bootloader files (XP in my case)
```
boot.ini
ntldr
NTDETECT.COM
```

2. Putting the bootloader file back into their respective OS'es
[INDENT]I just put the three file i found back into XP's boot area, right? (i plan to copy them just in case)[/INDENT]

3. Configure the bootloader files
[INDENT]Grub:Configure the grub entries so that it boots form the XP partition and Vista partition seperately (and hide them from each other)[/INDENT]
[INDENT]Windows XP: Edit the partition number so that it boots form XP's drive after Vista it's hidden (so I would boot to partition 1, since it was originally 2)[/INDENT]
[INDENT]Vista: Fire up EasyBCD and delete the entry relevant to XP[/INDENT]

Have I missed anything at all?? (in terms of Windows registry fix and others)

I am just here to ask if my procedure is all right, I have not tried it, since I want to have a green light from the experts.

Thanks in advance!~
SIB

---

### Post by caljohnsmith on 2008-12-18
> **SageInBlack said:**
> 
1. Is it that vista always steals the bootloader files of earlier versions of windows and puts it into vista's drive?

[CENTER]OR[/CENTER]

Does it, by default, just stuffs the Vista bootloader files in the first drive?

In my experience, Vista doesn't actually "steal" XP's boot files and put them on Vista's drive; what usually happens is Vista merely installs its boot files to the XP boot partition (whichever primary partition has XP's boot files), rewrites the XP partition boot sector to boot "bootmgr" instead of "ntldr", and then Vista takes over the booting process for both OSes. And since XP always puts its boot files in a primary partition on the master drive, then that's also where Vista's boot files will end up.
> **SageInBlack said:**
> 
2. If I kept the two systems hidden from each other, there would be no chance that one system would steal the bootloader files form the other right?

Again, in my experience, it is only necessary to "hide" XP and Vista from each other when you are installing them if you want to keep them separate (i.e. keep their boot files separate); once you have them successfully installed and their boot files are in their own respective partitions, you can then safely unhide them from each other and they won't "steal" each others boot files. 

Before you go about moving your boot files around and reconfiguring, how about first opening a terminal (Applications > Accessories > Terminal) and do:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash ./boot_info.txt
```
That will create a "BootInfo.txt" file on your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot Vista and XP separately from Grub.

---

### Post by SageInBlack on 2008-12-18
Here is the output

OUTPUT STARTS HERE
[Code code comments that things I found intresting]



Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for its boot files.
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63
    Operating System: Vista
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM /boot

sda2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 73402368
    Operating System: XP
    Boot files/directories present: 

sda3:
    File system:  Extended Partition

sda5:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda6:
    File system:  swap

```
From this I can see that the XP boot files are in Vista's disk, which is the first disk of the HDD... Vista came before XP because my lap had vista pre-loaded with out a "proper" Vista install disk, a minor hassle to wrestle to get XP dual boot
Also, now looking back, is it that most Window's Boot Loader just puts the bootloader files on the first physical Partition they could write on?
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e4523d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    73401014    36700476    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        73402368   230795255    78696444   17  Hidden HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       230805855   312576704    40885425    5  Extended
/dev/sda5       230805918   309138794    39166438+  83  Linux
/dev/sda6       309138858   312576704     1718923+  82  Linux swap / Solaris
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 73400952, Id= 7, bootable
/dev/sda2 : start= 73402368, size=157392888, Id=17
/dev/sda3 : start=230805855, size= 81770850, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=230805918, size= 78332877, Id=83
/dev/sda6 : start=309138858, size=  3437847, Id=82

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


sda1/boot

total 1024
drwxrwxrwx 1 root root   4096 2008-05-23 06:56 .
drwxrwxrwx 1 root root   8192 2008-12-18 06:41 ..
-rwxrwxrwx 1 root root  28672 2008-12-18 06:41 bcd
-rwxrwxrwx 1 root root 262144 2008-12-18 06:41 BCD.LOG
-rwxrwxrwx 2 root root 262144 2008-05-23 05:55 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-02-08 02:51 BCD.LOG2
-rwxrwxrwx 1 root root   1024 2008-01-03 04:54 bootfix.bin
-rwxrwxrwx 1 root root  65536 2008-02-08 02:51 bootstat.dat
drwxrwxrwx 1 root root      0 2008-02-08 02:51 cs-CZ
drwxrwxrwx 1 root root      0 2008-02-08 02:51 da-DK
drwxrwxrwx 1 root root      0 2008-02-08 02:51 de-DE
drwxrwxrwx 1 root root      0 2008-02-08 02:51 el-GR
drwxrwxrwx 1 root root      0 2008-02-08 02:51 en-US
drwxrwxrwx 1 root root      0 2008-02-08 02:51 es-ES
-rwxrwxrwx 1 root root   2048 2008-01-04 21:23 etfsboot.com
drwxrwxrwx 1 root root      0 2008-02-08 02:51 fi-FI
drwxrwxrwx 1 root root      0 2008-02-08 02:51 fonts
drwxrwxrwx 1 root root      0 2008-02-08 02:51 fr-FR
drwxrwxrwx 1 root root      0 2008-02-08 02:51 hu-HU
drwxrwxrwx 1 root root      0 2008-02-08 02:51 it-IT
drwxrwxrwx 1 root root      0 2008-02-08 02:51 ja-JP
drwxrwxrwx 1 root root      0 2008-02-08 02:51 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-20 20:48 memtest.exe
drwxrwxrwx 1 root root      0 2008-02-08 02:51 nb-NO
drwxrwxrwx 1 root root      0 2008-02-08 02:51 nl-NL
drwxrwxrwx 1 root root      0 2008-02-08 02:51 pl-PL
drwxrwxrwx 1 root root      0 2008-02-08 02:51 pt-BR
drwxrwxrwx 1 root root      0 2008-02-08 02:51 pt-PT
drwxrwxrwx 1 root root      0 2008-02-08 02:51 ru-RU
drwxrwxrwx 1 root root      0 2008-02-08 02:51 sv-SE
drwxrwxrwx 1 root root      0 2008-02-08 02:51 tr-TR
drwxrwxrwx 1 root root      0 2008-02-08 02:51 zh-CN
drwxrwxrwx 1 root root      0 2008-02-08 02:51 zh-HK
drwxrwxrwx 1 root root      0 2008-02-08 02:51 zh-TW

sda5/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=6e0e0971-8e9e-49dd-9583-754334c8de2e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6e0e0971-8e9e-49dd-9583-754334c8de2e

## should update-grub create alternative automagic boot options
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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		6e0e0971-8e9e-49dd-9583-754334c8de2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6e0e0971-8e9e-49dd-9583-754334c8de2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		6e0e0971-8e9e-49dd-9583-754334c8de2e
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=6e0e0971-8e9e-49dd-9583-754334c8de2e ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		6e0e0971-8e9e-49dd-9583-754334c8de2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6e0e0971-8e9e-49dd-9583-754334c8de2e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		6e0e0971-8e9e-49dd-9583-754334c8de2e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=6e0e0971-8e9e-49dd-9583-754334c8de2e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		6e0e0971-8e9e-49dd-9583-754334c8de2e
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
unhide		(hd0,0)
hide		(hd0,1)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


sda5/boot

total 25520
drwxr-xr-x  3 root root    4096 2008-12-17 10:27 .
drwxr-xr-x 21 root root    4096 2008-12-03 11:03 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-18 02:23 grub
-rw-r--r--  1 root root 8667100 2008-12-03 05:45 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8668250 2008-12-17 10:27 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sda5/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-18 02:23 .
drwxr-xr-x 3 root root   4096 2008-12-17 10:27 ..
-rw-r--r-- 1 root root    197 2008-12-02 23:20 default
-rw-r--r-- 1 root root     15 2008-12-02 23:20 device.map
-rw-r--r-- 1 root root   8108 2008-12-02 23:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-02 23:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-02 23:20 installed-version
-rw-r--r-- 1 root root   8712 2008-12-02 23:20 jfs_stage1_5
-rw-r--r-- 1 root root   5131 2008-12-18 02:23 menu.lst
-rw-r--r-- 1 root root   5101 2008-12-03 05:46 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-02 23:20 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-02 23:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-02 23:20 stage1
-rw-r--r-- 1 root root 121460 2008-12-02 23:20 stage2
-rw-r--r-- 1 root root   9556 2008-12-02 23:20 xfs_stage1_5

StdErr Messages 

```
I have an USB drive that seems to be turned on all the time
```
Unknown MBR on /dev/sdb


ls: cannot access /dev/hd?: No such file or directory
xxd: /dev/sdb: No medium found
hexdump: /dev/sdb: No medium found
/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
ls: cannot access /dev/hd??*: No such file or directory
/dev/sda3: unknown volume type

---

### Post by caljohnsmith on 2008-12-18
OK, first thing to do would be to unhide the Windows XP partition:
```
sudo grub
grub> unhide (hd0,1)
grub> quit
```
Do you have your Windows XP Install CD? You'll either need that or a Vista Install CD to repair your Windows XP boot sector. If you can boot your Windows XP Install CD, go to the "recovery console", and do:
```
map
```
That will list the drive letters of your partitions, so pick the one that is XP (probably the D drive), and do:
```
fixboot D:
```
Or replace D if the drive letter for XP is different. Next, to move your XP boot files back to the XP partition do:
```
sudo mkdir /mnt/sda1 /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
sudo mv /mnt/sda1/boot.ini /mnt/sda1/ntldr /mnt/sda1/NTDETECT.COM /mnt/sda2
```
Also, it looks like your boot.ini file is all ready configured for the correct partition as we expect, so no need to change it. Next open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Vista entry at the bottom with the following two entries:
```
title Windows Vista
root (hd0,0)
chainloader +1

title Windows XP
root (hd0,1)
chainloader +1
```
Next reboot, and try booting Vista and XP from the Grub menu. Let me know exactly what happens and we can work from there.

---

### Post by SageInBlack on 2008-12-19
At first it didn't work, but now it works since I added the savedefault and makeactive like the entries that Ubuntu automatically generates

Both operating systems boot from their separate entry

but they can still see each other's drives

so it's just the matter of adding the hide / unhide entry to grub

I also easyBCD'ed the Vista's boot entry so that it won't show XP

Thank you!
SIB

P.S. It would be nice if this can be compiled to a guide

---

### Post by caljohnsmith on 2008-12-19
Adding "default" and "makeactive" should not affect whether Windows can boot from Grub, so I would be surprised whether that was really the cause of the problems. Now that everything is for sure working, can you try removing them just to see if it works? I would really like to know if for some reason that makes a difference in the case of your setup.

About hiding/unhiding XP and Vista, is there some reason why you want to keep them hidden from each other now that you can successfully boot them separately? If you want to hide them from each other, then you can put the hide/unhide lines back in your Grub menu.lst if you want like you mentioned.

---

### Post by Jammanuser on 2008-12-26
> **caljohnsmith said:**
> [COLOR="Red"]That missing "hal.dll" is most likely a result of your boot.ini file being misconfigured for the wrong partition,[/COLOR] and thus Windows thinks that file is missing when it really isn't; that's a common problem in a situation like yours. If you are willing to download the boot files I provided and use that boot.ini file instead of your current boot.ini, I think you can get your Windows XP booting just fine. It's up to you though if you instead want to reformat.

Thanks for the info, Caljohnsmith! :) Looking back over a thread of mine just a few minutes ago, I came across this thread, and noticed your post, which aroused my interest, since I too have had a hal.dll error recently...but I just wanted to mention that I solved mine by replacing the "ntldr" file on XP, which seemed to be the root of that problem. SO in my case, it **wasn't ** the partition numbers in boot.ini that was the fault and cause of the hal.dll error. It was due, I believe, to a corrupt "ntldr" file. ;)

Cheers! :popcorn:

-Jam man

:guitar:

P.S. in case you haven't been keeping track of my posts in the tri-booting problem that I posted in the "General Help" section of this site, I have now succeeded at tri-booting, using BootIT NG! :guitar: Cheers! :)

---

### Post by TeXtonyx on 2008-12-26
> **caljohnsmith said:**
> Adding "default" and "makeactive" should not affect whether Windows can boot from Grub, so I would be surprised whether that was really the cause of the problems. Now that everything is for sure working, can you try removing them just to see if it works? I would really like to know if for some reason that makes a difference in the case of your setup.

About hiding/unhiding XP and Vista, is there some reason why you want to keep them hidden from each other now that you can successfully boot them separately? If you want to hide them from each other, then you can put the hide/unhide lines back in your Grub menu.lst if you want like you mentioned.

I think it's a well reported error that if XP can see the 
Vista partition, then XP will overwrite all but the last
System Restore for Vista. SageInBlack has been booting both
OS for awhile, so he can check in Vista's System Restore, which
is usually show as a light blue calendar, with the restore
dates highlighted in darker blue. If Vista has only one restore
point *blued*, then tis XP that doeth the dastardly deed. 

If not then maybe the Easybcd hide switch is fixing the problem,
or there just isn't any problem.

---

### Post by SageInBlack on 2009-01-09
Well I like to keep the two seperate as a form of containment, so virus don't spread the system... And they just need to feel diffrent (i tend to play around with my OS a lot)

Unfortunately... the first thing I do after I install windows is to disable system restore, because if there was a virus on my windows, I just don't think that system restore would cut it, it also cuts back space usage... so I still do my daily back up's :)

---

