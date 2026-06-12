---
title: "NTFS Partition and Windows Reinstall"
date: 2006-06-30
forum: Desktop Environments
---

### Post by visvak on 2006-06-30
two questions - 

1) since i've installed ubuntu its been mounting my NTFS partition without me having to change iny settings at all. but read access is enabled only in the root user. how do i read the NTFS with normal user accounts ?


2)my windows partition is now a month old an is therefore crawling with virii and trojans. i need to reinstall windows. is there anyway i could do this safely without disturbing the GRUB and Ubuntu ? otherwise, what is the easist way to get GRUB back after Windows overwrites it ?

---

### Post by shrift on 2006-06-30
1. please post the contents of /etc/fstab here.

2. You could try doing a "repair installation" of windows. It is an option when you boot off of your windows CD. Well, it's an option sometimes. Check it out.

If that doesn't work, and you do reinstall, you can boot a live CD of Ubuntu and run the grub installer.

---

### Post by lloydie on 2006-06-30
Excellent Tutorial allready - Mounting Windows Partitions
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[xxx] harddrive

sudo mount /dev/[xxx] /mnt/data -t ntfs -o nls=utf8,umask=0222

---

### Post by visvak on 2006-06-30
@shrift -

contents of fstab 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

no my windows source are my 8 hp system recovery cds. there is a recovery option but that is just formatting the user partition with a stylish name. tell me more about the live cd GRUB recovery method.

@lollydie

yes i know. there are plenty ofgreat guides available to MOUNT AN NTFS partition. as i've said already, my NTFS partition has been mounting by default since my dapper install. what i need is to make it accessible without root user.

---

### Post by shrift on 2006-06-30
Hmmm, interesting. Your ntfs isn't listed there. 

What is in your "/etc/mtab"

What lollydie posted is basicly what we need to do. But we need some info about the ntfs drive first, like what device it is. I think the mtab should have it. But just in case type "sudo fdisk -l" in a console and find the drive that has an ntfs file system type. Paste that into the forum as well.

---

### Post by shrift on 2006-06-30
As for Grub, this post may help.

