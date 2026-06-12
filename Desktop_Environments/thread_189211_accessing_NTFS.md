---
title: "accessing NTFS"
date: 2006-06-04
forum: Desktop Environments
---

### Post by wswswsws on 2006-06-04
Hi there, just a quick question if i may. im unable to access my NTFS windows partitions via natilus. I get the error : 

Unable to mount the selected volume :

error: device /dev/hdb1 is not removable

error: could not execute pmount


**************************************************
**************************************************
heres an output of: less /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
~
**************************************************
**************************************************

heres an output of: sudo fdisk -l


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         223     1791216    7  HPFS/NTFS
/dev/hda2             224         432     1678792+  83  Linux
/dev/hda3             433       14592   113740200    f  W95 Ext'd (LBA)
/dev/hda5             433         446      112392   82  Linux swap / Solaris
/dev/hda6             447        2996    20482843+   7  HPFS/NTFS
/dev/hda7            2997        5099    16892316    7  HPFS/NTFS
/dev/hda8            5100       14592    76252491    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5151    41375376    7  HPFS/NTFS
/dev/hdb2            5152        7872    21856432+  83  Linux
/dev/hdb3           13957       14596     5140800    5  Extended
/dev/hdb4   *        7873       13956    48869730   83  Linux
/dev/hdb5           14219       14596     3036253+  82  Linux swap / Solaris
/dev/hdb6           13957       14218     2104452   82  Linux swap / Solaris

(scary i know:P)

**************************************************
**************************************************

You mite of guessed im a complete linux noob. But im wondering if theres an easy way for me to access my NTFS files?

Let me know if any more information is required.

Thanks in advance

---

### Post by aysiu on 2006-06-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

### Post by wswswsws on 2006-06-04
thanks for the link matey, unfortunatly its all over my head. 


