---
title: "Tri-boot (Vista, XP, Wubi Ubuntu 8.10) problem"
date: 2008-12-18
forum: General Help
---

### Post by Jammanuser on 2008-12-18
Hello all. I am trying to enable tri-booting on my laptop computer with Win Vista, XP, and Ubuntu 8.10...but so far i have had no success! I am also getting support for this problem on the EasyBCD forums as well, but so far have still not got the problem fixed! :(

I am using the BootIT NG partitioning program, and so far I am unable to boot into either XP or Ubuntu...well **technically** i can boot into Ubuntu, only i have to use the Super Grub disk, as the Grub bootloader can apparently not run side by side with BootIt NG at the same time. The Grub bootloader is still there, only i can not access it (apparently it got deactivated somehow by BootIT NG...). BootIT NG boots at startup, and I go the "Default boot menu" and can boot fine into Vista, but can not boot into either XP or Ubuntu via the Vista bootloader. 

I've already added the appropriate boot entries with EasyBCD to the Vista bootloader...but they don't work. I get errors trying to boot into either one. In the case of XP, it is an error meaning that the "boot.ini" file partition values r not correct, which they are (but lets not go in that now...). In the case with Ubuntu, i get the following error when trying to boot into it via the Vista bootloader:

```
BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant http://www.winimage.com/bootpart.htm

Loading new partition

Bootsector from C.H. Hochst&#8222;tter

 Cannot load from harddisk.

Insert Systemdisk and press any key.
```

I selected the correct drive to boot from, using EasyBCD, i.e. the 20 GB partition that Ubuntu is installed on, however that is the message that i get, and that is also what it says in the C:/NST/nst_grub-B25D880C661ADB3AD9BCBECFE78693DC file. I assume that I need to somehow edit that file to point to the correct partition...however, i have literally **no idea** how to go about doing this! :confused:

Any help would be much appreciated...

Thanks in advance! ):P

Jam man

:guitar:

---

### Post by sPiN1 on 2008-12-18
sorry for spam but, why would you triboot? i would suggest sticking with dualbooting over tribooting if you're wanting to use linux and windows, sorry i can't help you! hoepfully someone can get this straightened out for you.

---

### Post by Jammanuser on 2008-12-18
> **sPiN1 said:**
> sorry for spam but, why would you triboot? i would suggest sticking with dualbooting over tribooting if you're wanting to use linux and windows, sorry i can't help you! hoepfully someone can get this straightened out for you.

Because i want all **3** OSes...Vista, XP, **and** Ubuntu 8.10! :D

Cheers! :lolflag:

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
Here's a copy of what my boot.ini (that i copied over from XP) says:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

```

---

### Post by Jammanuser on 2008-12-18
How would i reactivate Grub?

Looking forward to any and all replies...):P

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
I don't want it to go to the MBR however... ^

I want it to be on the Ubuntu partition...either the primary one or the swap that i'm using.

BTW, the Ubuntu install is actually a transfer of my **Wubi** install...this was accomplished using LVPM.

Would appreciate any and all replies. ):P

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
hmm...it seems like my thread keeps getting bumped down every second the silence continues... :(

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> Do you have a genuine Vista install cd? 

Yes, i do. Thanks for the reply.

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> Boot the Ubuntu live cd, and open a terminal, and type
sudo fdisk -l (small letter L) and then press the <enter> key
which will list your installed OS and partitions for later use.
Usually you should copy and paste that report on this forum.

Ok, i will run that command and post its output, even though i have already done that before, and have its output...however, since i have made changes since, i guess it would probably be a better idea (rather than copy and paste the output of "sudo fdisk -l" that i already have), to do it again, and paste the fresh info.

Cheers! :guitar:
> 
Then from the terminal type
sudo grub
grub>find /boot/grub/stage1 Use this information for next step,
grub>root (hd0,x) x equals the number obtained by the find command
[COLOR="Red"]grub>setup (hd0,x) grub is installed to the /boot partition not MBR[/COLOR]
grub>quit


I was of the understanding that the command in red installs Grub to the MBR...are you **absolutely** certain that it installs to the boot sector of the partition, and not to the MBR? Like i mentioned above, i do not want it installed to the MBR, as this will overwrite my Vista bootloader, and i don't want that. In addition, if it doesn't, then why have the commands right after that (using the Vista CD) to rebuild the BCD? i'm not completely computer illiterate...;)

Cheers! :cool:

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> 
When you boot with Bootit choose to uninstall Bootit.

Thanks, but i would rather keep BootIT NG, if you don't mind, and figure out some way to get the Ubuntu entry (created by EasyBCD) to chainload into the Grub bootloader (already installed)...:guitar:

Cheers! ):P

Jam man

:popcorn:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> Take the cd out. When you reboot you should boot into Vista. Now 
uninstall Easybcd and reinstall it. [COLOR="Red"]The next error comes from resizing.[/COLOR]
BootPart 2.60 Bootsector 
Loading new partition
 Cannot load from harddisk.
Insert Systemdisk and press any key.

hmm...so you say the error comes from **resizing**? resizing what, if you don't me asking...? Are you talking about the partition that Ubuntu is on? I have not resized the Ubuntu partition, after transferring my Wubi install to it, via LVPM...
> **TeXtonyx said:**
> 
I want to be sure your Easybcd settings are purged.

hmm...I think i need to post a screenshot of my EasyBCD window, to clear things up a bit...
> **TeXtonyx said:**
> 
Your boot.ini may have the wrong partition number. Mine says,
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT
c:\UbuntuB.bin="Ubuntu"


The actual partition number (counting from top to bottom in the BootIT NG "Partition work" window) of my XP install is #6...but i've already tried that number in "boot.ini" but i got the error message meaning that the ARC paths in the [operating systems] or the default entry in boot.ini is incorrect:

```
"Windows could not start because the following file is missing or corrupt:

<Windows root>\system32\ntoskrnl.exe.

Please re-install a copy of the above file" 

```

Anyway, i'd rather concentrate right now on getting Ubuntu booted from the Vista bootloader, via EasyBCD...;)

Cheers! :cool:

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> [COLOR="Red"]If Vista is installed on (hd0,0) first drive first partition = sda1[/COLOR]
Then XP may be on (hd0,1) first drive second partition = sda2
which means you need to change the partition number from 1 to 2
multi(0)disk(0)rdisk(0)partition(1)-> multi(0)disk(0)rdisk(0)partition(2)
Edit both places that there is a "partition" entry in boot.ini

boot.ini is often hidden so you need to unhide it and change
the property from read only to write. You can use Editbini 
which I think is on the Bootit cd. I use Notepad to edit boot.ini

It is also possible to do the booting with just grub for each OS
but will take some more work. The Super Grub Disk is good for
booting individual OS in case the others fail and own the MBR.

If there is a problem with grub, and/or the menu.lst settings,
the UUID can be replaced with blkid, but that is for another day.

Unfortunately, Vista is installed on my first drive, **third** partition. No doubt that changes things a bit...:guitar:

Cheers! :lolflag:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> Your boot.ini may have the wrong partition number. Mine says,
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
[COLOR="Red"]/NOEXECUTE=OPTIN /FASTDETECT
c:\UbuntuB.bin="Ubuntu"

[/COLOR]
hmm...it looks to me from what i highlighted in red, as if u somehow configured the **boot.ini ** file to boot Ubuntu, as well as XP...;)

Is that the truth, or is the last two lines for something else?

Looking forward to your reply...):P

Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> 
The command to put grub in the MBR for first drive is
setup (hd0) or
setup (hd1) if you had a second drive

(hdx,y)the first entry x is the hard drive and the second entry y 
is the partition number: (hd0,0) first drive first, first partition
The grub manual is available online if you would like to check it.

Alright...i get it now! Thanks! :guitar: not much difference though, in terms of characters (e.g. letters and numbers), but apparently it makes a lot of difference installing Grub...

Cheers! :popcorn:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> When I had Bootit installed it was to dual boot XP and Windows and 
I think it was used to hide/unhide partitions. XP will overwrite
Vista's System Restores unless you have Vista Ultimate which has
Bitlocker enabled, or you can make a registry fix to XP that will
let Vista read XP but not XP read Vista as workarounds.

[COLOR="Red"]How do you use Bootit, what work does it do?[/COLOR]

I am using it for all my partition work (i.e. creating, deleting, resizing, moving around, etc. partitions). And of course i also used it to hide/unhide the Vista partition, and to set the XP partition as active, when installing XP...:guitar:

Cheers! :popcorn:

EDIT: and what exactly did u mean by XP overwriting Vista's system restores? i'm asking because that just rang a warning bell for me, because i did both a System Restore for XP and a System Restore for Vista, after installing XP...due to problems i had!

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> 
The first line is part of the line before that didn't wrap around

The second line boots Ubuntu. T[COLOR="Red"]he Bootpart 2.60 error message
that you posted and I referenced is part of the Easybcd engine.
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)    	 bootpa26.zip
If you download that, unzip bootpart.exe to C:\ the output->[/COLOR]


Ahh...that is what i kind of figured. :-k The thought of EasyBCD having to depend on Bootpart to boot Ubuntu occurred to me, u see...unfortunately, though, i've already researched it (and visited the link u just gave), and i learned that that program can only be installed on Fat partitions. That is impossible in my case, because the Vista partition is NTFS...:-(

If only there was a way to boot Ubuntu using EasyBCD without using Bootpart...

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> 
The second line boots Ubuntu.

So what you are simply saying then is that you did indeed configure boot.ini to boot Ubuntu, using that line? hmm...i wonder if it would be possible in my case? of does boot.ini depend on Bootpart as well? :-k

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> "Unfortunately, Vista is installed on my first drive, third partition. No doubt that changes things a bit"

[COLOR="Red"]Well, more importantly an annotated fdisk report of which
OS matches which ntfs is useful for checking the boot.ini
choice of partition number.[/COLOR] Those partition numbers just
count Windows partitions and go by primary first, logical next.

Right...i'll go do that right away, and post the output in a few minutes... :guitar:

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
Ok...so here's the output for "sudo fdisk -l" as promised:

```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x3c5a8d58 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           5       40131    6  FAT16 
/dev/sda2           34664       38487    30716280    c  W95 FAT32 (LBA) 
/dev/sda3   *        1280       31541   243072920    7  HPFS/NTFS 
/dev/sda4           31542       34090    20474842+  83  Linux 