[http://ubuntuforums.org/showthread.php?t=206363](http://ubuntuforums.org/showthread.php?t=206363)

---

### Post by visvak on 2006-06-30
contents of etc/mtab -

```
/dev/hdb2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0

```

sudo fdisk -I -

```
Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5290    42491893+   7  HPFS/NTFS
/dev/hdb2            5291        9568    34363035   83  Linux
/dev/hdb3            9569        9733     1325362+   5  Extended
/dev/hdb5            9569        9733     1325331   82  Linux swap / Solaris

```

thanks for the GRUB post. will check it out.

---

### Post by visvak on 2006-07-01
ummm . . . just found this - [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

its called super grub disk and is supposed to restore the GRUB boot loader with a simple process. has anyone tried it ? does it work ? it sounds too good to be true after days of hunting around for the correct terminal commands from live cd.

---

### Post by shrift on 2006-07-01
It's worth a try. I don't think it will screw your system up more than reloading windows would.

---

### Post by adrian15 on 2006-07-01
[QUOTE=visvak]ummm . . . just found this - [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

its called super grub disk and is supposed to restore the GRUB boot loader with a simple process. has anyone tried it ? does it work ? it sounds too good to be true after days of hunting around for the correct terminal commands from live cd.[/QUOTE]

Why don't you try it yourself? Comment your thoughts and autorize me to post them in Super Grub Disk site so that everyone knows how wonderful is Super Grub Disk?

[i]The only "but" that you could have is if you had more than one linux installed... SGD will restore automatically only the first linux's grub.
But do not worry too much... in less than in a month... (well, in fact, it is already true with 0.9412) you will be able to choose Grub files partition manually from the new SGD version.[/i]

As long as your case it is only reinstalling windows. SGD will restore your Grub without any problem. Enjoy it.

Any problem? Just post it here.

And do not forget to ** Comment your thoughts and autorize me to post them in Super Grub Disk site ** ;)


adrian15

---

### Post by visvak on 2006-07-01
[QUOTE=adrian15]Why don't you try it yourself? Comment your thoughts and autorize me to post them in Super Grub Disk site so that everyone knows how wonderful is Super Grub Disk?

[i]The only "but" that you could have is if you had more than one linux installed... SGD will restore automatically only the first linux's grub.
But do not worry too much... in less than in a month... (well, in fact, it is already true with 0.9412) you will be able to choose Grub files partition manually from the new SGD version.[/i]

As long as your case it is only reinstalling windows. SGD will restore your Grub without any problem. Enjoy it.

Any problem? Just post it here.

And do not forget to ** Comment your thoughts and autorize me to post them in Super Grub Disk site ** ;)


adrian15[/QUOTE]

sure but make sure u check back to this post after a couple of days becoz ive given the cds out to ma friends and collegues and will get it back only monday. no prob for me wid that 2 linux thing. i jus got WinXP and Ubuntu Dapper. so u are adrian15 - the link i gave has ur name. wat are u ? the dev of this prog or somethin ???

also, a question - i've got the ISO file from the site. now can i just burn it to a blan CD-R with neroLinux making it bootable ? will it work then ? also, how come the download is so small ? i normally thought all ISOs were a few GB in size ? this thing just keeps on getting better and better.

---

### Post by adrian15 on 2006-07-02
> **visvak]sure but make sure u check back to this post after a couple of days 
[/QUOTE]
I am subscribed to the post. Do not worry.
[QUOTE=visvak]
becoz ive given the cds out to ma friends and collegues and will get it back only monday.
[/QUOTE]
You have given windows cds to your friends! You are not a good friend.  said:**
>  the link i gave has ur name. wat are u ? the dev of this prog or somethin ???

Yes, I am the dev of SGD but I do not consider myself as a god. I like feedback from normal users.

[QUOTE=visvak]
also, a question - i've got the ISO file from the site. now can i just burn it to a blan CD-R with neroLinux making it bootable ? 
[/QUOTE]
From the site you can download zip, bzip2 or gz files... please make sure to unzip, bunzip2 or gunzip it to an ISO before burning it. Some programs as winrar shadow real extension and you think you have an iso file when you, in fact, have a iso.bz2 file.

And yes. Once you burn it, not dragging it to the cd filesystem, but with the option Burn CD Image... inside File or Tools menu, it varies on Nero versions. the blank cd-r will be bootable.

Do you use NeroLinux?! Why don't you use K3b? NeroLinux lacks some features and it is very ugly. But NeroLinux can burn SGD too.

[QUOTE=visvak]
how come the download is so small ? i normally thought all ISOs were a few GB in size ? this thing just keeps on getting better and better.[/QUOTE]

Well... A normal grub disk is even smaller than SGD... but it is that with Grub you can do a lot of things without the need of booting a kernel, I mean without the need of having linux and a live system. And Grub it is small... so... everything goes small.

Waiting for your impressions.

adrian15

---

### Post by visvak on 2006-07-02
[QUOTE=adrian15]

From the site you can download zip, bzip2 or gz files... please make sure to unzip, bunzip2 or gunzip it to an ISO before burning it. Some programs as winrar shadow real extension and you think you have an iso file when you, in fact, have a iso.bz2 file.

And yes. Once you burn it, not dragging it to the cd filesystem, but with the option Burn CD Image... inside File or Tools menu, it varies on Nero versions. the blank cd-r will be bootable.

Do you use NeroLinux?! Why don't you use K3b? NeroLinux lacks some features and it is very ugly. But NeroLinux can burn SGD too.

Waiting for your impressions.

adrian15[/QUOTE]

yes yes. i know about the ISO. i forgot to tell u that i extracted it already. 