owell back to windows:(

---

### Post by aysiu on 2006-06-04
[QUOTE=wswswsws]thanks for the link matey, unfortunatly its all over my head. 


owell back to windows:([/QUOTE] You can type ```
less /etc/fstab
``` and ```
sudo fdisk -l
``` in the terminal, but the tutorial I pointed you to is over your head? I'm confused, unless it's just some kind of trick to get me to hand-hold you through this instead of you actually reading the link I posted.

Follow these directions then (just copy and paste them into the terminal): ```
sudo mkdir /windows_1a
sudo mkdir /windows_6
sudo mkdir /windows_7
sudo mkdir /windows_8
sudo mkdir /windows_1b
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add in these lines: ```
/dev/hda1 /windows_1a ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /windows_6 ntfs nls=utf8,umask=0222 0 0
/dev/hda7 /windows_7 ntfs nls=utf8,umask=0222 0 0
/dev/hda8 /windows_8 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /windows_1b ntfs nls=utf8,umask=0222 0 0
``` Save (Control-X), Confirm (Y), Exit (Enter). ```
sudo mount -a
``` I don't really see how that's different from what I linked to, but...

... if you still find that too complicated, consider using [Mepis](http://www.mepis.org)--as it automounts your partitions when you click on them. Contrary to what some people will tell you, Ubuntu can be a little command-line heavy in the beginning.

---

### Post by randell6564 on 2006-06-05
Like 'ayisu' said,

GO HERE: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

This is a step by step on mounting and accessing your win partition

---

### Post by 3rdalbum on 2006-06-05
I don't know if you've noticed it, but I PM'ed you a Python script that should hopefully help... never tested it on a computer with so many partitions, but I don't see why it wouldn't work.

I don't understand why you've got 3 swap partitions...

---

### Post by randell6564 on 2006-06-05
[QUOTE=wswswsws]Hi there, just a quick question if i may. im unable to access my NTFS windows partitions via natilus. I get the error : 

Unable to mount the selected volume :

error: device /dev/hdb1 is not removable

error: could not execute pmount


**************************************************
**************************************************
heres an output of: less /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
~
**************************************************
**************************************************

heres an output of: sudo fdisk -l


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         223     1791216    7  HPFS/NTFS
/dev/hda2             224         432     1678792+  83  Linux
/dev/hda3             433       14592   113740200    f  W95 Ext'd (LBA)
/dev/hda5             433         446      112392   82  Linux swap / Solaris
/dev/hda6             447        2996    20482843+   7  HPFS/NTFS
/dev/hda7            2997        5099    16892316    7  HPFS/NTFS
/dev/hda8            5100       14592    76252491    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        5151    41375376    7  HPFS/NTFS
/dev/hdb2            5152        7872    21856432+  83  Linux
/dev/hdb3           13957       14596     5140800    5  Extended
/dev/hdb4   *        7873       13956    48869730   83  Linux
/dev/hdb5           14219       14596     3036253+  82  Linux swap / Solaris
/dev/hdb6           13957       14218     2104452   82  Linux swap / Solaris

(scary i know:P)

**************************************************
**************************************************

You mite of guessed im a complete linux noob. But im wondering if theres an easy way for me to access my NTFS files?

Let me know if any more information is required.

Thanks in advance[/QUOTE]


[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)  This gives you all you need to mount partitions!

---

### Post by nocloud on 2006-06-05
hmm, when i use sudo fdisk -l, my hard drives turn up as sda instead of hda, can i use the same procedure even though my drives are sda?

---

### Post by localzuk on 2006-06-05
Why are you repeatedly saying 'go to this site' when they say the don't understand it?

---

### Post by localzuk on 2006-06-05
Yes, it will work fine. sda just means that the discs are either SCSI type or Serial ATA type (or external), rather than IDE (which is what hd represents).

---

### Post by randell6564 on 2006-06-05
[QUOTE=localzuk]Why are you repeatedly saying 'go to this site' when they say the don't understand it?[/QUOTE]

Well...

Lets see...

Because its a COMPLETE NO-BRAINER?  Because all that is required is to 'copy and paste' into the terminal?

YOU guy's, with YOUR instructions would intimidate a Pro!

I'm sorry...

This is just coming from my past headaches with trying to figure out myself how to mount my partitions!

The link that 'aysiu' first  provided ,and then I provided is the very one that got me on track!

Try it!  I just BET it works!  [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The ONLY difference is that 'wswswsws' has more partitions to mount than I did.

---

### Post by localzuk on 2006-06-05
You are obviously not used to helping people. Editing any config file can be overwhelming at first. Please don't just repeatedly say the same thing. It is not helpful.

Asking how it doesn't help and waiting a while for a response might be more useful.

---

### Post by randell6564 on 2006-06-05
[QUOTE=localzuk]You are obviously not used to helping people. Editing any config file can be overwhelming at first. Please don't just repeatedly say the same thing. It is not helpful.

Asking how it doesn't help and waiting a while for a response might be more useful.[/QUOTE]

Maybe you are right, my friend.

But then, maybe not.

The link that 'aysiu' and myself gave is JUST for those who know nothing about mounting partitions.

In this case it DOES seem like 'wswswsws' is choosing NOT to use the info that he/she has been given, (since he/she has not posted any reference to the info given) and instead is attempting to have someone mount his/her partitions FOR him/her!

In which case he/she will learn NOTHING!

Do some research. And look into the info that you are given.  It really IS fun when you figure out how to work things out!

---

### Post by aysiu on 2006-06-05
[QUOTE=localzuk]Why are you repeatedly saying 'go to this site' when they say the don't understand it?[/QUOTE] The OP started off by posting the output of ```
less /etc/fstab
``` and ```
sudo fdisk -l
``` so apparently has no problems using terminal commands.

She or he also did not state what exactly was incomprehensible about the site in question. There was no, "Well, I followed it up to about this part, but I'm not sure whether this partition name should go here..." or "What does that last command do? Should I be able to see my partition after this, because I don't."

Simply saying... > thanks for the link matey, unfortunatly its all over my head.


owell back to windows ...doesn't really help others help you.

Never mind that I *did* actually hand-hold the OP through the process in the following post.

---

### Post by wswswsws on 2006-06-05
Thanks for everyones help so far, sorry about the lack of inforamtion in my last reply, i was shattered and fed up. My first ubuntu install messed up my windows install, i had to reinstall windows, and then ubuntu again) But im going to give the info in that link another go now. And i will post my results asap:P

ps thanks aysiu, ill take your hand and try and get through:P

John

---

### Post by wswswsws on 2006-06-05
wow thanks aysiu for holding my hand, i used your guide and can now access most of my partitions, nice one! unfortunatly ill have to go back and actualy try to work out what i did:P



**************************************************************
**************************************************************
I used your code:

john@john-desktop:~$ sudo mkdir /windows_1a
Password:
john@john-desktop:~$ sudo mkdir /windows_1a
mkdir: cannot create directory `/windows_1a': File exists
john@john-desktop:~$ sudo mkdir /windows_6
john@john-desktop:~$ sudo mkdir /windows_6
mkdir: cannot create directory `/windows_6': File exists
john@john-desktop:~$ sudo mkdir /windows_7
john@john-desktop:~$ sudo mkdir /windows_8
john@john-desktop:~$ sudo mkdir /windows_1b
john@john-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
john@john-desktop:~$ sudo nano /etc/fstab
john@john-desktop:~$ sudo mount -a
john@john-desktop:~$


**************************************************************
**************************************************************

Any ideas why i cant access my 1.6GB and 20.8GB volumes?

---

### Post by randell6564 on 2006-06-05
[QUOTE=wswswsws]wow thanks aysiu for holding my hand, i used your guide and can now access most of my partitions, nice one! unfortunatly ill have to go back and actualy try to work out what i did:P



**************************************************************
**************************************************************
I used your code:

john@john-desktop:~$ sudo mkdir /windows_1a
Password:
john@john-desktop:~$ sudo mkdir /windows_1a
mkdir: cannot create directory `/windows_1a': File exists
john@john-desktop:~$ sudo mkdir /windows_6
john@john-desktop:~$ sudo mkdir /windows_6
mkdir: cannot create directory `/windows_6': File exists
john@john-desktop:~$ sudo mkdir /windows_7
john@john-desktop:~$ sudo mkdir /windows_8
john@john-desktop:~$ sudo mkdir /windows_1b
john@john-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
john@john-desktop:~$ sudo nano /etc/fstab
john@john-desktop:~$ sudo mount -a
john@john-desktop:~$


**************************************************************
**************************************************************

Any ideas why i cant access my 1.6GB and 20.8GB volumes?[/QUOTE]

Post your Fstab

---

### Post by wswswsws on 2006-06-05
hi,

******************************************
******************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /windows_1a ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /windows_6 ntfs nls=utf8,umask=0222 0 0
/dev/hda7 /windows_7 ntfs nls=utf8,umask=0222 0 0
/dev/hda8 /windows_8 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /windows_1b ntfs nls=utf8,umask=0222 0 0

******************************************
******************************************

---

### Post by randell6564 on 2006-06-05
[QUOTE=wswswsws]hi,

******************************************
******************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /windows_1a ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /windows_6 ntfs nls=utf8,umask=0222 0 0
/dev/hda7 /windows_7 ntfs nls=utf8,umask=0222 0 0
/dev/hda8 /windows_8 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /windows_1b ntfs nls=utf8,umask=0222 0 0

******************************************
******************************************[/QUOTE]


So...
Whats going on now?  everythings mounted.
here is my fstab:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0 
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/B]

hope it helps!

---

### Post by wswswsws on 2006-06-05
oops, i fixed the problem with my 2 drives not mounting. thanks aysiu, you eventually made me learn how to mount drives myself, without just copying your code:P (you mounted 5 of my drives, i mounted  the last 2)

so thanks again to everyone for their help in this thread. im now a very happy ununtu user. i feel its now time for a new thread with my latest support issue:P (jerky playback on my movie files)

---

### Post by aysiu on 2006-06-05
It wasn't over your head after all.

Congratulations on making it through.

---

### Post by darthvivi on 2006-06-05
If you think the topic creator is clueless because he doesn't understand this, I must also be because I don't understand it either. 

sudo fdisk -l:
Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         893     6751048+   b  W95 FAT32
/dev/hda2   *         894       13054    91937160    7  HPFS/NTFS
/dev/hda3           13055       15401    17743320   83  Linux
/dev/hda4           15402       15505      786240    5  Extended
/dev/hda5           15402       15505      786208+  82  Linux swap / Solaris

Disk /dev/sda: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6         497     3951990    b  W95 FAT32


my /etc/fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

My Windows XP is on hda2. In the guide on that site, the line that was edited was the same one that had Windows on it. What I just pasted doesn't have hda2 on it, so I don't know what to edit/add.

---

### Post by aysiu on 2006-06-05
Just paste these commands into the terminal: ```
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` and add this line ```
/dev/hda2 /windows ntfs nls=utf8,umask=0222 0 0
``` Save and then ```
sudo mount -a
```

Basically the idea is that the line has to be there and be correct. If the line isn't there (as in your case), you add it. If the line is there but incorrectly, you fix it.

---

### Post by darthvivi on 2006-06-05
Thank you for your extremely quick reply, that worked!

---

### Post by randell6564 on 2006-06-06
[QUOTE=darthvivi]If you think the topic creator is clueless because he doesn't understand this, I must also be because I don't understand it either. 

sudo fdisk -l:
Disk /dev/hda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         893     6751048+   b  W95 FAT32
/dev/hda2   *         894       13054    91937160    7  HPFS/NTFS
/dev/hda3           13055       15401    17743320   83  Linux
/dev/hda4           15402       15505      786240    5  Extended
/dev/hda5           15402       15505      786208+  82  Linux swap / Solaris

Disk /dev/sda: 4095 MB, 4095737344 bytes
255 heads, 63 sectors/track, 497 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6         497     3951990    b  W95 FAT32


my /etc/fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

My Windows XP is on hda2. In the guide on that site, the line that was edited was the same one that had Windows on it. What I just pasted doesn't have hda2 on it, so I don't know what to edit/add.[/QUOTE]

Hello!

Your 'fstab' is showing you that the only partitions that are mounted are your 'Linux' partitions.

Your 'fdisk -l' is showing you ALL of the partitions on your drives!

If I'm understanding you correctly, then you need to add your hda2 info to your 'fstab'.

This will do the trick: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Here is my 'fstab'.  Note my 'hda1':

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
**/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0 **
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by wswswsws on 2006-06-08
hi. unfortunatly iv had to reinstall ununtu again. (grr - why when you reinstall xp, does it mess up your ubuntu install)

But when i try to save (ctrl + s) my /etc/fstab , i get this

 [ XOFF ignored, mumble mumble. ]

why would this be?

---

### Post by randell6564 on 2006-06-08
ALWAYS...

I repeat, ALWAYS install 'Windows' FIRST!

It's just a 'Microsoft'  thing!  (no cooperation with other OS's!)

If you install windows first, you will not have a problem installing 'Linux!' (ubuntu in your case)

'Linux' will see your NTFS/Fat32 partition/partitions and act accordingly!

Just make sure that you install 'grub' on the 'MBR'. ('ubuntu' will ask where to install 'grub')

At least now you can start from the top!  (with a clean HD)

As soon as both OS's are installed, go to '/etc/fstab'  and see if your 'NTFS/Fat32'  partitions are there.

If not then you know what to do now right?

Gotta go!  I'm right in the middle of installing 'gentoo.'  (if you think that ubuntu is hard, try installing and compiling gentoo! LOL!)

Good Luck!

---

### Post by wswswsws on 2006-06-08
yep, unfortunatly i had to reinstall my winXP because it was acking for activation (even thought its corperate) So i had to install my legit xp home.

but back to my ubuntu problem.

When i try to save (ctrl + s) my /etc/fstab , i get this

[ XOFF ignored, mumble mumble. ]

why would this be?

---

### Post by randell6564 on 2006-06-09
[QUOTE=wswswsws]yep, unfortunatly i had to reinstall my winXP because it was acking for activation (even thought its corperate) So i had to install my legit xp home.

but back to my ubuntu problem.

When i try to save (ctrl + s) my /etc/fstab , i get this

[ XOFF ignored, mumble mumble. ]

why would this be?[/QUOTE]

Could you be more specific?  Please post the entire response that you get when attempting to save.

Post your 'fstab' again as well the way it looks when you try to save.

---

### Post by chalex on 2006-06-09
[QUOTE=wswswsws]yep, unfortunatly i had to reinstall my winXP because it was acking for activation (even thought its corperate) So i had to install my legit xp home.

but back to my ubuntu problem.

When i try to save (ctrl + s) my /etc/fstab , i get this

[ XOFF ignored, mumble mumble. ]

why would this be?[/QUOTE]

I'm assuming you're using the pico text editor.  The proper keystroke to save a file is Ctrl-O, which will write it to disk. Typically, you just hit Ctrl-X to exit and then it asks if you want to save.  Take a closer look at the bottom of your terminal window.

---

### Post by wswswsws on 2006-06-10
ok thanks yet again. I have now saved my fstab with "ctrl + o" 

But heres the info you requested anyway:

**************************************************
**************************************************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



**************************************************
**************************************************
**************************************************
**************************************************

  GNU nano 1.3.10             File: /etc/fstab                        Modified

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /windows_1a ntfs nls=utf8,umask=0222 0 0
/dev/hda6 /windows_6 ntfs nls=utf8,umask=0222 0 0
/dev/hda7 /windows_7 ntfs nls=utf8,umask=0222 0 0
/dev/hda8 /windows_8 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /windows_1b ntfs nls=utf8,umask=0222 0 0







                        [ XOFF ignored, mumble mumble. ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

**************************************************
**************************************************

im juts wondering why it didnt let me "ctrl + S" to save, as i did before. But not to worry:)

---

