---
title: "Help! No GRUB! :s"
date: 2008-12-21
forum: General Help
---

### Post by 22Ti on 2008-12-21
To make a long story short Windows f*cked up my grub. I dont get it in the startup anymore. I have tried with live cd>
sudo -i
grub
find /boot/grub/stage1 // Will print something like (hd0,1)
root (hd1,5)
setup (hd0)
quit

but at the setup I get:

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,5)/boot/grub/stage
2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested

***************
Please help I need my ubuntu asap!!
:(

---

### Post by northern lights on 2008-12-21
You could alternatively try to utilize the [SuperGrubDisk]("http://www.supergrubdisk.org/"). What you've been attempting sounds about right though. From the LiveCD, you should be able to run```
sudo grub
grub> find /boot/grub/stage1
grub> root (hdX,X) // replace X,X by what the above put out
grub> makeactive
grub> setup (hd0)
grub> quit
```

---

### Post by 22Ti on 2008-12-21
If I type makeactive I get the same Error 12: Invalid device requested

---

### Post by northern lights on 2008-12-21
Are you still going for (hd1,5)?

Error 12 is what it says. You've selected a wrong hdd. Are there more than one in the machine?

---

### Post by 22Ti on 2008-12-21
Yes their are 3 hdd. Only one is the one with ubuntu and xp but on seperate partitions

---

### Post by northern lights on 2008-12-21
Can you post the output of ```
sudo fdisk -l
```and```
blkid
```from the LiveCD? Thank you.

---

### Post by 22Ti on 2008-12-21
**********
sudo fdisk -l
**********

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75ab1d98

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       60801   488384001   83  Linux
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         450     3614593+  12  Compaq diagnostics
/dev/sda2   *         451        3000    20482875    7  HPFS/NTFS
/dev/sda3            3001       19456   132182820    f  W95 Ext'd (LBA)
/dev/sda4            5551       19456   111699913+  83  Linux
/dev/sda5            3001        5488    19984797   83  Linux
/dev/sda6            5489        5550      497983+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb7df0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    5  Extended
/dev/sdb5               1        9733    78180259+  83  Linux




*************
blkid
*************
/dev/hdb1: UUID="d50dc054-b226-4ce8-aec8-e616406c1e7f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="423B-2BDF" TYPE="vfat" 
/dev/sda2: UUID="3488BC9488BC5658" LABEL="EREBUS" TYPE="ntfs" 
/dev/sda4: UUID="45175502-0aa6-40a4-90bc-08a07511d693" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="8ebb30e4-defc-4557-99e9-187b35d5bd34" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="94f451fd-3267-4dc6-9c58-150c86089916" TYPE="swap" 
/dev/sdb5: UUID="47027abd-c77f-4c0b-8a14-f4807e5fb2be" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by northern lights on 2008-12-21
Your Ubuntu appears to be either installed on sda4 or sda5. As those are the two ext3 partitions.
Do you have a separate /home or a second distro installed?
Anyhow, sda4 is much larger than sda5. You should know whether Ubuntu is on the larger or the smaller of the two partitions.

sda4 translates to (hd1,3) and sda5 to (hd1,4) in GRUB syntax. (hd1,5) is your swap partition. Hence the "invalid device"

Run the above again with either (hd1,3) or (hd1,4).

I.e.```
sudo grub
grub> root (hd1,3) // or 1,4
grub> makeactive
grub> setup (hd0)
grub> quit
```

---

### Post by 22Ti on 2008-12-21
Thank you!!!!

I also read about the -1 in naming partitions but I figured the grub detect would take it into account. 

Anyway, the setup went through without error although I tried 1,4 first which gave error 12 but 1,3 went smoothly!

I will restart and hope everything is back to normal!

Vielen Dank!

---

### Post by 22Ti on 2008-12-21
Problem... now I get on bootup> cant start operating system

I think we did something but their is something missing.

Would you mind..

---

### Post by 22Ti on 2008-12-21
I might know why it dosent work...when I check the menu.lst its blank

any ideas

---

### Post by 22Ti on 2008-12-21
bump

---

### Post by northern lights on 2008-12-21
> **22Ti said:**
> Would you mind..
Of course not. Although I had hoped that'd be it.

GRUB should set itself up and create a menu.lst I have no idea why it'd be blank. Are you sure you checked the menu.lst on the harddisk and not on the LiveCD itself?
When booting from the LiveCD, your regular filesystem should be mounted under /media/. Hence check in /media/WHATEVER/boot/grub/ also.

If the hdd one is blank indeed, open it in a root texteditor (gksu gedit) and make it```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default		0

timeout		3

hiddenmenu

# kopt=root=/dev/sda3 ro
# groot=(hd0,0)
# alternative=true
# lockalternative=false
# defoptions=quiet splash
# lockold=false
# xenkopt=console=tty0
# altoptions=(recovery mode) single
# howmany=3
# memtest86=true
# updatedefaultentry=false
# savedefault=false

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		45175502-0aa6-40a4-90bc-08a07511d693
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45175502-0aa6-40a4-90bc-08a07511d693 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		45175502-0aa6-40a4-90bc-08a07511d693
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=45175502-0aa6-40a4-90bc-08a07511d693 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Windows XP
root		(hd1,1)
makeactive
chainloader	+1
```
The uuid's in the above are already yours. Just adjust the kernel version to what you have installed. Further, I'm assuming sda2, which is (hd1,1) hosts a Windows install. Is that right?

---

### Post by 22Ti on 2008-12-21
If i go to>

/media/disk/grub

I can find> 
/media/disk/grub/default (**empty except the line default)**
/media/disk/grub/device.map
/media/disk/grub/e2fs_stage1_5
/media/disk/grub/fat_stage1_5
/media/disk/grub/jfs_stage1_5
/media/disk/grub/minix_stage1_5
/media/disk/grub/reiserfs_stage1_5
/media/disk/grub/stage1
/media/disk/grub/stage2
/media/disk/grub/xfs_stage1_5

about the windows sda2 I think so.

---

### Post by northern lights on 2008-12-21
> **22Ti said:**
> If i go to>

/media/disk/grubRather check /media/disk/[COLOR="Red"]boot[/COLOR]/grub/

---

### Post by 22Ti on 2008-12-21
btw how do I check the kernel version on hdd.

I did backup my old menu.lst once as I changed my grub list. but I cant find it anywhere

---

### Post by ajgreeny on 2008-12-21
I note that you said you have three disks in your computer, but in fact you only have two physical disks.  This may be because windows sees your three windows partitions as disks, and will not see the linux partitions at all.  Don't worry about this, but I thought I would point it out to you as you may otherwise get confused between disks and partitions when you get further along the ubuntu road.

EDIT:  You can find the kernel you are running by using the command in terminal ```
uname -a
```

---

### Post by 22Ti on 2008-12-21
/media/disk/boot/grub/ 

dosent exist

only in filesystems (I guess is livecd) has boot but no grub...

---

### Post by northern lights on 2008-12-21
Check your kernel versions in /var/lib/dpkg/info/ and note the numbers after linux-image-

Alternatively you can run ```
locate linux-image
```Just don't get confused with the LiveCD's kernel version.

---

### Post by 22Ti on 2008-12-21
No, I have one hdd with 500gb, one with 160gb and one with 80gb. Iam sure of this.

---

### Post by northern lights on 2008-12-21
> **ajgreeny said:**
> I note that you said you have three disks in your computer, but in fact you only have two physical disks.
He's got three. A 500gig one, a 160gig one and an 80gig one.
> **22Ti said:**
> **********
sudo fdisk -l
**********
[COLOR="Red"]
Disk /dev/hdb: 500.1 GB, 500107862016 bytes[/COLOR]
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75ab1d98

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       60801   488384001   83  Linux
omitting empty partition (5)

[COLOR="Red"]Disk /dev/sda: 160.0 GB, 160041885696 bytes[/COLOR]
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         450     3614593+  12  Compaq diagnostics
/dev/sda2   *         451        3000    20482875    7  HPFS/NTFS
/dev/sda3            3001       19456   132182820    f  W95 Ext'd (LBA)
/dev/sda4            5551       19456   111699913+  83  Linux
/dev/sda5            3001        5488    19984797   83  Linux
/dev/sda6            5489        5550      497983+  82  Linux swap / Solaris

[COLOR="Red"]Disk /dev/sdb: 80.0 GB, 80060424192 bytes[/COLOR]
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb7df0f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9733    78180291    5  Extended
/dev/sdb5               1        9733    78180259+  83  Linux



> **ajgreeny said:**
> EDIT:  You can find the kernel you are running by using the command in terminal ```
uname -a
```
This will find the LiveCD's kernel, not the one on his hdd install.

---

### Post by 22Ti on 2008-12-21
Ran>  uname -r
[B]
2.6.22-14-generic[/B]

Also, this livecd is 7.10 and on hdd I have 8.4.

 locate linux-image gave>

locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/var/lib/dpkg/info/linux-image-**2.6.22-14-generic**.postinst
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.list
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.postrm
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.preinst
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.prerm
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.md5sums
/var/lib/dpkg/info/linux-image-generic.md5sums
/var/lib/dpkg/info/linux-image-generic.list
/usr/share/doc/linux-image-2.6.22-14-generic
/usr/share/doc/linux-image-2.6.22-14-generic/changelog.Debian.gz
/usr/share/doc/linux-image-2.6.22-14-generic/copyright
/usr/share/doc/linux-image-generic
/usr/share/doc/linux-image-generic/changelog.gz
/usr/share/doc/linux-image-generic/copyright

---

### Post by northern lights on 2008-12-21
> **22Ti said:**
> Ran>  uname -r
[B]
2.6.22-14-generic[/B]This is a mighty old kernel and definitely from the LiveCD.

If you're on Hardy your kernel version should be 2.6.26-XX-generic, where the XX is probably a number in the twenties.



> **22Ti said:**
> 
 locate linux-image gave>

locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/var/lib/dpkg/info/linux-image-**2.6.22-14-generic**.postinst
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.list
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.postrm
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.preinst
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.prerm
/var/lib/dpkg/info/linux-image-2.6.22-14-generic.md5sums
/var/lib/dpkg/info/linux-image-generic.md5sums
/var/lib/dpkg/info/linux-image-generic.list
/usr/share/doc/linux-image-2.6.22-14-generic
/usr/share/doc/linux-image-2.6.22-14-generic/changelog.Debian.gz
/usr/share/doc/linux-image-2.6.22-14-generic/copyright
/usr/share/doc/linux-image-generic
/usr/share/doc/linux-image-generic/changelog.gz
/usr/share/doc/linux-image-generic/copyright

This is also all LiveCD info.

Manually browse to /media/disk/var/lib/dpkg/info/. Now check here.

---

### Post by ajgreeny on 2008-12-21
Whoops!  Sorry, I was a bit too quick answering without looking in detail at your fdisk output;  it's a while since I have seen an hdb there as well as sda and sdb.  Just out of interest, where is your hda?  Also I didn't think about you only running the live CD to get the info asked for, so of course that would give the kernel of that, not your installed version.

Sorry again!!!

---

### Post by 22Ti on 2008-12-21
/media/disk/**var**/lib/dpkg/info/

this is what I have in disk>
/media/disk/grub
/media/disk/lost+found
/media/disk/mythtv
/media/disk/nnpro
/media/disk/tv
/media/disk/.directory

var seams to be missing...

I found an old backup of my whole root folder. boot>grub>menu.lst is in their.

Can this be used, kernel is 2.6.24-19-generic

this is before I changed anything in the list

---

### Post by northern lights on 2008-12-21
It can be used, if the package linux-image-2.6.24-19-generic is installed on your hdd. If you've never previously removed old kernel images, it should be there.

Anyhow, try it, you can't really screw up anything, as it isn't booting in the first place.

However,

> **22Ti said:**
> /media/disk/**var**/lib/dpkg/info/

this is what I have in disk>
/media/disk/grub
/media/disk/lost+found
/media/disk/mythtv
/media/disk/nnpro
/media/disk/tv
/media/disk/.directory

var seams to be missing...

/media/disk/ is not your hdd install's root filesystem. This is some other partition.

Your hdd install's root file system should include```
/apt
/bin
/boot
/dev
/etc
/home
/lib
/media
/mnt
/opt
/proc
/usr
/var

and the like
```

Run ```
sudo mount /dev/sda4
``` if it isn't mounted yet. If what you've posted was sda4 indeed, you system would be gone. Which I doubt is the case.

> **ajgreeny said:**
> it's a while since I have seen an hdb
True that. This is a Gutsy LiveCD...

---

### Post by 22Ti on 2008-12-21
in *disk* I cant do anything> no privileges except reading

---

### Post by northern lights on 2008-12-21
> **22Ti said:**
> in *disk* I cant do anything> no privileges except reading
Open nautilus as superuser```
gksu nautilus
```

---

### Post by 22Ti on 2008-12-21
Think I figured something out. I made an partition once when I hade problems with ubuntu> 20gb dedicated to ubuntu system files.
I finally mounted it and everything is in their

---

### Post by northern lights on 2008-12-21
Okay. Now don't attempt the manual route.

With your root filesystem mounted, run the grub setup again. It should work.

---

### Post by 22Ti on 2008-12-21
the system is on sda5 after all as a seperate (better safe than sorry) partition. But before I could not us it in grub...

---

### Post by northern lights on 2008-12-21
Okay. If the root filesystem is sda5, Run```
sudo grub
grub> root(hd1,4)
grub> makeactive
grub> setup (hd0)
grub> exit
```
You don't necessarily need to put grub in the 500gig drive's MBR either, you could even change the device after *setup*, but this should be fine.

If you need verification for this being the correct partition now, post the output of```
ls -l /media/SUPPOSEDROOTFILESYSTEM
```

---

### Post by 22Ti on 2008-12-21
still getting error 12 invaild device after makeactive

almost there...

---

### Post by northern lights on 2008-12-21
With it mounted?
Then it's not the correct partition.

Do the following:

Unmount everything```
sudo umount -a
```then mount /dev/sda4/ and post the contents. Unmount it and mount /dev/sda5/. Post its contents.

You also should not even need the "makeactive". Thus just run ```
sudo grub
grub> root(hdX,Y)
grub> setup (hd0)
grub> exit

```

---

### Post by 22Ti on 2008-12-21
sda4

/media/disk/grub
/media/disk/lost+found
/media/disk/mythtv
/media/disk/nnpro
/media/disk/tv


sda5 (this is it but it might have a privileges problem as I in grub setup (hd0) get error 17 can not mount selected device)

/media/disk-1/500gb_drive
/media/disk-1/bin
/media/disk-1/boot
/media/disk-1/cdrom
/media/disk-1/dev
/media/disk-1/etc
/media/disk-1/grub
/media/disk-1/home
/media/disk-1/initrd
/media/disk-1/lib
/media/disk-1/lost+found
/media/disk-1/media
/media/disk-1/mnt
/media/disk-1/nas2
/media/disk-1/opt
/media/disk-1/proc
/media/disk-1/root
/media/disk-1/sbin
/media/disk-1/second_drive
/media/disk-1/srv
/media/disk-1/sys
/media/disk-1/temp
/media/disk-1/TITAN
/media/disk-1/tmp
/media/disk-1/usr
/media/disk-1/var
/media/disk-1/initrd.img
/media/disk-1/initrd.img.old
/media/disk-1/reacocard.asc.1
/media/disk-1/sudo
/media/disk-1/vmlinuz
/media/disk-1/vmlinuz.old

---

### Post by northern lights on 2008-12-21
> **22Ti said:**
> this is it but it might have a privileges problem as I in grub setup (h0) get error 17 can not mount selected device
Okay. sda5 = (hd1,4) is definitely your root filesystem. The device after setup should be (h**d**0) though. Typo only here or also in the GRUB shell?
Since you're starting GRUB as root, permissions should not make a difference.

---

### Post by 22Ti on 2008-12-21
typo only here...

---

### Post by 22Ti on 2008-12-21
This is truly a pain in my ***! Why dosent sda5 mount in grub...
At it for 8 straight hours...

Thanks guys for enduring me this time

---

### Post by 22Ti on 2008-12-21
issue not solved...anybody have ideas

---

### Post by northern lights on 2008-12-21
I'm sorry man, but I'm hitting the hay. Got class at 7:30 in the morning and need read 15 pages for the weekly quiz before.

Can't come up with a reason for GRUB not handling that partition right either for now.

Good luck & Good Night. I'll check back tomorrow.

---

### Post by 22Ti on 2008-12-21
thx for the help, I hope it will be done by then but if not Ill see you tomorrow.

---

### Post by 22Ti on 2008-12-21
FINALLY got it to work with supergrubdisk. Couldnt burn it as I only have one drive (live cd in it) couldn't use usb to boot as my bios dosent support it and cant boot into xp as I burned that bridge earlier in this thread. I finally found an old computer that apparently had a burner!

After playing with supergrubdisk and not understand what the F I was doing it just started to work perfectly with one exception:

After splash screen I get a flashing "_". So I hit alt+F1 and se something like cannot load sda7, rename or hit enter to boot. If you hit enter the system boots normally but I REALLY want to get rid of this so it loads directly...any ideas??

---

### Post by Jammanuser on 2008-12-21
> **northern lights said:**
> 
[COLOR="Red"]sda4 translates to (hd1,3)[/COLOR] and sda5 to (hd1,4) in GRUB syntax. (hd1,5) is your swap partition. Hence the "invalid device"


Wouldn't it be (hd**0**,3)? I think that's what "sda4" actually is...at least, that's what it is on mine! ;)

Cheers! ):P

-Jam man

:guitar:

---

### Post by northern lights on 2008-12-21
> **Jammanuser said:**
> Wouldn't it be (hd**0**,3)? I think that's what "sda4" actually is...at least, that's what it is on mine! ;)

He's got an *hdb* though, which your setup hasn't.

@the OP: Finally, man!

---

### Post by TeXtonyx on 2008-12-22
Re: Help! No GRUB! :s
Quote:
Originally Posted by Jammanuser 
Wouldn't it be (hd0,3)? I think that's what "sda4" actually is...at least, that's what it is on mine!

-----------------------------------------------

northern lights replied:
He's got an hdb though, which your setup hasn't.

------------------------------------------------

I haven't read the whole thread, but on the first page I noticed
something that wasn't immediately corrected. For his grub entry,
OP used " root (hd1,5) "
but his Linux 83 partition is on /dev/sdb5, and that is *(hd1,4)*
and that is why he got the "invalid device requested"
In fdisk notation, the 5 after sdb5 or the 1 after sda1, is the
partition number. But in grub notation, the numbering starts at
0 for the first partition, thus sdb1=(hd1,0) and sdb5= *(hd1,4)*^
Drives in grub also start at 0. The numbering caused the error.

sda2=(hd0,1) ; sdb3=(hd1,2) ; sdc6=(hd2,5) and so on

Maybe this issue was corrected later on but in case it wasn't
I decided to mention it in case it has a bearing now. I'm not
saying that his choice of using sdb was the right one, just
making a point about what caused the error.

--------------------------------------------------

/dev/sdb1 1 9733 78180291 5 Extended
/dev/sdb5 1 9733 78180259+ 83 Linux <----- [where root is]

root (hd1,5) <-- [should be (hd1,4) because sdb5 = (hd1,4)]
setup (hd0)
quit

but at the setup I get:

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,5)/boot/grub/stage
2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested

TeX: The reason is that you used the wrong root "(hd1,5)" If 
you wanted to use sdb for the root, it should have been (hd1,4),
because sdb5 = (hd1,4).

---

### Post by northern lights on 2008-12-22
> **TeXtonyx said:**
> I haven't read the whole thread...Says it all.

Thanks for the effort, however completely redundant.

Please use quote tags for quoting.

---