Partition table entries are not in disk order 
ubuntu@ubuntu:~$ 
```

Hopefully this will help...

Note that the Fat 32 partition shown was only there currently because I placed XP back in the MBR before booting into the Live session. Every single time (after I put XP in the MBR) I boot into Vista, the MBR reverts back to its original state, and XP gets thrown out of the MBR. I'm not sure what causes this, only i know that it is consistent every time i boot into Vista...

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1005062&page=4&highlight=pr1ma1](http://ubuntuforums.org/showthread.php?t=1005062&page=4&highlight=pr1ma1)[/COLOR]

I post a longer explanation and links to websites in post #32
Usually there are several differently dated System Restores,
and iirc maybe the last one is not deleted. Vista does not
overwrite the XP system restores, just XP overwrites Vista.

hmm...that is **quite** a long thread! :D i'll try to read the parts relevant to my own problem, and hopefully can make some sense out of it...

Cheers! :guitar:

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> -------------------------------------

The MBR is a small portion of the drive at the beginning.
Grub can be installed to the MBR or XP can be installed to the 
MBR or Vista. [COLOR="Red"]I didn't follow your statement. 
[/COLOR]
To put XP back into the MBR you need to overwrite Vista which
at this point I'm assuming is in the MBR, with a command like
X:\fixmbr I don't think it sticks if issued from C:\ after
Windows is already loaded. Maybe you mean that.

Did you mean that you used X:\fixmbr and the used 
X:\bootrec /fixmbr to reinstall Vista to the MBR.

I think you meant choosing XP from the boot menu?
That loads boot files that are out on the disk not in the MBR.

XP seems to be on a fat32 partition. That is not the default and
takes some effort to accomplish. The default is ntfs.

I really don't know if XP boot.ini construes the fat16 bootit
partition as a primary. I think it likely does not. So that
means your partition number for XP should be (1) and I think
you have it as (2) which is the Vista partition number. 

I think it is worth trying to edit boot.ini and changes both
places where is say, partition(2) to partition(1) and try it.

I don't know if Bootit is preventing Vista from seeing XP 
because it hides XP first so that Easybcd can't boot it.
I'm just not sure. It seems to me that XP if its bootable
should also have a * beside it which means its bootable.

So I suggest changing the boot.ini partition number, run the
grub commands and install grub into the /boot partition of
sda4. The root and setup parameters are most likely (hd0,3)
but check with that find command first. 

Now boot to Vista. Run Easybcd and I think you should delete
the XP entry and the Ubuntu entries. Close Easybcd. Open it 
again and add XP (under Windows) back into Easybcd, and add 
Ubuntu which now has grub on (hd0,3) probably, back into the 
Linux entry. Now reboot and try both XP and then Ubuntu from
the Easybcd menu and see if either one now works.

Ok...let me clear this up for you. I inserted XP in the MBR (using BootIT NG), in the window that opens when u click on "View MBR". I simply replaced "MBR entry 1" which is the swap partition for Linux, with the XP entry. As for the partition maybe being partition (1), i can tell u straight out it is **not**. Believe me...i've tried 1,2,and 3 as the partition number in boot.ini, but none worked. I made sure to put it above and below [operating systems] each time, in both lines.... :confused:

Cheers! ):P

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> I said it is in Post #32, information about System Restore,
towards the bottom. You don't have to read the entire thread,
which consists of a few pages of numbered posts.

Yeah...i understood what you meant. I just thought there might have been more useful posts in that thread, that i should read...

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> [COLOR="Red"]Can you use Bootpart in place of Easybcd. Yes, but it is a lot
more work.[/COLOR] Here is how it used to be done before Easybcd.


I wasn't trying to use Bootpart in place of EasyBCD...:confused: What i said was that i could **not** install Bootpart on Vista, because it is NTFS and the program requires Fat filesystem...you were the one that suggested that that was what EasyBCD required in order to boot Ubuntu. :guitar:

Cheers! :lolflag:

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> As I mentioned in my first post, it has been too long since I used Bootit, 
and I don't seem qualified to help you with this problem. There is 
no guarantee my suggestions would have worked outside of a Bootit 
environment. I hope you find someone that is better qualified to 
give advice to your situation, meierfra is quite expert. Good luck.

Thanks for all your help! :guitar: BTW, who is meierfra?

Cheers! ):P

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> 
My other reason for showing you bootpart is LBA which stands for
Logical Block Address. Bootpart (Vista Easybcd GUI or standalone)
counts sectors from the beginning of the drive. When a partition
is resized it changes the partition's boundaries, the number of
sectors or distance from the beginning of the drive. 

[COLOR="Red"]When you moved Wubi from within Windows (do you have any other
Ubuntus as Wubis inside Windows)[/COLOR] I figured it might have changed
the value contained within the 512 byte segment. Or perhaps the
UUID value doesn't work anymore. So I doubt that the settings
in Easybcd are correct. So I think you should delete every one
of them besides the one for Vista, and then add them all in again
because it will create new counts for the 512 byte .bin segment.
So resizing and reinstall Easybcd were shorthand for this 
explanation because I don't intend to type this much in details.

I didn't realize that you already had Vista in the MBR, which is 
why I went through steps of putting it there in the earlier post.

So both Bootpart and fdisk -l (executed from the live cd if you 
can't boot Ubuntu) are good sources of information.

hmm...it seems i missed this part of your post! ;)

I have only **one** Wubi...the other Ubuntu that is on my computer is my transferred version (i.e. the Wubi install **transferred** to a real partition, using LVPM).

Thanks for the info. I was wondering what "LBA" meant, because i noticed it in several places, on the XP partition. I will delete all entries in EasyBCD (since they don't work anyway), except for Vista and Wubi, as i have tried before to boot into Wubi using EasyBCD, but that didn't work either.

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
EDIT: never mind

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> [http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

You will notice that this guide uses the dd command to create the
512 byte segment that eventually winds up in C:\ as linux.bin
dd only works on the same hard drive. When there are two hard
drives, dd doesn't work, but Bootpart's 512 bytes segment does.

[COLOR="Red"]So you can use the bootpart created *.bin file in place of the
dd command in the guide at the website above.[/COLOR] But it involves
more work. Notice that the steps there generate a Linux ID 
which has the same number of digits (12 I think) as UUID.

In my case I have XP and Vista on separate drives. When they are
on the same drive as in your case, they by MS design, have all
their boot files on just one Windows partition. Check it out.

So to get grub to work right, you have to put the files back
to their own correct partition. Grub needs a separate entry
for the boot files location (hdx,y) in the menu.lst for each
Windows partition and they use different UUIDs and titles.

That is why I went with the Vista bootloader rather than grub
because Vista/Easybcd will boot either Vista or XP without
any fuss with the boot files all congregated. And Linux OS too.

Hiding/unhiding is supposed to prevent XP from overwriting the
Vista System Restores. I don't have Bootit installed so I can't
address how well that is doing. Why don't you see how many
System Restore dates are available to you. If several then the
hide/unhide is probably working. The problem comes up when each
windows os is not hidden from each other. Vista Ultimate comes
with Bitlocker and prevents System Restores being overwritten by 
another means that doesn't require hide/unhide Windows partitions.

Is it possible to use EasyBCD for the same thing, in place of Bootpart? If so, how would i do it?

Looking forward to your reply...):P

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-18
Here's a pic of what Partition Work looks like (this one came from the BootIT NG **manual**, so don't mistake it for my own setup, because its not!;).

Especially take note of the "View MBR" on the left of the window, and also the layout of the partitions, so that when i explain (since i can't take a screenshot of my **own** BootIT NG window), what the partitions look like in my setup, it will be easy to replace the ones that are in this screenshot with my own setup! ;)

Cheers! :guitar:

P.S. i'll also grab a couple more pictures for you from the BootIT NG manual, which will hopefully explain itself far better than i could ever do with words! ):P

---

### Post by Jammanuser on 2008-12-18
On another note...how could i find out **precisely** where my Grub bootloader is? its obviously not in the MBR, which means its probably on a partition...possibly either my Linux partition or my swap partition. 

Is there any commands (i address this to anyone that might know the answer) that I could run, which would locate my Grub for me?

Thanks in advance! :guitar:

---

### Post by mkoyle on 2008-12-18
> **Jammanuser said:**
> On another note...how could i find out **precisely** where my Grub bootloader is? its obviously not in the MBR, which means its probably on a partition...possibly either my Linux partition or my swap partition. 

Is there any commands (i address this to anyone that might know the answer) that could run, which would locate my Grub for me?

Thanks in advance! :guitar:

Actually, post 8 answers that question:

> Boot the Ubuntu live cd, and open a terminal, and type
sudo fdisk -l (small letter L) and then press the <enter> key
which will list your installed OS and partitions for later use.
Usually you should copy and paste that report on this forum.

Then from the terminal type
[COLOR="Navy"]sudo grub
grub>find /boot/grub/stage1[/COLOR] Use this information for next step,
grub>root (hd0,x) x equals the number obtained by the find command
grub>setup (hd0,x) grub is installed to the /boot partition not MBR
grub>quit

Your fdisk report will say something like sda3 which converts
to (hd0,2) the grub partition numbering notat^ion is one less.
Another example: sda6 = (hd0,5)

I'm out of my depth... I'm just trying to figure out a dual-boot right this moment, but I believe that will at least locate the /boot things for you.  Install the grub onto that partition the way he already told you and you are that much closer.

One more thing... although there is a message about NTFS and bootpart, for the simple creation of an ini file and modification of boot.ini, it works just fine.

---

### Post by Jammanuser on 2008-12-18
> **mkoyle said:**
> [COLOR="Red"]Actually, post 8 answers that question.[/COLOR]
I'm out of my depth... I'm just trying to figure out a dual-boot right this moment, but I believe that will at least locate the /boot things for you.  [COLOR="Red"]Install the grub onto that partition the way he already told you and you are that much closer.[/COLOR]

One more thing... although there is a message about NTFS and bootpart, for the simple creation of an ini file and modification of boot.ini, it works just fine.

Not completely. I do believe the commands you highlighted in blue locate Grub...but the next commands he said run, i'm pretty installs Grub (if i have that wrong, please correct me!). The thing is...i don't want to install Grub, because it is already installed. :guitar:

And one more thing...what exactly "works just fine"? I'm confused...:confused:

Anyway, good luck with your own dual boot! ):P

Cheers! :guitar:

EDIT: side note: i've also run those commands before, but they didn't work...but i'll try them again, i guess, and maybe they'll work this time! :D 

Cheers!

-Jam man

:guitar:

---

### Post by mkoyle on 2008-12-18
Bootpart will work on an NTFS partition... even though there is a note on their web page says something about it not working for NTFS.  Apparently some of the things bootpart will do do not work on NTFS partitions.

To be able to boot your Ubuntu installation, a grub bootloader has to be installed *somewhere*.  Those commands will not get rid of a Vista / XP MBR (Master Boot Record) but will install an additional boot sector on just the Ubuntu partition.

I just got my dual boot squared away.  I'm using the NT boot manager (the one that usually only lists Windows versions) and it lists Ubuntu, too.  I installed Ubuntu and then installed Windows XP, so the XP bootloader had gotten rid of grub so I could not boot Ubuntu off the second hard drive partition, yet.

To fix this, I started in Windows XP.

I downloaded bootpart from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm), and extracted it to c:\bootpart.  Then I executed the following:

```
bootpart
bootpart 4 c:\ubuntu.lnx Ubuntu Linux
```

(this all worked fine even though it is just on an NTFS partition).

Then I started an Ubuntu Live CD, and booted from it to the Ubuntu desktop.  I opened a terminal (actually, I pressed Ctrl-Alt-F1). And executed the following:

```
sudo grub
find /boot/grub/stage1
root (hd0,3)
setup(hd0,3)
quit
```

On a reboot, selecting "Ubuntu Linux" boots into Ubuntu and waiting or selecting Windows XP... boots to Windows, so I'm squared away.

The grub bootloader is not on the MBR and only loads if I select Ubuntu Linux from the Windows boot up selector.

Good luck,

--Matthew

---

### Post by Jammanuser on 2008-12-18
Also, for the benefit of anyone viewing this thread, take a look at my BootIT NG window...and the one of Gparted. Notice that Gparted shows the approx. 10 GB second partition of my hard drive as "unallocated space" while BootIT NG on the other hand shows it as an NTFS partition...

Might give you something to think about! ;)

---

### Post by Jammanuser on 2008-12-18
> **mkoyle said:**
> [COLOR="Red"]Bootpart will work on an NTFS partition... even though there is a note on their web page says something about it not working for NTFS.[/COLOR]  Apparently some of the things bootpart will do do not work on NTFS partitions.

Ahh...ok! thanks for clearing that part up! :guitar: You see, I had gone to the website (both the download page, and also to their forum), and i read that the program could not work on NTFS partitions...it could only work on Fat. However, if you say it does...

I guess i'll have to try it then, and see if it works in my case!

Cheers! :popcorn:
> **mkoyle said:**
> 
To be able to boot your Ubuntu installation, a grub bootloader has to be installed *somewhere*.  Those commands will not get rid of a Vista / XP MBR (Master Boot Record) but will install an additional boot sector on just the Ubuntu partition.

I just got my dual boot squared away.  I'm using the NT boot manager (the one that usually only lists Windows versions) and it lists Ubuntu, too.  I installed Ubuntu and then installed Windows XP, so the XP bootloader had gotten rid of grub so I could not boot Ubuntu off the second hard drive partition, yet.

To fix this, I started in Windows XP.

I downloaded bootpart from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm), and extracted it to c:\bootpart.  Then I executed the following:

```
[COLOR="Red"]bootpart
bootpart 4 c:\ubuntu.lnx Ubuntu Linux[/COLOR]
```

(this all worked fine even though it is just on an NTFS partition).

Then I started an Ubuntu Live CD, and booted from it to the Ubuntu desktop.  I opened a terminal (actually, I pressed Ctrl-Alt-F1). And executed the following:

```
sudo grub
find /boot/grub/stage1
root (hd0,3)
setup(hd0,3)
quit
```

On a reboot, selecting "Ubuntu Linux" boots into Ubuntu and waiting or selecting Windows XP... boots to Windows, so I'm squared away.

The grub bootloader is not on the MBR and only loads if I select Ubuntu Linux from the Windows boot up selector.

Good luck,

--Matthew

Ok, thanks...so where do i enter the first commands you gave (i.e. the bootpart ones)? Do i run those in my Command Prompt back in Vista, or am i supposed to run that using the Ubuntu LiveCD? I'm sorry if that's a stupid question...

Looking forward to your reply...:guitar:

---

### Post by Jammanuser on 2008-12-18
I just tried it (that is, the bootpart commands) in the Command Prompt in Vista, Matthew, but i got the following error message when i typed "bootpart" without the quotes:

```
'bootpart' is not recognized as an internal or external command, operable program or batch file.
```

So it appears that that's not what you meant...:guitar:

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-18
> **TeXtonyx said:**
> I told you that I had used Bootpart on Vista to create linux.bin
and add it to the bcd menu manually, I provided the url on how
to add the 512 byte .bin file manually rather than with Easybcd.

[COLOR="Red"]Now if I couldn't use Bootpart on Vista how I could I do that?
I think you mean you read documentation which is 11 and 1/2 years
out of date and relied on that, rather than taking a minute to
download bootpart and unzip bootpart.exe to Vista's C:\ and
then type C:\bootpart.exe <enter> and see the result. [/COLOR]

I said that the bootpart which was part of your screenshot was
the same Bootpart that I used for XP. They both use the same
engine. I said Bootpart 2.60a was already part of Easybcd and
used your screenshot to prove it. I said I used bootpart by 
itself to create entries in XP's boot.ini when you asked me.
I did not say you needed to download Bootpart to make Easybcd
work, its already part of Easybcd. I said that C:\bootpart.exe
and fdsik -l provided useful information about how your partitions were structured. 

--------------------------------------------

Physical number of disk 0 : 56d9f43b
 0 : C:* type=7  (HPFS/NTFS), size= 64974861 KB, Lba Pos=63
 1 : C:  type=5  (Extended), size= 15028807 KB, Lba Pos=130769100
 2 : C:  type=83   (Linux native), size= 14354046 KB, Lba Pos=130769163
 3 : C:  type=5   (Extended), size= 674730 KB, Lba Pos=159477255
 4 : C:  type=82    (Linux swap), size= 674698 KB, Lba Pos=159477318
Physical number of disk 1 : 9ad7b
 5 : D:* type=83  (Linux native), size= 19462716 KB, Lba Pos=63
 6 : D:  type=5  (Extended), size= 891607 KB, Lba Pos=38925495
 7 : D:  type=82   (Linux swap), size= 891576 KB, Lba Pos=38925558

---------------------------------------

This is a list of partitions. What do you use now from Vista or
XP that provides you with this information? Certainly not Disk
Management which is not detailed about Linux partitions.

Ahh...ok. thanks! :guitar: i believe i missed that in your post...

I just typed "C:\bootpart.exe" without the quotes, and it opened up bootpart! 

Thanks! :guitar:

EDIT: here is the output of the Command Prompt in Vista, after i ran that command: 

```
Physical number of disk 0: 3c5a8d58
  0: C: type=6 <BIGDOS FAT 16>, size= 40131 KB, LBA Pos=63
  1: C: type=82 <Linux swap>, size= 4602622 KB, LBA Pos=547655850
  2: C: type=7 <HPFS/NTFS>, size= 243072920 KB, LBA Pos=20560325
  3: C: type=83 <Linux native>, size= 20474842 KB, LBA Pos=50670615
```

Now what? Do I continue with the second command posted by Matthew?

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by TeXtonyx on 2008-12-18
Delete

---

### Post by Jammanuser on 2008-12-19
> **TeXtonyx said:**
> Yes, I have been telling you how to do that. Easybcd already
uses Bootpart. I told you about that so you could better understand
how it works. [COLOR="Red"]reinstall grub to the Ubuntu /boot partition [/COLOR]
delete the current Ubuntu entry in Easybcd (not Wubi) and then add 
it back in, I want to reset the boundary values that are now used. 
Test it. The least we should get is an informative error message
or evidence regarding bootit.

Alright...rather than pointing out again that Grub is **already** installed somewhere on my computer, i guess i'll just go ahead and reinstall it again, with those commands..

Be back in a bit...

---

### Post by Jammanuser on 2008-12-19
Ok...i went ahead and reinstalled Grub with those commands. Here's the terminal output:

```
ubuntu@ubuntu:~$ sudo grub 
Probing devices to guess BIOS drives. This may take a long time. 

       [ Minimal BASH-like line editing is supported.   For 
         the   first   word,  TAB  lists  possible  command 
         completions.  Anywhere else TAB lists the possible 
         completions of a device/filename. ] 
grub> find /boot/grub/stage1 
find /boot/grub/stage1 
 (hd0,3) 
grub> root (hd0,3) 
root (hd0,3) 
grub> setup (hd0,3) 
setup (hd0,3) 
 Checking if "/boot/grub/stage1" exists... yes 
 Checking if "/boot/grub/stage2" exists... yes 
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal) 
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal) 
 Running "install /boot/grub/stage1 (hd0,3) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded 
Done. 
grub> 
```

I rebooted, and it went straight to the BootIT NG program...from that, i selected "Windows Vista", and it went to the Vista bootloader as always...but I still can not access Grub.  I then proceeded to add a new boot entry with EasyBCD for Ubuntu, rebooted again, and get the same exact error that i mentioned in previous posts...

It appears as if EasyBCD doesn't work for what i'm trying to do...

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-19
Delete

---

### Post by TeXtonyx on 2008-12-19
Delete

---

### Post by Jammanuser on 2008-12-19
> **TeXtonyx said:**
> You download bootpart.zip You have to unzip the files and
extract bootpart.exe to C:\
then you type C:\bootpart <enter>

When a user first opens a command prompt, by default the
directory is something like C:\Documents\yourusername
if you type bootpart there it won't work because that is
not where the bootpart.exe file is located. You need to
type bootpart from the directory where it exists not 
from where it doesn't exist.

Thanks...but i'm past that part now. I managed to open up Bootpart using the other command: C:\Bootpart.exe
The other command **after** that, that Matthew mentioned, is what i really needed. However, when i tried to run it, it failed as well...
> **TeXtonyx said:**
> 
I told you about Bootpart for informational purposes not
as part of your solution; your [B][COLOR="Red"]solution is to put Vista
in the MBR and use Easybcd.[/COLOR][/B] Remove Bootit. The documentation
for Bootit is way over your head. So far you have done nothing
but waste your time. I'm a computer professional and I tested
Bootit before. I discarded it because the documentation took
hours of my time to figure out. You have no chance whatsoever.
So stop being stubborn, this is not an issue calling for
persistence. How does this quote from the [COLOR="Red"]Bootit UG[/COLOR] relate
to your situation and what I've already told you about?


First of all, Vista is **already** in the MBR...as i do recall us over going before...and EasyBCD (which is what i've been trying to use for the last few...umm**(decades?)**, has so far not been the solution...Did you read my last post? As for BootIT NG being over my head...i think you got that wrong. I have not used if for very long, but I already practically understand it completely...and i also **like** the program! :) Perhaps you're not quite the computer professional you make out to be...and its BootIt **NG**, btw, not BootIt **UG**! :lolflag:
> **TeXtonyx said:**
> 
Using the Multi-OS Feature Page 34
"The BootIt NG Multi-OS feature lets you boot more than one 
operating system from the same primary partition. BootIt NG 
supports Multi-OS *only* in a FAT or **FAT32** primary partition.

To enable this feature, select the Multi-OS check box when 
creating the partition or, after the partition is created, 
select the Multi-OS check box in the properties dialog box 
available through the Work with Partitions dialog box. 
Once enabled, you can install multiple operating systems into 
the Multi-OS partition (but in different folders) or, you can 
install multiple OSes in separate partitions and use the 
Multi-OS partition as a shared boot partition."


That is not the post i referenced you to...](*,)
> **TeXtonyx said:**
> 
TeX: I mentioned that when two versions of Windows are on the
same hard drive that the boot files of one of the Windows OS
usually wind up all on the other Windows partition all mixed
together. Vista is an ntfs partition. [COLOR="Red"]Did you check to see
where the boot files are? On Vista/ntfs or on XP/fat32. [/COLOR]


Yes, and the boot files are on my Vista partition, which is NTFS. I'm pretty sure i mentioned that before in previous posts...
> **TeXtonyx said:**
> 
Bootit was the best 10 years ago. Now the simple solutions 
provided by Easybcd or grub for lower-level computer literates
makes them the tool of choice. That's why you aren't finding
any help on this forum: nearly everybody doesn't *know how* to
use bootit and the computer experts who know how, also know better.

Having high intelligence is not very important when it comes to
fixing computer problems. Much more important is to have education
and experience. People who think they are really intelligent also
think that it's not necessary to read the instructions first. These
are exactly the people more likely to damage their systems, trying
"intuitive" solutions like a chicken with its head cut off. When 
one becomes expert the first thing you do is read the directions
and you judge software by the quality of its documentation rather
than hype about the tricks it can perform that nobody ever needs.

hmm...perhaps the reason that most people do not use BootIT NG is because they have never tried it. If they **had** tried it, like me they would probably prefer it over any other partitioning program. But i think that's a moot point...and I never said that I thought I was really intelligent. You misunderstood me if you thought that. As for reading the directions...what makes you think that i have not? Do you take me for a **complete** idiot? [-X

Cheers! ):P

Jam man

:popcorn:

---

### Post by Jammanuser on 2008-12-19
> **TeXtonyx said:**
> Does your Ubuntu grub menu.lst have the right setting for the
Ubuntu partition, (hd0,3)?

Yes. Indeed it does...it is hd0,3. I can boot it just fine using the Super Grub Disk...it is only when i try to boot it with the Vista bootloader, that I have problems. :guitar:

Cheers! :lolflag:

Jam man

):P

---

### Post by meierfra. on 2008-12-19
Lets see whether EasyBCD/bootpart and Grub are  configured correctly:

Run the following code in a ubuntu terminal:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

```

That will create a "boot_info_results.txt" file on your desktop; please copy/paste the contents of that file to your next post.

---

### Post by mkoyle on 2008-12-19
What is the output when you run bootpart?  Nothing I see about bootpart in its documentation suggests that it is compatible with Vista, so I am guessing it just plain is not.

Can you set bootit to start the Ubuntu partition?  Now that you have installed grub to the drive, it should be able to boot ubuntu directly from that partition if it tries.

