---
title: "New Install"
date: 2009-06-20
forum: General Help
---

### Post by Quarkrad on 2009-06-20
Sorry for basic question.  I'm have trouble with my grub/boot and spending a lot of time going round in circles - it still will not boot.  If I reinstall from a live CD over the top of my existing ubuntu system what will happen?  Will it over write everything and I have a new system or will it get me back to my old system?  Existing broken system is 9.04 - should I use 9.04 live CD or can I use a 8.10 live CD?   (Tried using alternate CD and repairing/rebuilding grub but at the last stage it said something about a serious error and would go no further).

Thanks.

---

### Post by Ian_F on 2009-06-20
When install 9.04 you can tell it to wipe everything and start over.

---

### Post by Dysport on 2009-06-20
If you install Ubuntu again you will lose your old files and end up with a fresh install. If you want to, you can back up your old data in live mode on an external drive.
What's the exact problem with your GRUB? Have you tried [Super GRUB Disk]("http://www.supergrubdisk.org/") yet?

---

### Post by thegreenblob on 2009-06-20
If you boot up the live cd and install it will overwrite your previous install and be like a fresh install. Unless you tell it to resize the partitions instead of format the drive, which would make a dual boot.

And I would assume you could do this with 8.10 or 9.04.

Is there any specific error your getting at boot?

---

### Post by Quarkrad on 2009-06-20
Thank you for replies - appreciated.  No luck with Supergrub.  I was/am new to Ubuntu since 8.10 -recently upgraded to 9.04.  I have played with trying to get a graphical grub (no luck) ad on travels discovered the files in /boot/grub   I use to have two grub folders in /boot/   grub and grub.old  (Grub was the new graphical grub and grub.old the orginal.  When I couldn't get it to work I renamed the grub folders so /boot/grub/ was the original folder with all the files including menu.lst and stage1 and stage2.  My system has been booting OK for a couple of weeks.  Suddenly this morning nothing - all I get is error2 at the grub window.  If I boot up via live CD and enter gksudo nautilus and go to File System/boot/  there are no grub folders - this makes me think either I am looking in the wrong place.  Is this the live CD /boot/ or 'my system' /boot/ folder?  Actually something else is happening now.  In terminal:

sudo grub
grub> find /boot/grub/stage1
(hd0,0)
grub> setup (hd0)
Error 12: Invalid device requested
grub>

When I did these commands months ago to set up my dual boot system it worked every time.  My Ubuntu partition is sda1

---

### Post by Bucky Ball on 2009-06-20
Yea, probably looking at the CD.

I know it is difficult, but can you post any details of the grub you are trying to boot from? The menu.lst specifically? Perhaps just looking in the wrong place for the device because of changes.

---

### Post by Quarkrad on 2009-06-20
I'm not sure how to 'see' my old ubuntu system from the live CD desktop.  When I type sudo su root in the terminal and then fdisk -lu I get:

root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd800c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19535039     9767488+  83  Linux
/dev/sda2   *    19535040    60500789    20482875    7  HPFS/NTFS
/dev/sda3        60500790   781417664   360458437+   5  Extended
/dev/sda5        60500853    80983664    10241406    7  HPFS/NTFS
/dev/sda6        80983728   132198884    25607578+   7  HPFS/NTFS
/dev/sda7       132198948   375904934   121852993+   7  HPFS/NTFS
/dev/sda8       375904998   427120154    25607578+   7  HPFS/NTFS
/dev/sda9       427120218   730218509   151549146    7  HPFS/NTFS
/dev/sda10      730218573   750701384    10241406    7  HPFS/NTFS
/dev/sda11      750701448   773015669    11157111    7  HPFS/NTFS
/dev/sda12      773015733   781417664     4200966    7  HPFS/NTFS

so my Ubuntu partition is there - /dev/sda1 

but how do I access it from the live CD terminal?  When I type gksdo nautilus all I can see is the live CD part of Ubuntu - not sda1.  If I could access/see it I could get to boot/grub and check my files (menu.lst)

---

### Post by Bucky Ball on 2009-06-20
Ah, ha! The age old nightmare. You have Linux installed on the first partition of the first drive, exactly where Windows wants to be or it will get confused.

Which means you need to trick it in the menu.lst. Can you post the Windows entry from:

/boot/grub/menu.lst

... please?

SuperGrubDisk might fix things for you automatically:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

You might also try something like this for your Windows entry in menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 95/98/Me
root        (hd1,0)
savedefault
makeactive
map        (hd0,1)
map        (hd1,0)
chainloader    +1
```Not sure if that will work, but it is something along those lines.

The concept is on this page under the heading  ******Chainloading ****Windows on a non-first hard disk**, but you are looking at Windows on the non-first partition, not drive, .

[http://members.iinet.net.au/~herman546/p15.html#Windows_on_a_non-first_hard_disk]("http://members.iinet.net.au/%7Eherman546/p15.html#Windows_on_a_non-first_hard_disk")

---

### Post by Quarkrad on 2009-06-20
The problem is I cannot access my ubuntu system and/or any of its files.  When I boot the pc, after bios boot section, the screen goes black and text comes up - as normal:
Grub loading, stage 1.5
Grub loading, please wait


normally after a few seconds I get the ubuntu list to choose to boot to with winxp at the bottom of the list.  The problem is that this list does not appear.  All I get after Grub loading, please wait .... is:
Error 2

So ....  I cannot boot into my system.  If I could access my old ubuntu via the live CD I could check the files in /boot/grub/   - but I do not know how to access my old ubuntu via the live CD.

---

### Post by themusicalduck on 2009-06-20
If you have an Ubuntu install CD handy, you need to boot into the CD as if you were re-installing. A menu will come up and you need to select 'Try Ubuntu without any changes to your computer'. This will then take you into a live CD session.

---

### Post by Quarkrad on 2009-06-20
OK - I can get to my old files and /boot/grub/ looks OK with all the rights files.  This is the output from terminal:

grub> find /boot/grub/stage1 
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

So it looks to me that everything is OK.  When I restart the pc it will not boot to the options listed in menu.1st.  I get a black screen with the following text:

Grub loading, stage1.5                         **this is normal**
Grub loading, please wait...                   **this is normal**
Error 2                                        **this is wrong***


instead of Error 2 I use to get the menu.1st list and then boot either to Ubuntu or wnXP.

Help......

---

### Post by Bucky Ball on 2009-06-21
This might help:

[http://members.iinet.net.au/~herman546/p15.html#2_]("http://members.iinet.net.au/%7Eherman546/p15.html#2_")

You might want to have a look at that page from the top. Excellent resource for all things grub (and dual boot).

Incidentally, I don't see a swap file there for Linux. This shouldn't cause the problem you're getting though.

---

### Post by Quarkrad on 2009-06-24
Wrongly or rightly, using various tools including Super Grub Disk) I came to conclusion my file system was corrupt. So it was a hammer job - re format partition and re-install 9.04

---

### Post by Bucky Ball on 2009-06-24
And did that work?

---

### Post by Quarkrad on 2009-06-24
Yes it did:

[LIST]
[*]built 9.04 CD from iso
[*]used cd to re-format partition (hd0,0) on sda1 to ext4
[*]Installed 9.04 onto reformated partition
[/LIST]

it all works great but to my surprise when the Desktop launch it did not have a default Ubuntu Desktop Background but a winXP one!   How did that happen?  I looked in the Desktop Backgrounds folder and there it was?????????
Now removed!

I have installed Ubuntu a number of times (4 or 5) since ver 7.xxx and it has always launched with a default background - I was not expecting to see winXP!

Thanks for your help - appreciated.

---