i somehow dont like using KDE apps in GNOME. have bad experiences. they always popup 1 error message or another saying "error with Knotify" "error with this" "error witht that". is it reeally that gud that its better than neroLinux and gnomeBaker (both of which i have) ?

oh and thank u. u are the first ever accessible program developer i have ever come across.

---

### Post by visvak on 2006-07-06
not working. adrian i need help. fast. i burnt the cd, formatted my windows partition, and then booted with SGD. i selected Super Grub Disk - en and then automatic install after that it ran a lot of commands on my screen and kept prompting me to press any key once in a while and then it said "NO = SUCCESS" or something similar. there was no option to quit, so i just ejected the cd and restrted my comp by killing the power. it did not give me my GRUB, it booted straight into windows. 

pls help adrian. i want my ubuntu back.

---

### Post by adrian15 on 2006-07-06
UPDATE:
Please download last version of SGD in ISO format which it is:
[http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=67](http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=67)

[LIST]
[*]Restore Grub on the MBR
[*]Manually
[*]You can choose but I would bet it is /boot/grub/menu.lst
[*]Select Second Hard Disk. Select Second Partition.
[*]Select Second Hard Disk.
[/LIST]

SGD tries to restore Grub on the MBR automatically in hd0, which means first hard disk.

It seems that your system goes like this:
You have one hard disk which it is the second hard disk.
The bios boots this second hard disk identifying it as a second hard disk...
so Grub sees it as hd1.

hd0 does not exists... so when doing restore grub to hd0 it fails!

Now I am 90% sure that the Boot your OS again AUTO option will work.

The other 10% thinks about the SGD filesystem support.

Good Luck.

adrian15

=============
Hummm... Which fs did you use with Ubuntu ?

How did you make the windows format ? Weren't you go to do a reinstall?

Now there are two options to make your linux boot:

1) Special Boot -> Boot your OS again -> Auto
1.5) Try the manual options. Select one of the four... /boot/grub/menu.lst options and then second hard disk and second partition.
2) Boot other oses -> Linux -> Select the option you need.

If the option 1 does not work it would be very weird that would mean that a) you did not have grub correctly installed... maybe lilo was installed? or b) SGD cannot read the filesystem where ubuntu was installed. This is a problem of mine. I would bet the filesystem was reiserfs4 or something.


Hey... wait a minute! There's a little option: Did you use SGD as a floppy? Can you please use SGD as a cdrom ?

Tell me please what version of SGD you used (Check the file you downloaded not the version that shows off when booting).

If you tried a very new version I recommend you to download the version from freshmeat the 0.9328 version.

That's all the help I can give you right now. Please give me details about what works and what does not work.

adrian15

P.S.: If nothing of the above works... keep a knoppix in hand... and we will see the live-cd approach.
P.S2: The only strange thing about your partition scheme is that it is on a second hard disk. But SGD should handle it.

---

### Post by visvak on 2006-07-07
> **adrian15 said:**
> UPDATE:
Please download last version of SGD in ISO format which it is:
[http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=67](http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=67)

[LIST]
[*]Restore Grub on the MBR
[*]Manually
[*]You can choose but I would bet it is /boot/grub/menu.lst
[*]Select Second Hard Disk. Select Second Partition.
[*]Select Second Hard Disk.
[/LIST]

SGD tries to restore Grub on the MBR automatically in hd0, which means first hard disk.

It seems that your system goes like this:
You have one hard disk which it is the second hard disk.
The bios boots this second hard disk identifying it as a second hard disk...
so Grub sees it as hd1.

hd0 does not exists... so when doing restore grub to hd0 it fails!

Now I am 90% sure that the Boot your OS again AUTO option will work.

The other 10% thinks about the SGD filesystem support.

Good Luck.

adrian15

=============
Hummm... Which fs did you use with Ubuntu ?

How did you make the windows format ? Weren't you go to do a reinstall?