For example, because there were no later posts, it seems that a similar problem was fixed for someone here [http://ubuntuforums.org/archive/index.php/t-415652.html](http://ubuntuforums.org/archive/index.php/t-415652.html) ... good reason to post the final result, by the way-- so that future poor souls know it worked.

---

### Post by TeXtonyx on 2008-12-19
Delete

---

### Post by Jammanuser on 2008-12-19
> **meierfra. said:**
> Lets see whether EasyBCD/bootpart and Grub are  configured correctly:

Run the following code in a ubuntu terminal:
```

cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt

```

That will create a "boot_info_results.txt" file on your desktop; please copy/paste the contents of that file to your next post.

Just when I had given up all hope...:guitar: Thanks!

I ran that command, and here is the info from the file:

```
#!/bin/bash
#to use this script:
#
#sudo sh boot_info_script.txt
#
#date  12/18/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifes the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR's is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs: displays the offset of the partition as recorded
#          in  the boot sector
#   Identifes their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu"
#   Displays "sfdisk -d"
#   Finds  boot directories and displays their contents.
#   For EasyBCD: finds all bootpart codes  and displays the offset
#                and boot drive its is trying to chainloade. 
#   Finds and displays  boot configuration files.
#All information is written to the file "boot_info_results.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   Identify Distros. 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Read bootpart files and see which boot sector it is pointing to.  
#   Test the script on different distros.


Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    "

Dir=`cd $(dirname $0);pwd`;
LogFile=$Dir/boot_info_results.txt

exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! sudo mkdir $Folder$i 2>/dev/null)
    do  
      i=$((i+1));
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash )
for drive in $Hard_Drives;
  do 
    Message=$( echo is installed in the MBR of  $drive)
    case $(hexdump   -n  2 -e '/1 "%x"'  $drive) in
	eb48) pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 		else
		BL=Grub;
	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message  and  looks on the same drive in partition \#$pa  for its boot files.)
              else
               Message=$(echo $Message  and looks  on boot drive \#$dr in partition \#$pa  for its boot files.)
            fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        echo $BL $Message
  
    sfdisk -d  $drive >>$Log1;
    done
    echo


for part in $(ls /dev/hd??* /dev/sd??* 2>>$Trash)
   do
      BSI=""
      drive=$(expr substr $part  1 8)
      name=$(basename $part);
      echo  $name:;
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ "$type" = ""  ];
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:  "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 
      if  mount $part $name 2>$Mount_Error; then
      if [ "$type" = "ntfs" ];
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to  the  info in the boot sector, $name starts at sector $offset.)   
      fi;
          case $(hexdump  -s 0x80 -n  2 -e '/1 "%x"'  $part) in
            08cd) BST=XP;;
            b6d1) BST=XP;;
	    55aa) BST=Vista;;
	    5272) BST=Grub;
                 offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $part);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                   pa=-1
                  for hdd in $Hard_Drives;
		  do
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ $tmp = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ $dr = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file.);
                    
                        if [ $pa = -1  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ $pa = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
               *) BST=Unknown;;
       esac;

       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS=Vista

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS=XP
  
       [ -e $name"/lib" ] && OS=Linux
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              cat $name$file >> $Log1;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;

       for file in $Boot_Dir;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
              if [ "$file" = "/NST" ];
		  then
		  for loader in $( ls  $name$file );
		  do
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file/$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file/$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file/$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in $loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		  done;
               fi;
	   fi;
       done;

      echo "    Boot sector  type:  "$BST
      echo "    Boot sector  info:  "$BSI  
      echo "    Operating System: "$OS
      echo "    Boot files/directories present: " $BootFiles
     
     umount $name ;
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;

fdisk -lu
echo >> $Log1
echo "StdErr Messages ">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
cat $Error_Log
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile)   located in $Dir


```

There you go. Hopefully you can make some sense out of it...

Cheers! ):P

---

### Post by meierfra. on 2008-12-19
You posted the script. You need to post the file containing the results: boot_info_results.txt

---

### Post by Jammanuser on 2008-12-19
Here's something else...when I boot into Ubuntu, using the Super Grub Disk, before the actual boot process, and when i'm viewing the Super Grub Disk window, right before selecting the Ubuntu partition to boot from...right above it, it shows the IDE, which is (hda4)...but the actual partition that Ubuntu and Grub is installed on is (hd0,3). ;)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-19
> **meierfra. said:**
> You posted the script. You need to post the file containing the results: boot_info_results.txt

Alright...i was wondering if that's what you wanted! I'll upload the file...even though the text will be the same, because that's where i copied it from. :guitar:

Cheers! ):P

EDIT: never mind...i just noticed that the two files were different. I thought they were the same! i'll post the other one right away...

---

### Post by Jammanuser on 2008-12-19
Here's the boot_info_results.txt:

```
No known boot loader is installed in the MBR of /dev/sda

sda1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda2:
    File system:  swap

sda3:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda3 starts at sector 20560325. BootPart in nst_grub-01989DCEF0324D997FFB79052C605827.mbr is trying to chain load sector #506706165 on boot drive #1 BootPart in nst_grub.mbr is trying to chain load sector #506706165 on boot drive #1
    Operating System: Vista
    Boot files/directories present:  /ubuntu/disks/boot/grub/menu.lst /boot.ini /bootmgr /ntldr /ntdetect.com /wubildr.mbr /ubuntu/winboot/wubildr.mbr /boot /ubuntu/disks /ubuntu/disks/boot/ /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub /NST

sda4:
    File system:  ext3
    Boot sector  type:  Grub
    Boot sector  info:  Grub is installed to the boot sector of /dev/sda4 and looks at sector 527464797 of the same hard drive for the stage2 file. (a stage2 file is at this location on /dev/sda) and on partition #4 for menu.lst.
    Operating System: Linux
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131    6  FAT16
/dev/sda2       547655850   556861094     4602622+  82  Linux swap / Solaris
/dev/sda3   *    20560325   506706164   243072920    7  HPFS/NTFS
/dev/sda4       506706165   547655849    20474842+  83  Linux

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=    80262, Id= 6
/dev/sda2 : start=547655850, size=  9205245, Id=82
/dev/sda3 : start= 20560325, size=486145840, Id= 7, bootable
/dev/sda4 : start=506706165, size= 40949685, Id=83

sda3/ubuntu/disks/boot/grub/menu.lst

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
# kopt=root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



sda3/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


sda3/boot

total 4172
drwxrwxrwx 1 root root    8192 2008-12-10 21:30 .
drwxrwxrwx 1 root root   12288 2008-12-19 12:02 ..
-rwxrwxrwx 1 root root   28672 2008-12-19 12:04 BCD
-rwxrwxrwx 1 root root  262144 2008-12-10 14:34 BCD.Backup.0001
-rwxrwxrwx 1 root root  262144 2008-12-19 12:04 BCD.LOG
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG1
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG2
-rwxrwxrwx 1 root root    1024 2008-03-04 09:08 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-03-04 09:08 boot.sdi
-rwxrwxrwx 1 root root   65536 2008-02-03 16:06 bootstat.dat
drwxrwxrwx 1 root root       0 2008-02-03 16:06 cs-CZ
drwxrwxrwx 1 root root       0 2008-02-03 16:06 da-DK
drwxrwxrwx 1 root root       0 2008-02-03 16:06 de-DE
drwxrwxrwx 1 root root       0 2008-02-03 16:06 el-GR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 en-US
drwxrwxrwx 1 root root       0 2008-02-03 16:06 es-ES
-rwxrwxrwx 1 root root    2048 2008-03-04 15:05 etfsboot.com
drwxrwxrwx 1 root root       0 2008-02-03 16:06 fi-FI
drwxrwxrwx 1 root root    4096 2008-02-03 16:06 fonts
drwxrwxrwx 1 root root       0 2008-02-03 16:06 fr-FR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 hu-HU
drwxrwxrwx 1 root root       0 2008-02-03 16:06 it-IT
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ja-JP
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ko-KR
-rwxrwxrwx 1 root root  406584 2008-01-20 19:23 memtest.exe
drwxrwxrwx 1 root root       0 2008-02-03 16:06 nb-NO
drwxrwxrwx 1 root root       0 2008-02-03 16:06 nl-NL
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pl-PL
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pt-BR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pt-PT
-rwxrwxrwx 1 root root   20480 2008-12-10 21:30 Recovery.bcd
-rwxrwxrwx 2 root root   17408 2008-12-10 21:30 Recovery.bcd.LOG
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG1
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG2
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ru-RU
drwxrwxrwx 1 root root       0 2008-02-03 16:06 sv-SE
drwxrwxrwx 1 root root       0 2008-02-03 16:06 tr-TR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-CN
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-HK
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-TW

sda3/ubuntu/disks

total 14648448
drwxrwxrwx 1 root root           0 2008-12-13 00:03 .
drwxrwxrwx 1 root root        4096 2008-12-12 15:54 ..
drwxrwxrwx 1 root root        4096 2008-12-12 17:15 boot
-rwxrwxrwx 2 root root 14000000000 2008-12-15 18:31 root.disk
drwxrwxrwx 1 root root           0 2008-12-12 15:53 shared
-rwxrwxrwx 2 root root  1000000000 2008-12-12 17:10 swap.disk

sda3/ubuntu/disks/boot/

total 13016
drwxrwxrwx 1 root root    4096 2008-12-12 17:15 .
drwxrwxrwx 1 root root       0 2008-12-13 00:03 ..
-rwxrwxrwx 1 root root  503560 2008-10-24 01:55 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root   85316 2008-10-24 01:55 config-2.6.27-7-generic
drwxrwxrwx 1 root root       0 2008-12-12 17:15 grub
-rwxrwxrwx 1 root root 8901816 2008-12-12 17:15 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rwxrwxrwx 1 root root 1352144 2008-10-24 01:55 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root    1130 2008-10-24 01:57 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-10-24 01:55 vmlinuz-2.6.27-7-generic

sda3/ubuntu/disks/boot/grub

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

sda3/ubuntu/disks/boot/grub

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

sda3/NST

total 21
drwxrwxrwx 1 root root  4096 2008-12-18 22:24 .
drwxrwxrwx 1 root root 12288 2008-12-19 12:02 ..
-rwxrwxrwx 2 root root   512 2008-12-18 22:24 nst_grub-01989DCEF0324D997FFB79052C605827.mbr
-rwxrwxrwx 1 root root   512 2008-12-15 00:56 nst_grub.mbr

sda4/boot/grub/menu.lst

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
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,2)
makeactive
chainloader +1
boot


title Windows Vista/Longhorn (loader)
root (hd0,2)
makeactive
chainloader +1
boot


sda4/boot

total 12812
drwxr-xr-x  3 root root    4096 2008-12-15 18:24 .
drwxr-xr-x 21 root root    4096 2008-11-13 05:25 ..
-rwxr-xr-x  1 root root  503560 2008-12-15 18:23 abi-2.6.27-7-generic
-rwxr-xr-x  1 root root   85316 2008-12-15 18:23 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-15 18:30 grub
-rwxr-xr-x  1 root root 8647292 2008-12-15 18:24 initrd.img-2.6.27-7-generic
-rwxr-xr-x  1 root root  124152 2008-12-15 18:23 memtest86+.bin
-rwxr-xr-x  1 root root 1352144 2008-12-15 18:23 System.map-2.6.27-7-generic
-rwxr-xr-x  1 root root    1130 2008-12-15 18:23 vmcoreinfo-2.6.27-7-generic
-rwxr-xr-x  1 root root 2339712 2008-12-15 18:23 vmlinuz-2.6.27-7-generic

sda4/boot/grub

total 344
drwxr-xr-x 2 root root   4096 2008-12-15 18:30 .
drwxr-xr-x 3 root root   4096 2008-12-15 18:24 ..
-rwxr-xr-x 1 root root    191 2008-12-15 18:23 default
-rwxr-xr-x 1 root root     30 2008-12-15 18:23 device.map
-rwxr-xr-x 1 root root   8108 2008-12-15 18:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2008-12-15 18:24 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2008-12-15 18:24 jfs_stage1_5
-rwxr-xr-x 1 root root   5319 2008-12-15 18:30 menu.lst
-rw-r--r-- 1 root root   5304 2008-12-15 18:24 menu.lst~
-rwxr-xr-x 1 root root   7352 2008-12-15 18:24 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2008-12-15 18:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2008-12-15 18:24 stage1
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2008-12-15 18:24 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sda

00000000  fc eb 47 80 42 6f 6f 74  69 74 20 45 4d 42 52 49  |..G.Bootit EMBRI|
00000010  20 32 2e 30 31 0d 0a 0a  00 43 6f 70 79 72 69 67  | 2.01....Copyrig|
00000020  68 74 20 28 63 29 20 31  39 39 36 2d 32 30 30 30  |ht (c) 1996-2000|
00000030  2c 20 32 30 30 35 20 54  65 72 61 42 79 74 65 20  |, 2005 TeraByte |
00000040  55 6e 6c 69 6d 69 74 65  64 2e 33 c0 be 00 30 fa  |Unlimited.3...0.|
00000050  8e d6 89 c4 fb ea 5a 00  c0 07 0e 1f be 04 00 e8  |......Z.........|
00000060  bb 00 8e c0 8b f8 b4 08  8a 16 03 00 cd 13 72 1f  |..............r.|
00000070  80 e1 3f 88 0e 91 01 b4  02 a0 91 01 33 db b9 01  |..?.........3...|
00000080  00 33 d2 8a 16 03 00 68  e0 07 07 cd 13 73 05 be  |.3.....h.....s..|
00000090  38 01 eb 7c 06 1f 81 c3  00 02 8d 77 02 ad 3d 49  |8..|.......w..=I|
000000a0  42 75 0a ad 3d 4d 20 75  04 81 c3 00 02 89 de ad  |Bu..=M u........|
000000b0  3d 45 4d 75 2a ad 3d 42  52 75 24 ac 24 e0 75 1a  |=EMu*.=BRu$.$.u.|
000000c0  ac 2e 3a 06 91 01 77 0d  ad 50 ad 3d 00 02 74 14  |..:...w..P.=..t.|
000000d0  be 38 01 eb 3b be 68 01  eb 36 be 5a 01 eb 31 be  |.8..;.h..6.Z..1.|
000000e0  76 01 eb 2c 58 24 3f c1  e0 09 01 c3 8b 07 3d 55  |v..,X$?.......=U|
000000f0  aa 75 1a 89 de 33 ff 68  00 20 07 b9 00 28 f3 a5  |.u...3.h. ...(..|
00000100  1e 07 2e 8a 2e 03 00 ea  03 00 00 20 cb be 83 01  |........... ....|
00000110  0e 1f e8 08 00 be 47 01  e8 02 00 eb fe 06 53 50  |......G.......SP|
00000120  56 57 ac 3c 00 74 0b bb  07 00 b4 0e 56 cd 10 5e  |VW.<.t......V..^|
00000130  eb f0 5f 5e 58 5b 07 c3  48 61 72 64 77 61 72 65  |.._^X[..Hardware|
00000140  20 45 72 72 6f 72 00 07  20 2d 20 53 79 73 74 65  | Error.. - Syste|
00000150  6d 20 48 61 6c 74 65 64  21 00 56 65 72 73 69 6f  |m Halted!.Versio|
00000160  6e 20 43 68 65 63 6b 00  53 50 54 20 3c 20 4d 69  |n Check.SPT < Mi|
00000170  6e 69 6d 75 6d 00 45 4d  42 52 20 6d 69 73 73 69  |nimum.EMBR missi|
00000180  6e 67 00 45 4d 42 52 4c  20 6d 69 73 73 69 6e 67  |ng.EMBRL missing|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  58 8d 5a 3c 00 00 00 01  |.....,DcX.Z<....|
000001c0  01 00 06 fe 3f 04 3f 00  00 00 86 39 01 00 00 00  |....?.?....9....|
000001d0  c1 ff 82 fe ff ff aa 90  a4 20 fd 75 8c 00 80 d1  |......... .u....|
000001e0  d8 ff 07 fe ff ff c5 b9  39 01 30 ff f9 1c 00 00  |........9.0.....|
000001f0  c1 ff 83 fe ff ff f5 b8  33 1e b5 d7 70 02 55 aa  |........3...p.U.|
00000200

```

Sorry about the mixup...i didn't look very closely!

Cheers! :guitar:

---

### Post by Jammanuser on 2008-12-19
> **mkoyle said:**
> What is the output when you run bootpart?  Nothing I see about bootpart in its documentation suggests that it is compatible with Vista, so I am guessing it just plain is not.

Can you set bootit to start the Ubuntu partition?  Now that you have installed grub to the drive, it should be able to boot ubuntu directly from that partition if it tries.

For example, because there were no later posts, it seems that a similar problem was fixed for someone here [http://ubuntuforums.org/archive/index.php/t-415652.html](http://ubuntuforums.org/archive/index.php/t-415652.html) ... good reason to post the final result, by the way-- so that future poor souls know it worked.

So would the commands mentioned in the following quote of what it said in the link u gave me work in my case? Would it enable BootIT NG to boot my Linux partition **directly**?

> GRUB normally gets installed onto the MBR of the hard disk. As the PC boots from the MBR, it loads GRUB and GRUB then loads Linux from the partition it has been set for. At no stage does the partition get booted.

If you want to make the Ubuntu root partition bootable, you shoud boot into Ubuntu and then issue the following command:
[COLOR="Red"]sudo grub-install /dev/xxx[/COLOR]
where xxx is the device id of your root partition. Youcan get this from the command
[COLOR="Red"]df -h[/COLOR]
For instance, my df -h says that my / is on filesystem /dev/sda7 so I would say grub-install /dev/sda7. This installs grub into the root partition and makes the partition bootable, so now your other funny bootloader should be happy. You haven't deleted the boot code from the MBR though, so now you have two ways of booting Ubuntu.

Looking forward to your reply...

---

### Post by meierfra. on 2008-12-19
Every thing seems to be configured correctly. Your ubuntu partition starts at roughly 250GB, some Bios can only read the first 137GB. But I doubt that this is the issue, since Supergrub is able to boot Ubuntu.

> So would the commands mentioned in the following quote of what it said in the link u gave me work in my case? Would it enable BootIT NG to boot my Linux partition directly?

You don't need to run "grub-install" since grub is already installed correctly in the boot sector of /dev/sda4. You need to tell BootID to boot from /dev/sda4.  But I don't have any experience with BootID, so I can't tell you how to do that.


You can also try to use [NeoGrub]("http://neosmart.net/wiki/display/EBCD/NeoGrub")

If none of that works, you should install Grub to the MBR:

```

sudo dd if=/dev/sda of=MBR_Backup count=63
sudo grub 
```

and at the grub prompt

```
root (hd0,3)
setup (hd0)
quit
```

You "menu.lst" seems to  need some fixing (but that is a minor issue). When you boot with SuperGrub, does the grub menu appear, or do you boot directly into Ubuntu?

---

### Post by Jammanuser on 2008-12-19
> **meierfra. said:**
> 
You "menu.lst" seems to  need some fixing (but that is a minor issue). When you boot with SuperGrub, does the grub menu appear, or do you boot directly into Ubuntu?

When i boot with the Super Grub disk I have to navigate through several menus, until at last I see the partition that Ubuntu is installed on. When I boot from that, it **then** sends to the Grub menu! ;)

I hope that answers your question.

Thanks! ):P

-Jam man

P.S. I would still like to find a way for BootIT NG to boot the Ubuntu partition, though...

EDIT: and what do I need to do to fix my menu.lst file? for that matter, what's wrong with it?

---

### Post by Jammanuser on 2008-12-19
Well...I reinstalled BootIT NG, and when I rebooted...the program now had my Linux partition in the boot menu. I selected it, and it booted FINE to Ubuntu! :guitar: And then I came straight here...

I haven't tried XP yet though, to see if that one works yet, but at least now I can boot into Ubuntu fine, although not through the Vista bootloader! :D

I'll go try XP and make my report...:guitar:

Cheers! :lolflag:

---

### Post by TeXtonyx on 2008-12-19
Delete

---

### Post by meierfra. on 2008-12-19
>  and it booted FINE to Ubuntu! 


Great news.

> EDIT: and what do I need to do to fix my menu.lst file? for that matter, what's wrong with it?

Change:

# groot=()/ubuntu/disks

to

# groot=(hd0,3)


(otherwise you will have problems after the next kernel update


deleted everything from

title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst

on

(That's just to clean up your Grub menu)


You might also want to change:

# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio


to

# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro 


("ROOTFLAGS=syncio" is an option used by a wubi install and I never have seen it used for a regular install. But I don't  really know what it does)


Then in a terminal.

```
sudo update-grub
```

---

### Post by meierfra. on 2008-12-19
Do you know  where your XP partition could be?

I see  three  possibilities:

1)  It got formated to "swap".

2) Its hiding in the 38GB of unallocated space at the end of your disk.

3)  It got overwritten by Ubuntu.

In case 1) and 2) we should be able to rescue your XP partition.  In case 3) your XP partition is gone (unless you are willing to spend some money on a professional rescue)


To avoid any further damage in Case 1)

```
sudo  swapoff /dev/sda2
```

You can use testdisk to figure out where your XP partition is hiding:
(instruction borrowed from caljohnsmith)

Make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```


sudo apt-get install testdisk
sudo testdisk


```

**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there.

**If you are using Version 6.9:**
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results, and we can work from there.

---

### Post by TeXtonyx on 2008-12-19
Delete

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
> Great news.

Indeed it is! :guitar: I'm glad i finally got it booting without using Super Grub Disk,through BootIT NG at least...of course I **would** also like to be able to boot using the Vista bootloader, as well! ;)

But who knows? Maybe this will be possible once I try NeoGrub, which I have not done yet...

Hopefully it will! :popcorn:

Cheers! ):P


> **meierfra. said:**
> 
Change:

# groot=()/ubuntu/disks

to

# groot=(hd0,3)


(otherwise you will have problems after the next kernel update


deleted everything from

title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst

on

(That's just to clean up your Grub menu)


You might also want to change:

# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio


to

# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro 


("ROOTFLAGS=syncio" is an option used by a wubi install and I never have seen it used for a regular install. But I don't  really know what it does)


Then in a terminal.

```
sudo update-grub
```


Thanks! :D Since i'm in Vista right now, i'll have to reboot into Ubuntu, in order to change the menu.lst...shouldn't be a problem, though, now that I can boot into it with BootIT NG! :guitar:

Cheers! ):P

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
> Do you know  where your XP partition could be?

I believe I answered that in my PM...but just so everyone can see it, i'll go over it again! ;)

My XP partition **still** exists, and is my 6th partition...counting from top to bottom in BootIT NG. The pic of my BootIT NG that i gave in one of my other posts should help...

It is preceded by: #1 a 36MB partition used by BootIT NG for the EMBR (extended master boot record), #2 a former "Recovery" partition, which ended up being overwritten (MY fault!) during the transfer of LVPM, and which became free space...but I recently changed it back to an NTFS partition (same size as before, and the same filesystem type), #3 a 234 GB (if i remember correctly) NTFS partition for Vista, and my default OS, #4 the Linux partition I created for the transfer of my Wubi install, and which is now home for my transferred Ubuntu 8.10, #5 the swap partition for Ubuntu, #6 the 8 MB partition for the BootIT NG program, #7 the XP partition, and finally #8 a recently created Extended partition...formerly free space, but now another partition...don't know yet what i'm going to use it for! ;)

The reason (i think) that Bootpart and the txt file did not show the XP partition (even though it exists, and XP is installed on it), is because XP is not actually in the MBR. This, however, is no real problem for BootIT NG, since it uses a EMBR (extended master boot record), and in **theory** at least, it should be able to boot XP just fine...that is why i don't understand why it doesn't! :lolflag:

I get the "hal.dll" error now, when trying to boot XP, using BootIT NG. I think that that may be due to the fact that my boot.ini file (on XP...not the one on Vista!) has the incorrect partition number entered...or could be perhaps due to the fact that my "ntldr" over on XP doesn't work...the reason why i think that may be the case is because when i copied the boot files over from XP, and tried creating an XP boot entry in the Vista bootloader with EasyBCD, it gave me a message saying the "ntldr" did not exist. So it **sounds** like to me that the file may be corrupt over on XP, but not on Vista (because I replaced the one on Vista with a downloaded version, which worked fine).

Cheers! ):P

EDIT: note that the partition numbering above ^ was meant from the beginning of the drive to the end...in other words, i was speaking about the **first** partition, followed by the **second**, and so on...counting from top to bottom in BootIt NG.

EDIT #2: here's the BootIT NG pic again...so it is easier to view it, and the latest posts at the same time...without having to jump back and forth between pages! ;) See attachment.

EDIT #3: as this is not an updated image, it still shows (what is now an Extended partition at the end of the drive) as free space...that is because I took the pic before creating a partition out of it! Cheers! :D

---

### Post by Jammanuser on 2008-12-20
**Also**...for those of you claiming that XP doesn't exist on my computer, see my attached image of "Computer"! Notice how it says "WinXP" on the D drive right next to C...that would be XP! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: see [http://www.terabyteunlimited.com/kb/category.php?id=52](http://www.terabyteunlimited.com/kb/category.php?id=52) for BootIT NG support. hmm...

---

### Post by meierfra. on 2008-12-20
Sorry, I did not know that BootIt keeps is own partition table independent from the MBR.  I did  a little bit of reading and it seems that  it is not possible to boot XP if it does not appear in  the MBR (because the XP boot loader will  use the partition table in the MBR to locate XP)

But can't you use BootIt to rearrange the partitions so that XP, Vista, Swap and Ubuntu are the first four partitions and so appear in the MBR?
(Keep Ubuntu in the fourth partition, otherwise you will have to edit Menu.lst and reinstall grub).

---

### Post by TeXtonyx on 2008-12-20
Delete

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
> [COLOR="Red"]Sorry, I did not know that BootIt keeps is own partition table independent from the MBR.[/COLOR]  I did  a little bit of reading and it seems that  it is not possible to boot XP if it does not appear in  the MBR (because the XP boot loader will  use the partition table in the MBR to locate XP)

But can't you use BootIt to rearrange the partitions so that XP, Vista, Swap and Ubuntu are the first four partitions and so appear in the MBR?
(Keep Ubuntu in the fourth partition, otherwise you will have to edit Menu.lst and reinstall grub).

You and I both had the same thought...one thing I neglected to mention before is that before I reinstalled BootIT NG, I first deleted the entry in the MBR for the partition for the EMBR (the extended master boot record for BootIT NG) [never should have put it in there, in the first place, come to think of it, since the EMBR is actually another partition table operated **outside** of the standard MBR...that was dumb of me! I don't remember now if it was there in the MBR to begin with when I installed BootIT the first time....most probably it wasn't, and I just placed it in there later, thinking that it needed to be in the MBR to boot from it, which was of course wrong...] and replaced it with XP. Unfortunately, though, when I rebooted the first time after the reboot, I forgot to check if XP was still in the MBR after booting in Vista, and then rebooting again. I just checked it now, and it turns out it **is**! \\:D/

I apologize for all the confusion...no doubt that piece of information would have been helpful in the beginning! And of course that also explains why Vista can now see XP...

I now understand why I wasn't able to boot Ubuntu before from BootIT NG...it appears as if the EMBR in the MBR was affecting the boot process, and preventing Ubuntu from booting. It also explains why XP didn't work, no matter what partition number I tried in boot.ini...

I will now proceed to try out all the different possible partition numbers in boot.ini...and hopefully I will find the correct one, and be able to boot into XP from the Vista bootloader! :guitar:

Cheers! ):P

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
> 
Then in a terminal.

```
sudo update-grub
```

Menu.lst and Grub updated...:guitar:

Thanks! :popcorn:

Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-20
Jammanuser wrote: "I apologize for all the confusion...no doubt 
that piece of information would have been helpful in the beginning! 
And of course that also explains why Vista can now see XP..."

------------------------------------

My guesses are not so good. I would have thought the reason why
Vista can now see XP were, than you forgot to, or chose not to,
hide the Windows partitions in regard to System Restores. But
it seems like now, is a good time to copy any files between them.

---

### Post by Jammanuser on 2008-12-20
> **TeXtonyx said:**
> My guesses are not so good. [COLOR="Red"]I would have thought the reason why
Vista can now see XP were, than you forgot to, or chose not to,
hide the Windows partitions in regard to System Restores.[/COLOR] But
it seems like now, is a good time to copy any files between them.

Indeed...well, now you know the truth! :guitar:

Cheers! :)

Jam man

:popcorn:

---

### Post by abn91c on 2008-12-20
> **Jammanuser said:**
> Here's a copy of what my boot.ini (that i copied over from XP) says:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

```

you seem to be missing this lines on the boot.ini
**[COLOR="Blue"]/noexecute=optin /fastdetect[/COLOR]**(between  windows xp professional and/fast detect)
[COLOR="Blue"]**c:\wubildr.mbr="ubuntu"**[/COLOR]
mine last 2 lines are: multi(0)disk(0)partition(2)\Windows="Microsoft Windows XP Home Edition"
/noexecute=optin /fastdetect
c:\wubildr.mbr="kubuntu"

---

### Post by Jammanuser on 2008-12-20
> **abn91c said:**
> you seem to be missing this lines on the boot.ini
**[COLOR="Blue"]/noexecute=optin /fastdetect[/COLOR]**(between  windows xp professional and/fast detect)
[COLOR="Blue"]**c:\wubildr.mbr="ubuntu"**[/COLOR]
mine last 2 lines are: multi(0)disk(0)partition(2)\Windows="Microsoft Windows XP Home Edition"
/noexecute=optin /fastdetect
c:\wubildr.mbr="kubuntu"

hmm...I was of the understanding that the "/noexecute=optin" was not needed in my case. And of course the "c:\wubildr.mbr" part is to boot kubuntu from your boot.ini...correct?

If I have that wrong, then please correct me! ;)

Cheers! :popcorn:

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-20
Here is my newly-created boot_info_**results**.txt file...**naturally**, this one will mention XP, while the other one didn't! :popcorn:

```
Bootit is installed in the MBR of /dev/sda

sda1:
    File system:  vfat
    Boot sector  type:  XP
    Boot sector  info:  
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2:
    File system:  swap

sda3:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda3 starts at sector 20560325. BootPart in nst_grub-01989DCEF0324D997FFB79052C605827.mbr is trying to chain load sector #506706165 on boot drive #1 BootPart in nst_grub.mbr is trying to chain load sector #506706165 on boot drive #1
    Operating System: Vista
    Boot files/directories present:  /ubuntu/disks/boot/grub/menu.lst /boot.ini /bootmgr /ntldr /ntdetect.com /wubildr.mbr /ubuntu/winboot/wubildr.mbr /boot /ubuntu/disks /ubuntu/disks/boot/ /ubuntu/disks/boot/grub /ubuntu/disks/boot/grub /NST

sda4:
    File system:  ext3
    Boot sector  type:  Grub
    Boot sector  info:  Grub is installed to the boot sector of /dev/sda4 and looks at sector 527464797 of the same hard drive for the stage2 file. (a stage2 file is at this location on /dev/sda) and on partition #4 for menu.lst.
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       556861095   618293654    30716280    c  W95 FAT32 (LBA)
/dev/sda2       547655850   556861094     4602622+  82  Linux swap / Solaris
/dev/sda3        20560325   506706164   243072920    7  HPFS/NTFS
/dev/sda4   *   506706165   547655849    20474842+  83  Linux

Partition table entries are not in disk order
/dev/sda1: LABEL="WINXP-OS" UUID="5BE6-0200" TYPE="vfat" 
/dev/sda2: UUID="94cd6bbb-4b8c-437e-abef-fb744053d906" TYPE="swap" 
/dev/sda3: UUID="2C6EDB496EDB0B0A" LABEL="OS" TYPE="ntfs" 
/dev/sda4: LABEL="Ubuntu-real" UUID="dd4f326a-2165-40f6-aed4-2b44b15b71a5" TYPE="ext3" 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=556861095, size= 61432560, Id= c
/dev/sda2 : start=547655850, size=  9205245, Id=82
/dev/sda3 : start= 20560325, size=486145840, Id= 7
/dev/sda4 : start=506706165, size= 40949685, Id=83, bootable

sda1/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\="Unidentified operating system on drive C." 


sda3/ubuntu/disks/boot/grub/menu.lst

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
# kopt=root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2C6EDB496EDB0B0A loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1



title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



sda3/boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


sda3/boot

total 4172
drwxrwxrwx 1 root root    8192 2008-12-10 21:30 .
drwxrwxrwx 1 root root   12288 2008-12-20 12:29 ..
-rwxrwxrwx 1 root root   28672 2008-12-20 12:52 BCD
-rwxrwxrwx 1 root root  262144 2008-12-10 14:34 BCD.Backup.0001
-rwxrwxrwx 1 root root  262144 2008-12-20 12:17 BCD.LOG
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG1
-rwxrwxrwx 2 root root       0 2008-02-03 16:06 BCD.LOG2
-rwxrwxrwx 1 root root    1024 2008-03-04 09:08 bootfix.bin
-rwxrwxrwx 1 root root 3170304 2008-03-04 09:08 boot.sdi
-rwxrwxrwx 1 root root   65536 2008-02-03 16:06 bootstat.dat
drwxrwxrwx 1 root root       0 2008-02-03 16:06 cs-CZ
drwxrwxrwx 1 root root       0 2008-02-03 16:06 da-DK
drwxrwxrwx 1 root root       0 2008-02-03 16:06 de-DE
drwxrwxrwx 1 root root       0 2008-02-03 16:06 el-GR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 en-US
drwxrwxrwx 1 root root       0 2008-02-03 16:06 es-ES
-rwxrwxrwx 1 root root    2048 2008-03-04 15:05 etfsboot.com
drwxrwxrwx 1 root root       0 2008-02-03 16:06 fi-FI
drwxrwxrwx 1 root root    4096 2008-02-03 16:06 fonts
drwxrwxrwx 1 root root       0 2008-02-03 16:06 fr-FR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 hu-HU
drwxrwxrwx 1 root root       0 2008-02-03 16:06 it-IT
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ja-JP
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ko-KR
-rwxrwxrwx 1 root root  406584 2008-01-20 19:23 memtest.exe
drwxrwxrwx 1 root root       0 2008-02-03 16:06 nb-NO
drwxrwxrwx 1 root root       0 2008-02-03 16:06 nl-NL
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pl-PL
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pt-BR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 pt-PT
-rwxrwxrwx 1 root root   20480 2008-12-10 21:30 Recovery.bcd
-rwxrwxrwx 2 root root   17408 2008-12-10 21:30 Recovery.bcd.LOG
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG1
-rwxrwxrwx 2 root root       0 2008-12-10 21:30 Recovery.bcd.LOG2
drwxrwxrwx 1 root root       0 2008-02-03 16:06 ru-RU
drwxrwxrwx 1 root root       0 2008-02-03 16:06 sv-SE
drwxrwxrwx 1 root root       0 2008-02-03 16:06 tr-TR
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-CN
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-HK
drwxrwxrwx 1 root root       0 2008-02-03 16:06 zh-TW

sda3/ubuntu/disks

total 14648448
drwxrwxrwx 1 root root           0 2008-12-13 00:03 .
drwxrwxrwx 1 root root        4096 2008-12-12 15:54 ..
drwxrwxrwx 1 root root        4096 2008-12-12 17:15 boot
-rwxrwxrwx 2 root root 14000000000 2008-12-15 18:31 root.disk
drwxrwxrwx 1 root root           0 2008-12-12 15:53 shared
-rwxrwxrwx 2 root root  1000000000 2008-12-12 17:10 swap.disk

sda3/ubuntu/disks/boot/