Now there are two options to make your linux boot:

1) Special Boot -> Boot your OS again -> Auto
1.5) Try the manual options. Select one of the four... /boot/grub/menu.lst options and then second hard disk and second partition.
2) Boot other oses -> Linux -> Select the option you need.

If the option 1 does not work it would be very weird that would mean that a) you did not have grub correctly installed... maybe lilo was installed? or b) SGD cannot read the filesystem where ubuntu was installed. This is a problem of mine. I would bet the filesystem was reiserfs4 or something.


Hey... wait a minute! There's a little option: Did you use SGD as a floppy? Can you please use SGD as a cdrom ?

Tell me please what version of SGD you used (Check the file you downloaded not the version that shows off when booting).

If you tried a very new version I recommend you to download the version from freshmeat the 0.9328 version.

That's all the help I can give you right now. Please give me details about what works and what does not work.

adrian15

P.S.: If nothing of the above works... keep a knoppix in hand... and we will see the live-cd approach.
P.S2: The only strange thing about your partition scheme is that it is on a second hard disk. But SGD should handle it.

i use the ext3 filesystem with ubuntu. also, i did not try on a floppy. i used a cd-r. i burnt with nerolinux and used it. i've already tried "boot other OSs > boot GNU/Linux. it failed. i don't remember which version of SGD i used and i can't check bcoz the file is on my Ubuntu partition.](*,) 

anywayz, what manual option ar you talking about ? there's only one option in Restore GRUB to MBR and thats Automatic.](*,)  there's a manual option in this new version u asked me to download ?

i have a ubuntu live (+ install) CD. i got it from shipit. will this work ? coz i dont have Knoppix.

previously i had formmatted the whole HDD, installed windows on the full hard disk, then iinstalled ubuntu on a 40gb partition which the install/live cd made. what i did no was format my user partition and reisntall windows on that partition with my HP system recovery CDs. does that give you more of an idea as to how my partitioning looks like ?

---

### Post by visvak on 2006-07-07
adrian,

i've managed to boot into ubuntu with the special boot option in super grub disk. it even detected my existing GRUB. now is it restored as default ?? can u tell me the commands to reinstate GRUB now if its not already become default ? waiting for your reply, thanks.

EDIT - yipee. i've got my GRUB back. i used SGD to boot into Ubuntu thru special boot then i ran the following commands - 

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar. (I booted from SGD)

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. (I got (hd0,1)

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)". (I typed (hd0) to rewrite it to MBR)

and i now have my GRUB back. thanks for all your help adrian.

---

### Post by adrian15 on 2006-07-07
Can you make me two favours please?

1) Which was the version of SGD that did not do the work ok?
2) 
2.1)If you boot with SGD go to the main page where you do have Restore Grub to the MBR, Special boot,... and you press c key and then you type this commands:

root (hd0,1)
setup (hd0)

What does SGD replies to you?

2.2)
can you please type

cat (hd
and press the TABULATOR key to see if it suggests you only the hd1 hard disk?

If autocompletes hd1... I think that: (Can you try it please?)

2.3)
root (hd1,1)
setup (hd1)

will restore grub to your mbr.

If the problem it is because of the hd1... the new version of SGD... yes has the manual fashion of restoring grub to the mbr.

Please tell me your results... SGD is supposed to understand ext3 very well... well... in fact if you could boot that means that SGD understands it.

The problems reduces to two:
1) SGD did not deal ok with your hd1-based system
or
2) SGD cannot manage your stage2 file (I mean installing on mbr) for some reason that I do not know.

As long as you can boot Ubuntu with SGD and then restore Grub manually with the commands you've learnt... do not be afraid of doing the tests. ;)

Thank you very much!

adrian15

---

### Post by visvak on 2006-07-07
the version i used is something like .9382 not sure. coz i've deleted the ISO file. anyways i will do these tests and tell u what happened.

---