total 13016
drwxrwxrwx 1 root root    4096 2008-12-12 17:15 .
drwxrwxrwx 1 root root       0 2008-12-13 00:03 ..
-rwxrwxrwx 1 root root  503560 2008-10-24 01:55 abi-2.6.27-7-generic
-rwxrwxrwx 1 root root   85316 2008-10-24 01:55 config-2.6.27-7-generic
drwxrwxrwx 1 root root       0 2008-12-12 17:15 grub
-rwxrwxrwx 1 root root 8901816 2008-12-12 17:15 initrd.img-2.6.27-7-generic
-rwxrwxrwx 1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rwxrwxrwx 1 root root 1352144 2008-10-24 01:55 System.map-2.6.27-7-generic
-rwxrwxrwx 1 root root    1130 2008-10-24 01:57 vmcoreinfo-2.6.27-7-generic
-rwxrwxrwx 1 root root 2339712 2008-10-24 01:55 vmlinuz-2.6.27-7-generic

sda3/ubuntu/disks/boot/grub

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

sda3/ubuntu/disks/boot/grub

total 21
drwxrwxrwx 1 root root    0 2008-12-12 17:15 .
drwxrwxrwx 1 root root 4096 2008-12-12 17:15 ..
-rwxrwxrwx 1 root root  191 2008-12-12 17:15 default
-rwxrwxrwx 1 root root   30 2008-12-12 17:15 device.map
-rwxrwxrwx 1 root root 5135 2008-12-15 18:24 menu.lst
-rwxrwxrwx 1 root root 4261 2008-12-12 17:15 menu.lst~

sda3/NST

total 21
drwxrwxrwx 1 root root  4096 2008-12-18 22:24 .
drwxrwxrwx 1 root root 12288 2008-12-20 12:29 ..
-rwxrwxrwx 2 root root   512 2008-12-18 22:24 nst_grub-01989DCEF0324D997FFB79052C605827.mbr
-rwxrwxrwx 1 root root   512 2008-12-15 00:56 nst_grub.mbr

sda4/boot/grub/menu.lst

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
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1







title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,2)
makeactive
chainloader +1
boot


title Windows Vista/Longhorn (loader)
root (hd0,2)
makeactive
chainloader +1
boot


sda4/boot

total 12812
drwxr-xr-x  3 root root    4096 2008-12-15 18:24 .
drwxr-xr-x 21 root root    4096 2008-11-13 05:25 ..
-rwxr-xr-x  1 root root  503560 2008-12-15 18:23 abi-2.6.27-7-generic
-rwxr-xr-x  1 root root   85316 2008-12-15 18:23 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2008-12-20 02:10 grub
-rwxr-xr-x  1 root root 8647292 2008-12-15 18:24 initrd.img-2.6.27-7-generic
-rwxr-xr-x  1 root root  124152 2008-12-15 18:23 memtest86+.bin
-rwxr-xr-x  1 root root 1352144 2008-12-15 18:23 System.map-2.6.27-7-generic
-rwxr-xr-x  1 root root    1130 2008-12-15 18:23 vmcoreinfo-2.6.27-7-generic
-rwxr-xr-x  1 root root 2339712 2008-12-15 18:23 vmlinuz-2.6.27-7-generic

sda4/boot/grub

total 344
drwxr-xr-x 2 root root   4096 2008-12-20 02:10 .
drwxr-xr-x 3 root root   4096 2008-12-15 18:24 ..
-rwxr-xr-x 1 root root    191 2008-12-15 18:23 default
-rwxr-xr-x 1 root root     30 2008-12-15 18:23 device.map
-rwxr-xr-x 1 root root   8108 2008-12-15 18:24 e2fs_stage1_5
-rwxr-xr-x 1 root root   7856 2008-12-15 18:24 fat_stage1_5
-rwxr-xr-x 1 root root   8712 2008-12-15 18:24 jfs_stage1_5
-rwxr-xr-x 1 root root   5223 2008-12-20 02:10 menu.lst
-rw-r--r-- 1 root root   5224 2008-12-20 02:07 menu.lst~
-rwxr-xr-x 1 root root   7352 2008-12-15 18:24 minix_stage1_5
-rwxr-xr-x 1 root root   9756 2008-12-15 18:24 reiserfs_stage1_5
-rwxr-xr-x 1 root root    512 2008-12-15 18:24 stage1
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2
-rwxr-xr-x 1 root root 121460 2008-12-15 18:24 stage2_eltorito
-rwxr-xr-x 1 root root   9556 2008-12-15 18:24 xfs_stage1_5

StdErr Messages 



```

Cheers! :)

Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-20
Ok...here's an update! :popcorn:

I replaced the ntldr file (I knew it was corrupt before, but never bothered to replace it, because I was trying to boot into XP from the Vista bootloader) in XP with the downloaded copy...and i'm no longer getting the hal.dll error! :guitar: I'm now getting the ntoskrnl.exe error, which according to [this link]("http://neosmart.net/wiki/display/EBCD/Troubleshooting+Windows+XP") means the partition number in boot.ini is wrong. I now only have to find the correct partition number, and I should be able to boot into XP fine from BootIT NG! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-20
You posted the wrong  file again. But  to  determine  the correct number for boot.ini  I just need the  output of

```
sudo fdisk -lu
```

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
> You posted the wrong  file again. But  to  determine  the correct number for boot.ini  I just need the  output of

```
sudo fdisk -lu
```

Right...sorry! :redface: That was pretty dumb of me to make the same mistake twice...

It seems I got carried away with happiness that I was finally having success, that I forgot what i was doing...:rolleyes:

I'll go get the other file right away! :guitar:

Cheers!

---

### Post by Jammanuser on 2008-12-20
Problem fixed! :guitar: I just put partition #1 in my boot.ini file in XP, and I can now boot into XP from BootIT NG! :D Once I change the one in Vista, to also say partition (1), then I will be able to boot into it using the Vista bootloader! \\:D/

Cheers! :D :D :D :D

-Jam man

:guitar:

EDIT: of course I got the "stop error" the first time...but only because I had to change the BIOS settings, as the same setting doesn't work for Vista and XP!

---

### Post by abn91c on 2008-12-20
> **Jammanuser said:**
> hmm...I was of the understanding that the "/noexecute=optin" was not needed in my case. And of course the "c:\wubildr.mbr" part is to boot kubuntu from your boot.ini...correct?

If I have that wrong, then please correct me! ;)

Cheers! :popcorn:

Jam man

:guitar:
your probably should say ubuntu instead, that is what my Xp/kubuntu boot.ini shows, when i reboot grub shows xp as default with 15 seconds timer and kubuntu below, but only because I choose Kubuntu as my default GUI(I have ubuntu installed also)

---

### Post by Jammanuser on 2008-12-20
Ok...I just modified my post to display the boot_info_**results**.txt file this time, instead of the boot_info_**script**.txt file! :D

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-20
It seems I wont be able to boot into XP from the Vista bootloader...due to the same BIOS settings not working for both OSes! :( I just thought of that...I already know that when I try to boot into XP from the Vista bootloader, i'll get the same **unstoppable** "stop error" :), and I wont be able to change the BIOS settings without locking myself from the Vista bootloader...:(

Hopefully someone can come up with a workaround or fix to this problem! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-20
Edit:  I didn't see your latest post until after I posted this. Make the three changes suggested below, and we will worry about the bios later.


Your boot.ini needs to use "partition(1)". Change the boot.ini in your XP partition and in the Vista partition.
 
I noticed a couple of more potential problems:


1)  You  have two different "ntldr" on your XP partition:  "ntldr" and "NTLDR". Rename one of them, if that does  not work undo the renaming and  rename the other one.


2)  Your XP boot.ini says "C:\="Unidentified operating system on drive C." 

This usually  happens if you  install XP on   a "vfat" partition  created with linux. It means that your boot XP sector is slightly corrupted. This can be fixed with testdisk from an ubuntu terminal:


```

sudo apt-get install testdisk
sudo testdisk /dev/sda
```

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"

If it reports that the rebuild boot sector is not identical, choose "write". Then press "q" a few times to quit testdisk

---

### Post by TeXtonyx on 2008-12-20
> **Jammanuser said:**
> Ok...I just modified my post to display the boot_info_**results**.txt file this time, instead of the boot_info_**script**.txt file! :D

Cheers! :)

-Jam man 

This is the new fdisk result:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       556861095   618293654    30716280    c  W95 FAT32 (LBA) <---
/dev/sda2       547655850   556861094     4602622+  82  Linux swap / Solaris
/dev/sda3        20560325   506706164   243072920    7  HPFS/NTFS
/dev/sda4   *   506706165   547655849    20474842+  83  Linux

-------------------------------------------------------------

sda1 means first drive, first partition, so that agrees with
your change to boot.ini, partition(1) the first Windows primary.

The odd thing is that sda1 used to show the Bootit partition 
which was 39mb or so and was reported as fat16. But since
Bootit is still working, I suppose it must be hidden.

--------------------------------------------------------
fdisk report from post #26 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           5       40131    6  FAT16 
/dev/sda2           34664       38487    30716280    c  W95 FAT32 (LBA) 

---------------------------------------
The screenshot from Gparted in post #44 agrees with the below,

fdisk report from post #64 (different in size and system)
Device Boot      Start         End      Blocks   Id  System
/dev/sda1           63       80324       40131    6  FAT16 <---

--------------------------------------

I guess the small fat16 Bootit partition shows up in the complete
Bootit Boot Menu display.

---

### Post by Jammanuser on 2008-12-20
> **meierfra. said:**
>  Your boot.ini needs to use "partition(1)". Change the boot.ini in your XP partition and in the Vista partition.

Already done...:guitar:
 


> **meierfra. said:**
> 
I noticed a couple of more potential problems:

1)  You  have two different "ntldr" on your XP partition:  "ntldr" and "NTLDR". Rename one of them, if that does  not work undo the renaming and  rename the other one.


I DO? :confused: Are you sure about this? I just checked (from Ubuntu) my XP partition, and I see only one ntldr...and that is "ntldr" and not "NTLDR". I don't see another one...
> **meierfra. said:**
> 
2)  Your XP boot.ini says "C:\="Unidentified operating system on drive C." 


Right! I have already removed that line from my XP boot.ini...along with the extra line right above it! :guitar: Now when I boot into XP it goes straight to the XP screen, instead of to the XP bootloader menu, like it did previously, in which was previously 2 different entries for XP, along with the "unidentified OS on C"...:)

Cheers! :)

-Jam man

:guitar:

P.S. I will run those commands anyway, like you said, just to verify that there are no more problems on the XP partition...Cheers!

---

### Post by Jammanuser on 2008-12-20
> **TeXtonyx said:**
> 
The odd thing is that sda1 used to show the Bootit partition 
which was 39mb or so and was reported as fat16. But since
Bootit is still working, I suppose it must be hidden.


That is because I replaced the entry for the EMBR in the MBR, with the XP entry! ;) The 36 MB partition, though, was the EMBR partition, NOT the partition that BootIT NG is actually installed on...**that** partition is also not in the MBR, since there's no need for it to be, and it is the partition right below the XP one, looking at the BootIT NG window! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-20
> **TeXtonyx said:**
> 
I guess the small fat16 Bootit partition shows up in the complete
Bootit Boot Menu display.

The **default boot menu**  of BootIT NG and the **Partition Work** window are **two** different things! :) The pic of BootIT NG that I gave shows the Partition Work window, not the default menu...and of course naturally, the small BootIT partition does indeed show up in that. But its not in the Default menu, because that's where you boot from, and you can't boot from the partition that BootIT NG is installed on! :guitar:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-20
> Already done

Oops, I had looked  at post #90 and responded to that. Only now I realizes that you had a couple of post before that, which  I hadn't seen.


> I DO? Are you sure about this? I just checked (from Ubuntu) my XP partition, and I see only one ntldr...and that is "ntldr" and not "NTLDR". I don't see another one...

Seems to be a bug in my script.  The results you posted say:

 Boot files/directories present:  /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

I have to admit, I never tested it on a Fat partition.


> It seems I wont be able to boot into XP from the Vista bootloader...due to the same BIOS settings not working for both OSes


Sorry, I don't know much about bios. I suggest to start a new thread on the subject and provide some informations about the different BIOS setting you have to use.


Did you run testdisk yet?  Since your are able to boot  into XP,  the rebuild boot sector is probably identical  with your current  boot sector.

---

### Post by TeXtonyx on 2008-12-20
> **Jammanuser said:**
> That is because I replaced the entry for the EMBR in the MBR, with the XP entry! ;) The 36 MB partition, though, was the EMBR partition, NOT the partition that BootIT NG is actually installed on...**that** partition is also not in the MBR, since there's no need for it to be, and it is the partition right below the XP one, looking at the BootIT NG window! :)

Cheers! :popcorn:

-Jam man

The hard drive is a physical device. Information is stored in
electro-magnetic configurations on the sectors of the hard drive
which amount to an area (technically is has depth). The MBR is

The MBR is a 512 byte segment on the very first sector ("LBA Sector 0")  
of your hard drive composed of three parts: 1) the boot code which is 
446 bytes long, 2) the partiton table which is 64 btyes long, and 3) 
the boot code signature which is 2 bytes long. 

So it is at the front of the drive and it's a stretch to think
of the MBR as within a partition. The EMBR, which you mentioned,
means Extended Master Boot Record and is also very small and it
does not have its own partition. It's possible to backup the
embr into the fat16 partition which is the Bootit partition.
When you boot Bootit into Maintenance mode, the utilities that
it accesses are all stored in that 36 or 39 mb Bootit partition.
Backing up the embr and several Bootit Ng files all fit on a
1.44mb floppy.

I'm gonna quote this article from TeraByte because it reveals
some information about the size of the embr. It says when you
overwrite the MBR with grub, sometimes you overwrite the embr
which means the embr is small and contiguous. Grub is not diving
into some partition and damaging the embr. 

Maybe you're not interested in reading the article, so I'll close
with something else. I can see from my screenshot that Booit NG
is not listed on it, "The Direct Boot Menu displays all enabled
partition--" I think that screenshot shows a much clearer picture
of what is actually enabled to boot, Vista, XP or Ubuntu, than
the Partition Work screen, which I think shows what is available.

I used to use Bootit when it was still free. I had to complain
on the Bootit forum to provide documentation on how to hide and
unhide different Windows OS, before Vista. The documentation is
the antonym of perspicuity. I didn't mean just for you, but for
everybody on this forum no matter if they have a 99+ reading 
comprehension level, years of experience, and a college degree
in computers. People who are too young to have that background
are mostly likely doomed to wander through it making mistakes.


[http://www.terabyteunlimited.com/kb/article.php?id=231](http://www.terabyteunlimited.com/kb/article.php?id=231)
Section 2 - The EMBR has also been overwritten:

"If you are not offered the option to Reactivate BootIt NG when booting 
from the installation disk, this means that GRUB has also overwritten 
the EMBR area on HD0, and that you will need to install BootIt NG again. 
In this case, you will be presented with the BootIt NG Setup prompt, as 
if it had never been installed. From there, it is suggested that you 
follow the procedure below to recover.

Note: If you have a current backup of the EMBR on HD0 (as saved from 
the Backup dialog on the BootIt NG desktop), you can also restore that 
instead of following the steps in this section. A current backup means 
that no partition structure changes have been made on HD0 since the 
EMBR backup was made. If there is any doubt about the EMBR backup being 
current, you are best advised to follow the procedure below.

1. Before installing BootIt NG again, it is suggested that you first 
install GRUB to the Linux root partition, so that you can later boot 
Linux from BootIt NG. This can also be done after the fact, but it is 
usually easier to do it while GRUB is still in the MBR. To do that, 
reboot your system from the hard drive and let GRUB boot into Linux. 
Then, as root, run the following command:

grub-install  /dev/hdxx    
(where hdxx is your root partition, such as hda1, hda2, etc.)

2. Boot your system again from the BootIt NG installation disk, 
which will get you back to the Setup prompt to install BootIt NG. 
Click OK to proceed with the installation.

3. If your BootIt NG installation was limiting primaries 
(to 4 or less per drive),  click No when asked if you would like 
to support more than 4 primary partitions. Otherwise, click Yes."

---

### Post by Jammanuser on 2008-12-21
Just edited my NeoGrub menu.lst file...it would be appreciated if someone would take a look at it, and see if I did everything right! ;)

Here it is:

```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD


#This is a comment. Comments are prefixed with a '#'

default 0		#Pick the task to be run if the user doesn't pick one within the time limit.
timeout 10		#Give the user 10 seconds to choose a task.

#We use the "title" keyword to indicate a new entry in the menu.

title 		Windows XP	#This is our first entry - it's number 0
find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.
makeactive  			#Make this the active partition
chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader
#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.

#This is our second entry
title		Ubuntu Linux    
root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.
#Next Line: Translate (hd0,3) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda4
initrd		/boot/initrd.img-2.6.22-14-generic
#End Ubuntu entry

#That's it!
```

**Obviously,** this is the multi.entry version...this can not be helped, since I simply copied and pasted from the link Meierfra gave to me, and I needed one that would be able to boot Ubuntu, and the single entry example on that page had only the info to boot XP...:)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
>  [COLOR="Red"]Did you run testdisk yet?[/COLOR]  Since your are able to boot  into XP,  the rebuild boot sector is probably identical  with your current  boot sector.

Not yet. I've been busy doing things in the real world up until just a few minutes ago, and I wanted to work on the NeoGrub thing first...and of course that can only be done in Vista, which means I have to first reboot, and then boot into Ubuntu in order to run testdisk! ;)

Cheers, though! I WILL! :)

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-21
> Just edited my NeoGrub menu.lst file...it would be appreciated if someone would take a look at it, and see if I did everything right

Everything looks fine but you seem to be using the wrong kernel version. Use this:


#This is our second entry
title		Ubuntu Linux    
root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.
#Next Line: Translate (hd0,3) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro
initrd		/boot/initrd.img-2.6.27-7-generic
#End Ubuntu entry

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> Make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```


sudo apt-get install testdisk
sudo testdisk


```



I made sure it was enabled, in Software Sources, but when I tried to install it using "sudo apt-get install testdisk", I received the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  testdisk: Depends: libntfs10 (>= 2.0.0) but it is not installable
E: Broken packages

```

I went to synaptic, and tried to find libntfs10, but it didn't show up in the Quick Search box. I found a couple things similar in name though when i left off the "10" part..."libntfs-gnomevfs", and "libntfs-3g28".

Should i install one of them instead? if so, which one? 

Looking forward to your reply...

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> [COLOR="Red"]Everything looks fine but you seem to be using the wrong kernel version.[/COLOR] Use this:


#This is our second entry
title		Ubuntu Linux    
root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.
#Next Line: Translate (hd0,3) to Linux notation and set that as the root partition
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro
initrd		/boot/initrd.img-2.6.27-7-generic
#End Ubuntu entry



kernel		/boot/vmlinuz-2.6.27-7-generic

Alright...affirmative! I actually suspected this...but I wanted to hear it from someone here! ;)

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> Everything looks fine but you seem to be using the wrong kernel version.

Kernel changed! :guitar:

Hopefully now I will be able to boot into Ubuntu from my Vista bootloader, using NeoGrub...:popcorn:

Cheers! :)

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-21
"Not yet. I've been busy doing things in the real world up until just 
a few minutes ago, and I wanted to work on the NeoGrub thing first"

That seems like a productive approach and I wish I knew more about
it. [http://forums.techarena.in/vista-setup-install/755927.htm](http://forums.techarena.in/vista-setup-install/755927.htm)

 Using NeoGrub to hide Vista partition in XP
"I'm using EasyBCD to dual-boot between Windows Vista and XP. 
There's an option in EasyBCD to install NeoGrub, which I understand 
has the ability to hide the Windows Vista partition when booting 
into XP. Consequently, XP would not then delete the Vista 
restore points."

Reply: A good place to ask: [http://neosmart.net/forums/](http://neosmart.net/forums/)

TeX: I'll look around there.

---

### Post by meierfra. on 2008-12-21
First time I see somebody having problems with installing testdisk. Try this

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install testdisk
sudo testdisk
```


If this does not help post

```
cat /etc/apt/sources.list 
```

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> First time I see somebody having problems with installing testdisk. Try this

```

sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```


If this does not help post

```
cat /etc/apt/sources.list 
```

Nope...didn't help! I still get the same output in my terminal...:(

Here's the output for "cat /etc/apt/sources.list":

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted multiverse universe

```

---

### Post by meierfra. on 2008-12-21
I edited my last post ( i  left out a line)  Try again  while I'll look over your sources.list.

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> I edited my last post ( i  left out a line)  Try again  while I'll look over your sources.list.

Right...i had already noticed that before this post, and immediately changed that section of my NeoGrub menu.lst file to mirror what you wrote! ;)

Thanks! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
Here's my updated NeoGrub menu.lst file, to prevent confusion:

```
# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# http://neosmart.net/wiki/display/EBCD





#This is a comment. Comments are prefixed with a '#'



default 0		#Pick the task to be run if the user doesn't pick one within the time limit.

timeout 10		#Give the user 10 seconds to choose a task.



#We use the "title" keyword to indicate a new entry in the menu.



title 		Windows XP	#This is our first entry - it's number 0

find --set-root	/NTLDR  	#Search for NTLDR on all partitions. Once found, use that partition as root.

makeactive  			#Make this the active partition

chainloader /NTLDR		#Run NTLDR, the Windows XP bootloader

#If we're using a menu, we don't need to use the `boot` command - it's automatically implied.



#This is our second entry

title		Ubuntu Linux    

root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.

#Next Line: Translate (hd0,3) to Linux notation and set that as the root partition

kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro

initrd		/boot/initrd.img-2.6.27-7-generic

#End Ubuntu entry


#That's it!
```

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-21
Your  grub menu looks fine, but I would remove all whose  blank lines. 


The last part of your sources.lst is messed up. Back it up and then replace it with

```

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

Then run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by Jammanuser on 2008-12-21
Now when I try to boot into Ubuntu, using NeoGrub, i get the following error:

```
Booting 'Ubuntu Linux'

root (hd0,3)    #Load Ubuntu from the 1st harddrive, 3rd partition.

Warning: Unrecognised partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool (err=8). Current C/H/S=16383/255/63
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda4 ro

Warning: Unrecognised partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool (err=8). Current C/H/S=16383/255/63

Error 2: Bad file or directory type

Press any key to continue...
```

It seems like something is wrong in my NeoGrub menu.lst file...:confused:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> The last part of your sources.lst is messed up. Back it up and then replace it with...


How do I edit it? I copied it from the terminal, and no file was opened when i ran that command...:confused:

EDIT: never mind...i found it by browsing to it with the file browser! Cheers! :D

EDIT #2: Hello...when I try to open the file, it opens up the Software Sources! :confused: I thought the file itself was supposed to open when I clicked on it...:)

---

### Post by meierfra. on 2008-12-21
> Error 2: Bad file or directory type

Sorry, I did know this. NeoGrub has not been updated in a while and cannot  handle the  256 inodes ext3 file system used by Intrepid.
You can get a newer version from Grub4Dos. I'll do some research  do figure out the easiest way to this.


> Hello...when I try to open the file, it opens up the Software Sources
You probably can achieve the same thing from Software souces by enabling the security repositories.

Or 

```
cd /etc/apt
sudo mv sources.list sources.list.bu
gksudo gedit  sources.list
```

This should open a blank file. Just copy and paste the sources.list I posted and save the file.

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> 
```
cd /etc/apt
sudo mv sources.list sources.list.bu
gksudo gedit  sources.list
```

This should open a blank file. Just copy and paste the sources.list I posted and save the file.

Thanks! :) It worked perfectly...now i'm in the process of performing the upgrade. Once that completes, I'll try to run test disk again, and let u know if it works or not! :popcorn:

Cheers! :guitar:

---

### Post by meierfra. on 2008-12-21
There are (at least) two ways to solve your NeoGrub problem:

1)  Use this for your Ubuntu item in the NeoGrub menu.lst:

title		Ubuntu Linux    
root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.
chainloader +1
#End Ubuntu entry

If you choose "Ubuntu Linux" at the NeoGrub menu,  the Grub menu from  Ubuntu  will appear. But  if you change

"#hiddenmenu" to "hiddenmenu"

and 

"timeout 10" to  "timeout 2"

in your Ubuntu menu.lst, you will not even noticed the second Grub menu. This method has the advantage that you won't have to   edit your NeoGrub menu.lst after Ubuntu kernel updates.

 
2)  In Vista, download the latest version of Grub4Dos from[URL="http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-11-19.zip"] here
[/URL]
Open the folder C:\NST.
Rename "NeoGrub.mbr" to "NeoGrubBu.mbr"
Unzip the  file you downloaded. This will create a folder with the name grub4dos-0.4.4. In there you will find  files with the names "grldr" and "grldr.mbr" 
Copy "grldr.mbr" to  C:\NST and rename it to "NeoGrub.mbr.
Copy "grldr" to C:\.
Move your NeoGrub  menu.lst (it should be in C:\NST) to C:\

---

### Post by TeXtonyx on 2008-12-21
Quote:
Error 2: Bad file or directory type
-------------------
meierfra wrote:
"Sorry, I did know this. NeoGrub has not been updated in a while and cannot handle the 256 inodes ext3 file system used by Intrepid."
----------------------------------------

I've heard about this 128 to 256 problem, I think with a video
driver. But anyway, I have 8.10 on my second drive, and I boot
it with Bootpart. I think that means that after he got Ubuntu
to boot from Bootit, that the more usual (bootpart) way of using 
Easybcd's method of adding Intrepid (sda4) may work if Neogrub 
doesn't. Maybe delete his current entry and add it in again. 

And perhaps putting XP into the Ubuntu menu.lst would also
be more likely to work after he was able to boot XP in Bootit.

---

### Post by meierfra. on 2008-12-21
>  I think that means that after he got Ubuntu
to boot from Bootit, that the more usual (bootpart) way of using
Easybcd's method of adding Intrepid (sda4) may work if Neogrub
doesn't. Maybe delete his current entry and add it in again. 

I doubt it. Nothing in the relation between bootpart and Ubuntu has changed.  Also the boot part code is already pointing to the correct sector:  (see post #84)

> BootPart in nst_grub-01989DCEF0324D997FFB79052C605827.mbr is trying to chain load sector #506706165 on boot drive #1 

BootPart in nst_grub.mbr is trying to chain load sector #506706165 on boot drive #1

/dev/sda4   *   506706165   547655849    20474842+  83  Linux


But  I can't rule it out, since I do not understand why bootpart failed. Also there are  4 bytes in the dynamic part of the bootpart code which I don't understand.
So it's worth a try.


> And perhaps putting XP into the Ubuntu menu.lst would also
be more likely to work after he was able to boot XP in Bootit. 

I'm almost certain that this will work. Just use 

title Windows XP
root (hd0,0)
chainloader +1

in the Ubuntu menu.lst.

---

### Post by TeXtonyx on 2008-12-21
meierfra wrote:"But I can't rule it out, since I do not understand 
why bootpart failed." 

---------------------------

Neither do I, but of course I understand Windows better than this
side anyway. Jammanuser said that the Ubuntu partition started as
a Wubi partition. I know the least about this process. Does Wubi
have a UUID and does it get changed when its moved to sda4? I'm
just grasping at straws since I couldn't think of anything at all. 

I read about grub4dos because caljohnsmith recommended it and it
seemed a lot better than System Commander of the good old days.

---

### Post by Jammanuser on 2008-12-21
> **Jammanuser said:**
> Thanks! :) It worked perfectly...now i'm in the process of performing the upgrade. Once that completes, I'll try to run test disk again, and let u know if it works or not! :popcorn:

Cheers! :guitar:

Nope. Still didn't work...:( When I try to install testdisk, i get the same message saying that it depends on libntfs10, which is not installable...:confused:

I finished the upgrade and update before trying to install testdisk...but it didn't help. It looks like I wont be able to run testdisk after all...

---

### Post by meierfra. on 2008-12-21
> It looks like I wont be able to run testdisk after all...

No big deal.  Did you see my post #116?  I recommend the first method.

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> No big deal.  Did you see my post #116?  I recommend the first method.

Oh, sorry! I missed that post...:)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> 

Use this for your Ubuntu item in the NeoGrub menu.lst:

title		Ubuntu Linux    
root		(hd0,3)   	#Load Ubuntu from the 1st harddrive's 3rd partition.
chainloader +1
#End Ubuntu entry



But shouldn't it mention the kernel...or is that automatically included when you add "chainloader +1"? ;) 

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
Here's my updated Ubuntu menu.lst...would appreciate if you would take a look at it, to make sure everything is correct, after I edited it...;) 

```
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
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,3)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1







title Ubuntu-on-/dev/sda1
root (hd0,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sda4
root (hd0,3)
configfile /boot/grub/menu.lst



# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows
root (hd0,2)
makeactive
chainloader +1
boot


title Windows Vista/Longhorn (loader)
root (hd0,2)
makeactive
chainloader +1
boot
```


Thanks for all your help! ):P

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
>  I'm almost certain that this will work. Just use 

title Windows XP
root (hd0,0)
chainloader +1

in the Ubuntu menu.lst.

Thanks...but where exactly do I put it? Do I replace one of the boot entries in my menu.lst with this or simply add it? if so, where?

Looking forward to your reply...:)

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-21
> 
[QUOTE]
Use this for your Ubuntu item in the NeoGrub menu.lst:

title Ubuntu Linux
root (hd0,3) #Load Ubuntu from the 1st harddrive's 3rd partition.
chainloader +1
#End Ubuntu entry

But shouldn't it mention the kernel...or is that automatically included when you add "chainloader +1"?
[/QUOTE]

It does not need the kernel information. It just  executes the code in the boot sector of (hd0,3) (=/dev/sda4). And since Grub is installed in the boot sector of /dev/sda4, the Grub menu  from Ubuntu will appear.


> Here's my updated Ubuntu menu.lst...would appreciate if you would take a look at it, to make sure everything is correct, after I edited it

> Thanks...but where exactly do I put it? Do I replace one of the boot entries in my menu.lst with this or simply add it? if so, where?


I insert the Windows entry```

```, and cleaned up your Ubuntu menu.lst:
```
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
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dd4f326a-2165-40f6-aed4-2b44b15b71a5  ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


title Windows XP
root (hd0,0)
chainloader +1


title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1

```

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> It does not need the kernel information. It just  executes the code in the boot sector of (hd0,3) (=/dev/sda4). And since Grub is installed in the boot sector of /dev/sda4, the Grub menu  from Ubuntu will appear.


Ok then...Thanks! :D :D 

> **meierfra. said:**
> 
I insert the Windows entry```

```, and cleaned up your Ubuntu menu.lst...


Ok...I replaced completely the text in my Ubuntu menu.lst with the text you gave! :) So I hope that there are no errors in it...;)

**Much** appreciation! I will now reboot and see if I can boot into Ubuntu, using NeoGrub, and see if I can boot into XP from my Grub... :)

I'll let you know if it works or not! :popcorn:

Cheers! ):P

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-21
I forget to mention: since you changed "#hiddenmenu" to "hiddenmenu" you will have the press "Esc" to bring up Ubuntu's Grub menu (otherwise it should boot automatically into Ubuntu)

---

### Post by Jammanuser on 2008-12-21
> **TeXtonyx said:**
> 
[COLOR="Red"]So it is at the front of the drive and it's a stretch to think
of the MBR as within a partition.[/COLOR] The EMBR, which you mentioned,
means Extended Master Boot Record and is also very small and it
does not have its own partition. It's possible to backup the
embr into the fat16 partition which is the Bootit partition.
When you boot Bootit into Maintenance mode, the utilities that
it accesses are all stored in that 36 or 39 mb Bootit partition.
Backing up the embr and several Bootit Ng files all fit on a
1.44mb floppy.


The MBR is not within a partition...the **EMBR** is! :) The EMBR was placed on the first partition of my hard drive...hence the labeling name "EMBR"! Of course, it is very small, like you said, but it is placed on the first partition of the hard drive, when you create it at the BootIT NG installation...this i know from experience! ;)

The EMBR is **not** in my BootIT NG partition...**that** partition is #7 if you look at the BootIT NG pic, and count from top to bottom. The EMBR is always placed at the front of the drive, first partition...if you take a look at the BootIT NG manual. Of course the size of the partition that EMBR is installed on is of little consequence...**obviously**, the partition does not have to be as big as it is currently, i.e. 36 MBs, but that is simply the size that the partition was originally, before installing BootIT NG, as it originally housed a Dell Utility tool by factory default, but I didn't feel like changing the size, so I let it be...:lolflag:

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
> **meierfra. said:**
> I forget to mention: since you changed "#hiddenmenu" to "hiddenmenu" you will have the press "Esc" to bring up Ubuntu's Grub menu (otherwise it should boot automatically into Ubuntu)

Ok...thanks! :D I'll go check it right now, to see if I can boot into Ubuntu that way...

Cheers! 

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-21
woohoo! it WORKED!!! :grin: \\:D/ =D> :twisted:

I just tried booting into Ubuntu with NeoGrub, and it WORKED! :guitar: 

Thank you SO much, Meierfra and TeX!!! 

I now have a working tri-boot with Windows Vista, XP, and Ubuntu 8.10! \\:D/

I can now boot into any of the 3 using BootIT NG, and can also boot into any of them from the Vista bootloader, using NeoGrub, as well!

Thank y'all so much! 

Now if only I can get the BIOS settings problem worked out...

Cheers! :)

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-22
Now that I have successfully managed to tri-boot using BootIT NG, i will try to write a full-length tutorial on the process for others who might have trouble figuring it out! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-22
> **meierfra. said:**
> I doubt it. Nothing in the relation between bootpart and Ubuntu has changed.  Also the boot part code is already pointing to the correct sector:  (see post #84)


I was looking over all the previous posts on this thread, and I came across this post, and wanted to clear it up...;) The entry in my Vista bootloader created by EasyBCD for XP does indeed work now...I didn't have to delete it and create another one though, in answer to TeX's post....the old one works fine. I guess all that was preventing it from working before was the wrong partition number in my boot.ini in Vista...and of course the fact that XP didn't exist at the time in my MBR! Now that I have partition (1) in both of my boot.ini files...i.e. the one in Vista, and the native one in XP, it now boots fine (excluding of course the BSOD problem!:)) from my Vista bootloader, using the entry for XP created by EasyBCD.

Just wanted to clear that part up! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by meierfra. on 2008-12-22
> [QUOTE]
I doubt it. Nothing in the relation between bootpart and Ubuntu has changed. Also the boot part code is already pointing to the correct sector: (see post #84)
I was looking over all the previous posts on this thread, and I came across this post, and wanted to clear it up... The entry in my Vista bootloader created by EasyBCD for XP does indeed work now...I didn't have to delete it and create another one though, in answer to TeX's post....the old one works fine.[/QUOTE]

But  Tex and I were talking about your  EasyBCD entry for Ubuntu via bootpart.  (bootpart is not used to  boot XP)

---

### Post by TeXtonyx on 2008-12-22
> **meierfra. said:**
> But  Tex and I were talking about your  EasyBCD entry for Ubuntu via bootpart.  (bootpart is not used to  boot XP)

Early in the thread I noticed an error message from Easybcd that
was generated by the Bootpart mechanism that Easybcd uses. So
if there is something which could be wrong, like picking the wrong
setting for Ubuntu when one creates the entry with Easybcd, I 
always eliminate potential problems like that if it is very quick
to do, even if it is only a 1 in 20 shot of being the problem cause.

Troubleshooting is a balance between time needed to try a fix,
balanced with the liklihood that a possible fix matches with the
cause of the problem, which is an art, imo, Jammanuser. Out of say 
10 possible causes for an error, you only know the precisely shortest 
steps, or order of the troubleshooting, after the fact, there's a guess.

Also early the right partition for XP was unknown. So I showed
him a portion of my boot.ini for illustration. It contained
at the tail, my entry to boot Ubuntu using bootpart. I use 
bootpart for XP to boot Ubuntu which boot Vista. Its because
I like XP Pro better than Vista except for Aero, and I try
different Linux OS which I always install to the /boot partition.
Using bootpart at the command line to add an entry automatically
for boot.ini and create a linux.bin is faster than doing the
same thing with with Easybcd in Vista. 

Anyway, I have seen the error message that he got from the
Bootpart aspect of Easybcd and knew it could arise from from
a partition boundary changing. There was enough uncertainty at
that point (also moving Wubi) that I thought it would be better
to play it safe. I actually think its better to uninstall and
reinstall a fast program like Easybcd because when you just
remove a boot entry, it's hard to say how deeply removed it is.
At the least I thought, he should uninstall and reinstall all
entries including the one for XP (it wasn't booting).

Since we're clearing small issues, Jammanuser would say that
Vista was in the MBR; he meant that Vista was selected to be
shown as one OS in the Bootit EMBR settings for what was in
the MBR (actually I think trading its partition table). I OTOH,
though when he said Vista in the MBR meant the standard meaning
of the first 512 bytes of the drive were owned by Vista.

Easybcd has two ways of adding Linux. The one which uses bootpart 
and the other one which uses neogrub. I never did understand why the 
neogrub method worked but the bootpart method didn't. I think its closest 
to true to say that ntldr boots XP though it uses two other files.(?)

---

### Post by Jammanuser on 2008-12-23
> **meierfra. said:**
> But  Tex and I were talking about your  EasyBCD entry for Ubuntu via bootpart.  (bootpart is not used to  boot XP)

Oh! :shock: Then in that case...Ok! :) I thought you meant the XP entry...alright! I understand it now! :lolflag: And of course, like you said, the entry for Ubuntu created by EasyBCD still does not work...I guess there still is a problem with Bootpart, after all! ;)

Cheers! :redface:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-23
> **TeXtonyx said:**
> Early in the thread I noticed an error message from Easybcd that
was generated by the Bootpart mechanism that Easybcd uses. So
if there is something which could be wrong, [COLOR="Red"]like picking the wrong
setting for Ubuntu when one creates the entry with Easybcd[/COLOR], I 
always eliminate potential problems like that if it is very quick
to do, even if it is only a 1 in 20 shot of being the problem cause.


hmm...[-X See my attached images of the EasyBCD window, with the Ubuntu entry created by EasyBCD...and then tell me I did something wrong! :) Notice how the last screenshot shows the same file opened that the bootloader path in EasyBCD points to, and how that in the first screenshot, it shows that the correct partition was selected to boot the Ubuntu entry from...i.e. the 20 GB Linux native partition that Ubuntu 8.10 is installed on.

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> hmm...[-X See my attached images of the EasyBCD window, with the Ubuntu entry created by EasyBCD...and then tell me I did something wrong! :) Notice how the last screenshot shows the same file opened that the bootloader path in EasyBCD points to, and how that in the first screenshot, it shows that the correct partition was selected to boot the Ubuntu entry from...i.e. the 20 GB Linux native partition that Ubuntu 8.10 is installed on.

Cheers! :lolflag:

----------------------------------------------

I make an effort to word my posts accurately so I will quote me,

"So if there is something which could be wrong, like picking 
the wrong setting for Ubuntu when one creates the entry with 
Easybcd, I always eliminate potential problems like that if it 
is very quick to do, even if it is only a 1 in 20 shot of being 
the problem cause."

Notice that I said *could*. I did not accuse you of making a
mistake. I actually thought that using the wrong setting was
better than a 50/50 shot of being the cause of the problem, but
my statement is true even if it is 1 in 20 because its so quick.

I am attaching a screenshot of your screenshot because it looks
to me like there is an error there.  Notice where it says,

Drive:  Partition 3 (Linux native -20GB

I think Partition 3 is sda3 and I think all of your fdisk reports
have shown that Ubuntu is installed on sda4, Partition 4.

Post #26 /dev/sda4   31542       34090    20474842+  83  Linux 
Post #44 Gparted shows sda4, and Bootit shows 4th in the order

Post #48 your later edit showing Bootpart output

Physical number of disk 0: 3c5a8d58
0: C: type=6 <BIGDOS FAT 16>, size= 40131 KB, LBA Pos=63
1: C: type=82 <Linux swap>, size= 4602622 KB, LBA Pos=547655850
2: C: type=7 <HPFS/NTFS>, size= 243072920 KB, LBA Pos=20560325
3: C: type=83 <Linux native>, size= 20474842 KB, LBA Pos=50670615

TeX: The number is given as 3 but that is the 4th partition,
because the numbering starts at 0. 0,1,2,3, = 4 partitions

Post #63  sda4: File system:  ext3 <--[that means Linux native]
Post #84  sda4: File system:  ext3

Post #99 
title		Ubuntu Linux    
root		(hd0,3)   	
#Load Ubuntu from the 1st harddrive's 3rd partition. <----***

I seldom critique/comment on grub posts. I've explained the
difference between grub and fdisk style reports regarding 
partition numbers. So your above #comment is mistaken.
root (hd0,3) works because (hd0,3) = sda4, the 4th partition.
The grub partition numbers are one lower than fdisk numbers.
(hd0,x) corresponds to sdax where x is the partition number. 
But the x value in (hd0,x) is one number lower than the x value in sdax.
Anyway, the Easybcd/bootpart error message happened before #99.

I can't tell what other choices that Easybcd offered in your 1st
screenshot. Perhaps you picked Partiton 3 because it was the
only choice offered; but you failed to notice it was incorrect.
Those things happen along with typos. That is why I've learned
to eliminate/simplify any area which could go wrong, and to
uninstall/reinstall in quick situations like this out of good habit.

---

### Post by TeXtonyx on 2008-12-23
I won't expect a quick admission of culpability, I see you've 
finished downloading the Dell Studio 1535 XP drivers and are no 
doubt busy. ;)

---

### Post by TeXtonyx on 2008-12-23
> **Jammanuser said:**
> hmm...[-X See my attached images of the EasyBCD window, with the Ubuntu entry created by EasyBCD...and then tell me I did something wrong! :) Notice how the last screenshot shows the same file opened that the bootloader path in EasyBCD points to, and how that in the first screenshot, it shows that the correct partition was selected to boot the Ubuntu entry from...i.e. the 20 GB Linux native partition that Ubuntu 8.10 is installed on.

Cheers! :lolflag:

------------------------------------------------------

In thread, Re: Help! no GRUB! :s Post #43
Originally Posted by northern lights  
sda4 translates to (hd1,3) and sda5 to (hd1,4) in GRUB syntax. (hd1,5) is 
your swap partition. Hence the "invalid device"

Jammanuser corrected the post of northern lights by saying,
"Wouldn't it be (hd0,3)? I think that's what "sda4" actually is...
at least, that's what it is on mine!"

Jammanuser wrote in this post "...and how that in the first 
screenshot, it shows that the @correct partition@ was selected 
to boot the Ubuntu entry from...i.e. the 20 GB Linux native"
@you are claiming that the 3rd partition is correct, Partition 3@

TeX: Well, that 1st screenshot specifies "Partition 3" which
means you made a similar mistake to the one which you corrected.
(hd0,3) = sda4 as you say, but that's the 4th partition not the 3rd.
Which means Easybcd had the wrong partition chosen to boot
which caused the bootpart error message. I've only seen error
messages from bootpart when the partition boundary is moved and
bootpart is not rerun, or when the wrong partition is chosen to
boot; seems likely that there are other reasons to cause an error.

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> 
[COLOR="Red"]I think Partition 3 is sda3 and I think all of your fdisk reports
have shown that Ubuntu is installed on sda4, Partition 4.[/COLOR]

Post #26 /dev/sda4   31542       34090    20474842+  83  Linux 
Post #44 Gparted shows sda4, and Bootit shows 4th in the order

Post #48 your later edit showing Bootpart output

Physical number of disk 0: 3c5a8d58
0: C: type=6 <BIGDOS FAT 16>, size= 40131 KB, LBA Pos=63
1: C: type=82 <Linux swap>, size= 4602622 KB, LBA Pos=547655850
2: C: type=7 <HPFS/NTFS>, size= 243072920 KB, LBA Pos=20560325
3: C: type=83 <Linux native>, size= 20474842 KB, LBA Pos=50670615

TeX: The number is given as 3 but that is the 4th partition,
because the numbering starts at 0. 0,1,2,3, = 4 partitions

Post #63  sda4: File system:  ext3 <--[that means Linux native]
Post #84  sda4: File system:  ext3

Post #99 
title		Ubuntu Linux    
root		(hd0,3)   	
#Load Ubuntu from the 1st harddrive's 3rd partition. <----***

I seldom critique/comment on grub posts. I've explained the
difference between grub and fdisk style reports regarding 
partition numbers. So your above #comment is mistaken.
root (hd0,3) works because (hd0,3) = sda4, the 4th partition.
The grub partition numbers are one lower than fdisk numbers.
(hd0,x) corresponds to sdax where x is the partition number. 
But the x value in (hd0,x) is one number lower than the x value in sdax.
Anyway, the Easybcd/bootpart error message happened before #99.

I can't tell what other choices that Easybcd offered in your 1st
screenshot. Perhaps you picked Partiton 3 because it was the
only choice offered; but you failed to notice it was incorrect.
Those things happen along with typos. That is why I've learned
to eliminate/simplify any area which could go wrong, and to
uninstall/reinstall in quick situations like this out of good habit.

I already know that (hd0,3) equals sda4, or hard drive 0, and partition 4...as you can see from my post on that other thread from which you quoted in your last post...and I also already knew that the comment in my NeoGrub menu.lst, right next to the Ubuntu partition (hd0,3) was incorrect. :) That was what it said, before I edited it, and I didn't bother to correct it before...but now that you chose to bring up this "issue", I just fixed it, and changed it to say "4th partition", instead of "3rd partition".

Incidentally, I had a feeling that what it said in EasyBCD, i.e. "Partition 3", might become a problem for some...but I know for a **fact** that that is the correct partition that Ubuntu 8.10 is installed on, no matter what the partition number in EasyBCD is...I can tell that from the size! :) The 20 GB partition is the **only** partition close to that size...I don't have another, and so I know that i'm not mistaken that that is the correct partition that Ubuntu is installed on. However, since you seem to be having trouble believing that it is...I will take a few screenshots of the OTHER partitions shown by EasyBCD, and upload them in my next post! :lolflag:

I think the reason that it shows "Partition 3" instead of "Partition 4" in EasyBCD is maybe due to the program having a different numbering system...i.e. maybe only counting certain partitions, and excluding others! :) I have never understood that odd behavior of EasyBCD...perhaps I'll post over at the EasyBCD forums, and question them about it! ;)

Cheers! :lolflag:

-Jam man

:guitar:

P.S. maybe you should post over there as well...Techtonic! :guitar:

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> ------------------------------------------------------

In thread, Re: Help! no GRUB! :s Post #43
Originally Posted by northern lights  
sda4 translates to (hd1,3) and sda5 to (hd1,4) in GRUB syntax. (hd1,5) is 
your swap partition. Hence the "invalid device"

Jammanuser corrected the post of northern lights by saying,
"Wouldn't it be (hd0,3)? I think that's what "sda4" actually is...
at least, that's what it is on mine!"

Jammanuser wrote in this post "...and how that in the first 
screenshot, it shows that the @correct partition@ was selected 
to boot the Ubuntu entry from...i.e. the 20 GB Linux native"
@you are claiming that the 3rd partition is correct, Partition 3@

TeX: [COLOR="Red"]Well, that 1st screenshot specifies "Partition 3" which
means you made a similar mistake to the one which you corrected.[/COLOR]
(hd0,3) = sda4 as you say, but that's the 4th partition not the 3rd.
Which means Easybcd had the wrong partition chosen to boot
which caused the bootpart error message. I've only seen error
messages from bootpart when the partition boundary is moved and
bootpart is not rerun, or when the wrong partition is chosen to
boot; seems likely that there are other reasons to cause an error.

Again you're making the assumption that just because EasyBCD shows the partition selected as **Partition 3**, it means that it is **actually** partition 3, in terms of my hard drive sectors! ](*,) Just take a look at the attached image...:guitar: Notice in particular the **sizes** of the shown partitions in EasyBCD...and of course the order that they are shown! :) Counting from top to bottom, in EasyBCD, the "first" partition (partition 0) of drive 0 is Windows XP, the "second" is the swap partition (partition 1) for Linux, the "third" partition (partition 2) is Vista, and last of all, the "fourth" partition (partition 3) is the 20 GB Linux native partition for Ubuntu! 

Cheers! :lolflag:

-Jam man

:popcorn:

---

### Post by TeXtonyx on 2008-12-24
I'm not sure of the time sequence. Are the screenshots which show
the Easybcd/Bootpart error message quite recent? 

Your entry looks correct. At the time it is made, bootpart computes
a partition value. Later, changes can make another value correct.
So did you delete the entry you have for Ubuntu under Linux?
Then did you reinstall the entry for Ubuntu (using the same words 
and chosen partition as the first time)again? The reason is that
the inner partition value may have changed, if you do work on the 
system, since the first time you made the entry. When you reinstall
the entry a new inner value for the 512 bytes is computed. 

Since it only takes 10 to 15 seconds to delete Ubuntu and add it
back it again, it is worth trying. Because I only know of two 
reasons that bootpart fails, wrong partition selection, and an
uncorrected change to the inner computed value of the 512 byte 
segment ->linux.bin, already created.

.."it means that it is actually partition 3, in terms of my hard 
drive sectors!"

You explain this right after this phrase above. The grub (hd0,0)
and fdisk/gparted notation are different, sda1. But in an English
description (as you said you changed) people start counting at 1
and the sdax notation reflects this. They also use GB counting
of hard drive capacity versus GiB counting of drive capacity. 
It seems to me that you should include in your tutorial the
explanation why Bootit NG results don't match Gparted results
as covered in the Bootit docs, so go by linux results for linux.

---------------------------------------------------

"Your fdisk report will say something like sda3 which converts
to (hd0,2) the grub partition numbering notat^ion is one less.
Another example: sda6 = (hd0,5) "  post #41

-----------------------------------------------------

So how is installing the newly downloaded drivers working out?

---

### Post by TeXtonyx on 2008-12-24
"I think the reason that it shows "Partition 3" instead of 
"Partition 4" in EasyBCD is maybe due to the program having a 
different numbering system...i.e. maybe only counting certain 
partitions, and excluding others! I have never understood that 
odd behavior of EasyBCD...perhaps I'll post over at the EasyBCD 
forums, and question them about it

P.S. maybe you should post over there as well...Techtonic!"

--------------------------------------------------

I did and I have a new idea from doing that. How about creating
a new entry for Ubuntu called something like Ubu, so that you
can distinguish when you boot up, under add for Linux, and choose
partition 3 again (I suppose). When you boot up you should have
a choice for Ubuntu and Ubu, test the Ubu one out. This accomplishes
the same idea as deleting Ubuntu and then recreating the entry
for Ubuntu, it will write a new 512 byte boot segment for the 
bootpart aspect and test it (not NeoGrub) of the Easybcd mechanism.

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> I'm not sure of the time sequence. Are the screenshots which show
the Easybcd/Bootpart error message quite recent? 

I don't recall any screenshots of a error message in EasyBCD...:confused:
> 
Your entry looks correct. At the time it is made, bootpart computes
a partition value. Later, changes can make another value correct.
So did you delete the entry you have for Ubuntu under Linux?
Then did you reinstall the entry for Ubuntu (using the same words...


I tried deleting it, and putting back several times already...didn't help! ;) Actually, the entry shown in my screenshot was taken right after creating another entry for Ubuntu! I had previously deleted it, since it wasn't working anyway, and I put it back for illustrative purposes only...;)

Cheers!

> 
...and chosen partition as the first time)again? The reason is that
the inner partition value may have changed, if you do work on the 
system, since the first time you made the entry. When you reinstall
the entry a new inner value for the 512 bytes is computed. 


Every time I put the Ubuntu entry back, i made sure to select the correct partition each time...:lolflag:

> 
You explain this right after this phrase above. The grub (hd0,0)
and fdisk/gparted notation are different, sda1. But in an English
description **(as you said you changed)**...


I don't recall saying I changed anything...:confused:

> 
It seems to me that you should include in your tutorial the
explanation why Bootit NG results don't match Gparted results
as covered in the Bootit docs, so go by linux results for linux.

Yes, that seems like a good idea...obviously, the different numbering systems by BootIT NG and Gparted might confuse some! :)

I think I will include that in my tutorial...

Cheers! :lolflag:
> 
"Your fdisk report will say something like sda3 which converts
to (hd0,2)... 


sda3 is Vista, so i'm not sure what you're referring to there...;)
> 
So how is installing the newly downloaded drivers working out?

As I mentioned in the "[other] BIOS settings for XP and Vista" thread, most of them work...but a few dont! 

Cheers! 

-Jam man

---

### Post by Jammanuser on 2008-12-24
> **TeXtonyx said:**
> 
[COLOR="Red"]I did and I have a new idea from doing that.[/COLOR] How about creating
a new entry for Ubuntu called something like Ubu, so that you
can distinguish when you boot up, under add for Linux, and choose
partition 3 again (I suppose). When you boot up you should have
a choice for Ubuntu and Ubu, test the Ubu one out. This accomplishes
the same idea as deleting Ubuntu and then recreating the entry
for Ubuntu, it will write a new 512 byte boot segment for the 
bootpart aspect and test it (not NeoGrub) of the Easybcd mechanism.

I just checked over at the EasyBCD forum thread, and I didn't see any new post by you...:confused: The only new posts over there were by PCEye, and a few others...but I didn't see a new one by "Techtonic"! :)

As for creating a new Ubuntu entry with EasyBCD, and naming it "Ubu"...hmm, i'll try that! :) Although I seriously doubt that I will obtain any different results...;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-24
Quote:
Originally Posted by TeXtonyx View Post
I'm not sure of the time sequence. Are the screenshots which show
the Easybcd/Bootpart error message quite recent.

--------------------------------------------------------------

I don't recall any screenshots of a error message in EasyBCD...

-------------------------------------------------------
Post #1
"In the case with Ubuntu, i get the following error when trying to boot into it via the Vista bootloader:

Code:

BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

Loading new partition

Bootsector from C.H. Hochst&#8222;tter

 Cannot load from harddisk.

Insert Systemdisk and press any key.

--------------------------------------------------

I meant the above, a bootpart error message generated because Easybcd
is used.
This does not happen with the normal Vista bootloader menu process
because the Vista bootloader doesn't use Bootpart. There is a 
Vista boot menu without needing Easybcd(3rd party) to create it.
 
------------------------------------------------------

TeX: But in an English description (as you said you changed)...
I don't recall saying I changed anything.

"and I also already knew that the comment in my NeoGrub menu.lst, 
right next to the Ubuntu partition (hd0,3) was incorrect.  
That was what it said, before I edited it,"

--------------------------------------------------
I just checked over at the EasyBCD forum thread, and I didn't see any new post by you.

[http://neosmart.net/forums/showthread.php?t=3088](http://neosmart.net/forums/showthread.php?t=3088)

I created a new thread. I've lost interest in this discussion.

---

### Post by meierfra. on 2008-12-24
I figured out the remaining  dynamical bytes of the bootpart code. They are just the starting  sector of the partition  expressed in CHS. That means that your bootpart  code is definitely configured correctly.

---

### Post by TeXtonyx on 2008-12-24
Thanks, though doesn't that mean it should have worked. I 
can't seem to find any user fault which is mildly annoying. :-)

Also, thanks for your wonderful diagnostic bash script. I 
have the Advanced Bash Scripting Guide from TLDP, but it is 
a very long term project. A crafty script is just so clever!
And the change to RESULTS also good. 

Did you by any chance makes notes? I collect things like that
and have a bunch of utilities from PC World before they started
selling them, with a mini collection of context menu editors.
I have a hex editor but have only opened it once. I don't even
know any Windows people who use them. They don't know 
what they are missing. :-) Happy Holidays

---

### Post by Jammanuser on 2008-12-24
delete

---

### Post by TeXtonyx on 2008-12-24
> **Jammanuser said:**
> delete

---------------------------------------------

Originally Posted by Jammanuser  
That was not a screenshot, though... It was text that 
I typed up, and then simply wrapped code tags around!

So what. My word was descriptive enough for a non-technical
reference for a computer literate person to put 2 + 2 together.

--------------------------------------------------------

Jammanuser aka Coolname007 wrote:

"Do u take me for a complete idiot?
Ok, thanks...so where do i enter the fist commands u gave (i.e. 
the bootpart ones)? Do i run those in my Command Prompt back in 
Vista, or am i supposed to run that using the Ubuntu LiveCD? 
I'm sorry if that's a stupid question... "

TeX: You barely had a dozen references, to XP, bootpart, boot.ini,
Vista, Easybcd, and C:\bootpart (Linux doesn't have a C:\ root)
why would anyone think it was a stupid question?

--------------------------------------------------

Since I thought that, you have made quite a bit of progress in
restoring your XP drivers which has upgraded my opinion of your
computer literacy from its initial impression/judgment which
was based on your question about where to install bootpart, and
that I had to tell you 3 times that installing grub to (hd0,0)
would install to a boot partition and not overwrite the MBR=hd0 
and I gave you a reference to the online grub manual to prove it.
So your posts haven't inspired computer literacy awe.

---

### Post by Jammanuser on 2008-12-25
I was willing to let it alone (no need to point out his mistake, I thought), which is why I deleted my last post. :) If this discussion continues, I may have to unmark my thread as solved! Or the admins and mods may begin to get annoyed at the comments flying back and forth in a thread marked as "solved". :lolflag: But since you weren't able to...

> **TeXtonyx said:**
> ---------------------------------------------

Originally Posted by Jammanuser  
That was not a screenshot, though... It was text that 
I typed up, and then simply wrapped code tags around!

[COLOR="Red"]So what. My word was descriptive enough for a non-technical
reference for a computer literate person to put 2 + 2 together.
[/COLOR]


Descriptive perhaps...but not accurate. :popcorn: Again, it was **text** in that post, not a screenshot. :guitar:
> 
Jammanuser aka Coolname007 wrote:

"Do u take me for a complete idiot?
Ok, thanks...so where do i enter the fist commands u gave (i.e. 
the bootpart ones)? Do i run those in my Command Prompt back in 
Vista, or am i supposed to run that using the Ubuntu LiveCD? 
I'm sorry if that's a stupid question... "

TeX: You barely had a dozen references, to XP, bootpart, boot.ini,
Vista, Easybcd, and C:\bootpart (Linux doesn't have a C:\ root)
why would anyone think it was a stupid question?


It was indeed not a stupid question...I had no way of knowing whether he was talking about entering it in a Command Prompt, or in a Terminal using the LiveCD. And I don't recall ever saying that Linux had a C:\root...](*,)
> 
Since I thought that, you have made quite a bit of progress in
restoring your XP drivers which has upgraded my opinion of your
computer literacy from its initial impression/judgment [COLOR="Red"]which
was based on your question about where to install bootpart,[/COLOR] and
that I had to tell you 3 times that installing grub to (hd0,0)
would install to a boot partition and not overwrite the MBR=hd0 
and I gave you a reference to the online grub manual to prove it.
So your posts haven't inspired computer literacy awe.

Hmm...I don't ever recall saying I was perfect (as you obviously think **you** are), but it seems I need to re-read the previous posts of this thread, so I will know for sure that I never asked a question about where to install bootpart. It seems we both need to delve in the past a little, so we can make sure that our posts are 100% accurate, when we're quoting someone else, so we don't say something wrong which could be used by the other one against each of us...=;

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-25
> **Jammanuser said:**
> Ahh...that is what i kind of figured. :-k The thought of EasyBCD having to depend on Bootpart to boot Ubuntu occurred to me, u see...unfortunately, though, i've already researched it (and visited the link u just gave), and [COLOR="Red"]i learned that that program can only be installed on Fat partitions.[/COLOR] That is impossible in my case, because the Vista partition is NTFS...:-(

If only there was a way to boot Ubuntu using EasyBCD without using Bootpart...

Yes...I believe I said that bootpart couldn't be installed on NTFS partitions, which was of course cleared up by this comment in Post #43:

> [COLOR="Red"]Bootpart will work on an NTFS partition... even though there is a note on their web page says something about it not working for NTFS. Apparently some of the things bootpart will do do not work on NTFS partitions.
[/COLOR]
To be able to boot your Ubuntu installation, a grub bootloader has to be installed somewhere. Those commands will not get rid of a Vista / XP MBR (Master Boot Record) but will install an additional boot sector on just the Ubuntu partition.

I just got my dual boot squared away. I'm using the NT boot manager (the one that usually only lists Windows versions) and it lists Ubuntu, too. I installed Ubuntu and then installed Windows XP, so the XP bootloader had gotten rid of grub so I could not boot Ubuntu off the second hard drive partition, yet.

I don't believe I asked where to install bootpart...:-k Of course you might have been talking about a different post...8) I will continue my search, though...i'll let you know if I find anything! :D

Cheers! :)

-Jam man

:guitar:

> **TeXtonyx said:**
> 
Since I thought that, you have made quite a bit of progress in
restoring your XP drivers which has upgraded my opinion of your
computer literacy from its initial impression/judgment which
was based on your question about [COLOR="Red"]where to install bootpart[/COLOR], and
that I had to tell you 3 times that installing grub to (hd0,0)
would install to a boot partition and not overwrite the MBR=hd0 
and I gave you a reference to the online grub manual to prove it.
So your posts haven't inspired computer literacy awe.

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> Take the cd out. When you reboot you should boot into Vista. Now 
uninstall Easybcd and reinstall it. [COLOR="Red"]The next error comes from resizing.[/COLOR]
BootPart 2.60 Bootsector 
Loading new partition
 Cannot load from harddisk.
Insert Systemdisk and press any key.


I still don't understand how the error could have come from resizing, if I didn't resize anything...](*,)

Cheers! :lolflag:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-25
TeX: You barely had a dozen references, to XP, bootpart, boot.ini,
Vista, Easybcd, and C:\bootpart (Linux doesn't have a C:\ root)
why would anyone think it was a stupid question?
---------------------------------------------------------
Jammanuser replied in Post #152:
"It was indeed not a stupid question...I had no way of knowing 
whether he was talking about entering it in a Command Prompt, or 
in a Terminal using the LiveCD. And I don't recall ever saying 
that Linux had a C:\root.."

----------------------------------------------

No, you never said that, we said that bootpart.exe went to C:\ 
That is called the root directory of Windows. *C:\ shows up 
in the posts made by mkoyle and those posts you quote me in.
-----

Post #12
 Originally Posted by TeXtonyx  
Your boot.ini may have the wrong partition number. Mine says,
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT
*c:\UbuntuB.bin="Ubuntu"

Post #14 J: hmm...it looks to me from what i highlighted in red, as if 
u somehow configured the boot.ini  file to boot Ubuntu, as well as XP..

You quote me in Post #20 referring to the boot.ini file:
The second line boots Ubuntu. The Bootpart 2.60 error message
that you posted and I referenced is part of the Easybcd engine.
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) bootpa26.zip
If you download that, unzip bootpart.exe to *C:\ the output->

-----------------------------

mkoyle wrote in post #43
"Bootpart will work on an NTFS partition ...
To fix this, I started in Windows XP.
I downloaded bootpart from [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm), 
and extracted it to *c:\bootpart. Then I executed the following:
Code:
bootpart
bootpart 4 *c:\ubuntu.lnx Ubuntu Linux

-------------------------------

J*wrote in post #45
"and i read that the program could not work on NTFS partitions...
it could only work on Fat. However, if u say it does...

Ok, thanks...so where do i enter the fist commands u gave (i.e. 
the bootpart ones)? Do i run those in my Command Prompt back in 
Vista, or am i supposed to run that using the Ubuntu LiveCD? 
I'm sorry if that's a stupid question..."

--------------------------------------

It is a matter of education and experience to know that no
Windows .exe command file runs in Linux and you are new to 
Linux, so perhaps don't know that a Linux terminal does not
open and show anything beginning with C:\ 
But that is a Windows basic that people beyond email and browsing
the internet know. I mean that's the next step up, command prompt.
Noticing that both mkoyle and I are talking about the same 
program comes from recognizing that the download url is identical.
mkoyle:   extracted it to *c:\bootpart    
TeXtonyx: unzip bootpart.exe to *C:\

You say that you think bootpart works on Fat, and will take it 
on faith that it works for NTFS despite what the webpage says.
#26
/dev/sda3   *       1280       31541   243072920    7  HPFS/NTFS 
/dev/sda4           31542       34090    20474842+  83  Linux

Again you may not understand Linux and fdisk. The report above
tells one that opening a terminal on Linux type 83 is not the
correct partition type for bootpart, which works on NTFS and 
NTFS/Windows, which open Command Prompts not Linux 83 terminals.

What you failed to connect the dots on mostly has to do with
education and experience. I have to make assessments of the skill
level of my customers in order to give them a meaningful answer
to their questions. I don't give answers that involve them having
to ask more questions, and then ask more questions to understand
those answers. For instance I gave you a short summary of what
you missed that would have answered your question. Your response
showed you didn't understand that summary. It seemed like you
thought I was making up quotes when actually, you didn't remember
them and also you don't have the background to interpret them.
But that is not how you see yourself. So I went through and
documented my summary of remarks from posts mostly that you wrote
which quoted me or mkoyle. We do not share the same skill set.  
I didn't include references to discussing Vista and Easybcd and
how bootpart was part of how Easybcd, a Windows program, worked.

I'm not going into detail about that kind of exchange again. I
will provide deeper explanations about specific *computer*
solutions if asked. That concludes my responses to you on this
thread which means I'm free to discuss with anybody else I
choose and to change my mind about that.

---

### Post by Jammanuser on 2008-12-25
Ok. I think this article explains why I had to reinstall BootIT NG, when I transferred my Wubi install of Ubuntu 8.10 over to a dedicated partition...it seems that LVPM must use install Grub to the MBR, instead of to the partition's boot sector! :) And when this happened, it simply overwrote my EMBR, making BootIT NG unbootable...and of course it also explains why I wasn't able to boot from Ubuntu before using BootIT NG, even after creating a direct boot entry for it with the program! It was because the opposite **also** holds true. When Grub exists in the MBR, and you install BootIT NG's EMBR, it overwrites at least **part** of Grub in the MBR, making Grub in turn unusable! :guitar:

To see what I mean, see this article: [http://www.terabyteunlimited.com/kb/article.php?id=171&pt_sid=25a30f62aed83910d91d8053127b4ee0](http://www.terabyteunlimited.com/kb/article.php?id=171&pt_sid=25a30f62aed83910d91d8053127b4ee0)

Of course I have been suspecting this for a long time, but this article just confirms it! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Jammanuser on 2008-12-25
> **TeXtonyx said:**
> 
[COLOR="Red"]It is a matter of education and experience to know that no
Windows .exe command file runs in Linux[/COLOR] and you are new to 
Linux, so perhaps don't know that a Linux terminal does not
open and show anything beginning with C:\ 


Admittedly, I am new to Linux, like you said, but I did indeed already know that .exe files don't work in Linux! :) Of course at that time, though, my mind was occupied by other things, and so that small detail didn't immediately rise to the surface! :lolflag: Thanks for bringing that matter to the light! :) I stand corrected...

But that doesn't justify either all of the **incorrect** things you said...half of which you deleted after realizing it! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

EDIT: "delete...delete...delete...delete...delete..." :D

---

### Post by Jammanuser on 2008-12-25
> **mkoyle said:**
> [COLOR="Red"]What is the output when you run bootpart?[/COLOR]  Nothing I see about bootpart in its documentation suggests that it is compatible with Vista, so I am guessing it just plain is not.


Never mind...I got it to work after looking back over this thread, though I had to run "C:\bootpart 4 c:\ubuntu.lnx", instead of "bootpart 4 c:\ubuntu.lnx Ubuntu Linux"...even though it says there's an error in the parameters. It seems it has to be prefixed (in Vista, at least) with "C:\", instead of just "Bootpart".

Anyway, here's the output of that command now:

```
C:\bootpart 4 c:\ubuntu.lnx Ubuntu Linux
Boot partition 2.60 for WinNT/2K/XP <c>1995-2005 G. Vollant <info@winimage.com>
WEB : http://www.winimage.com and http://www.winimage.com/bootpart.htm
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "C:\bootpart /?" for more information

Physical number of disk 0: 3c5a8d58
  0 : C: type=c <win95 Fat32 LBA>, size= 30716280 KB, Lba Pos=556861095
  1 : C: type=82 <Linux swap>, size= 4602622 KB, Lba Pos=547655850
  2 : C:* type=7 <HPFS/NTFS>, size= 243072920 KB, Lba Pos=506706165
Error in parameters
```

I also attached a screenshot of the output, as well...I hope its close enough to see! :)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by TeXtonyx on 2008-12-26
If you open a command prompt, it usually opens in the
C:\Documents and Settings\username> directory 
From that location you have to type the absolute path to
bootpart.exe assuming that bootpart.exe is in C:\ the root directory.
C:\Documents and Settings\username\> "C:\bootpart 4 ubuntu.bin Ubuntu"
without the quote marks.

I usually change from C:\Documents and Settings\username> cd \ <enter>
which takes you to the root directory C:\>
where you simply type "C:\>"bootpart 4 ubuntu.bin Ubuntu" <enter>
without the quotes. That is what you use for XP, because the
above command also writes Ubuntu into the boot.ini file (menu).

From Vista, you just type C:\>bootpart 4 ubuntu.bin 
without the Ubuntu title, because Vista has no boot.ini (itslef) 
so there is no boot.ini to write to. That is an XP file. 
What I wrote did not cover when XP and Vista boot files combine.
Usually bootpart is information for Vista. You can use ubuntu.bin
to make a manual addition to the bcd data store with a lot of work.

---

### Post by Jammanuser on 2008-12-26
> **TeXtonyx said:**
> If you open a command prompt, it usually opens in the
C:\Documents and Settings\username> directory 


Mine opens in the "C:\Windows\System32>" dir without the quotes...which is why I didn't understand it the last time! :) It seems that mine and yours start at two different locations...:guitar:

Cheers! :popcorn:

-jam man

:guitar:

---

### Post by dmizer on 2008-12-26
Closing this thread.

The thread is marked solved, and I'm not happy with the direction the conversation has gone.

Thank you.

---

