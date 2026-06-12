---
title: "A stubborn MBR"
date: 2010-01-21
forum: Desktop Environments
---

### Post by coredeal on 2010-01-21
I have happily used Jaunty and XP for some time. Recently, however, upon booting the pc, I noticed that instead of presenting the usual dual-boot choice menu, the pc would go straightly to Ubuntu. The dual boot menu had vanished. So, no XP anymore. I was obliged to use the XP live CD to repair (i.e. correct) the MBR and have XP back. This of course wiped out all reference to Grub in MBR. Since then I have tried all possible routines but none has worked to put Grub back in its place in MBR. I know the routine was successful and this is the proof (copied from Terminal) :

grub> root (hd1,1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+17 p (hd1,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

No way. I reboot and there is no dual menu, just the XP choice.

Why would my MBR be so stubborn ? Has any of your experienced the same behavior ? Thank you for your responses.

---

### Post by quixote on 2010-01-23
Grub numbers drives oddly.  The first HD is 0.  In old grub (the one you have, if you're using Jaunty) the first partition on the first HD would be 0,0

So, are you really booting off the second partition on a second hard drive?  Possibly, what's happened is that grub has installed itself where it was told to, that just doesn't happen to be where your ubuntu partition is.

If you run in a terminal ```
$sudo fdisk -l
``` (that's "l" as in list) it will list all your drives and partitions.  You can select the output with a mouse and use Shift-Ctrl-C to copy it.  Then you can use Ctrl-V to paste it into your answer here.  That'll tell us what drives and partitions you have and which filesystems they have.

By the way, I suspect the original problem was in grub's menu.lst file, not actually the MBR, but we'll tackle all that once you have things running the way you want.

---

### Post by coredeal on 2010-01-23
Hello Quixote,

and many thanks for your assistance. Yes, I had tried hd0,0 and even hda after the setup entry, but none worked. At any rate, here is the result of fdisk -l that you suggested :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38673866

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         782     6281383+   b  W95 FAT32
/dev/sda2             783       19457   150006937+   f  W95 Ext'd (LBA)
/dev/sda5             783       19457   150006906    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x925020ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       13776   110647687+   f  W95 Ext'd (LBA)
/dev/sdb2           13777       38913   201912952+  83  Linux
/dev/sdb5               2        2228    17888346    7  HPFS/NTFS
/dev/sdb6            2229        8143    47512206    b  W95 FAT32
/dev/sdb7            8144       12708    36668331    7  HPFS/NTFS
/dev/sdb8           12709       13776     8578678+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc123cfa5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdd: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         984     7903948+   b  W95 FAT32

By the way, I do not have Win95, just Win98 to run some old but still good apps.

Meanwhile, I am testing a new routine. When I'm finished I'll post the results here. 

Thanx again.

---

### Post by coredeal on 2010-01-23
Hello again Quixote,

after reading your message again, I have one question : does Grub locate itself (when Jaunty is first installed or when sudo setup is run) :

1. in the first partition of the first hard disk (that would be where C:\ is located)

2. or  - if I have, as I have, Jaunty in its own partition on the second hard drive - does it install at the beginning of the second hard drive

3. or does it place itself in the same partition where Jaunty is installed (which in my case is the last partition of the drive) ?

I'm kind of confused now about the location. I would assume that it places itself at the very beginning of the first hard disk, where C:\ is located.

Thanx again for your time.

P.S. The other drives you see in the Terminal transcript are a USB flash drive and an external USB drive.

---

### Post by quixote on 2010-01-24
Grub can put itself in either:

++ the Master Boot Record of the hard drive (that's even before the first partition). In that case you'd type setup (hd*X*)

++ or it can reside on the same partition as the linux install. However, the latter method has issues if Linux is on a second hard drive, and that's the one you're using with root at (hd1,1).  When grub is installed to a partition, not the MBR, the setup command is: setup (hd*X*,*X*)

(By the way, all of this applies only to Jaunty.  karmic uses Grub2.  Totally different.)

The grub situation is discussed in detail [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").  See especially a couple of screens' worth down, just before "Preserving Windows Bootloader."  That page mentions SuperGrub, which can handle using a master boot record on drive 2.  I haven't used SuperGrub myself, but people who use it swear by it.  There's some discussion of it [here]("http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems"), and a download site [here]("http://forjamari.linex.org/projects/supergrub/").

Another way:  You could do "root (hd1,1)" and "setup (hd0)".  (I haven't done this myself, but I'm 99% sure it would work.)  That would write grub to the MBR of the boot disk and point to the right Linux partition.  Then it would look like you'd lost Windows.  But all you need to do is edit grub's "menu.lst" file with an entry that tells it where to find Windows:```
gksudo gedit /boot/grub/menu.lst
```

and add the lines (from the first link above)```
title WinXP # Use any title you wish, it will appear in the grub boot menu
rootnoverify (hd0,0) # This is the location of the windows partition
makeactive
chainloader +1
```

---

### Post by coredeal on 2010-01-24
Thank you, Quixote. You have been of tremendous help. I really appreciated your guidance. I'll let you know the result of the test mentioned in my last message.

---

### Post by coredeal on 2010-01-27
Hello Quixote,

after doing some testing, based your advices, I have finally arrived at a solution of the problem. Here is how : I have downloaded Super Grub Disk ver. 0.97-os1 and burned it to a CD. When booting with the latter, I was offered an array of menus, among which one that offered to repair Grub and that provided this diagnostics : "Mismatched or corrupt version of Stage1/Stage2". After accepting the correction my Grub was again in place. I am not sure what caused the mismatch or the corruption.

Bear with me now, I have one final question linked to your last message : when you write *"However, the latter method has issues if Linux is on a second hard drive, and that's the one you're using with root at (hd1,1). When grub is installed to a partition, not the MBR, the setup command is: setup (hd**X,**X)"*, and based on the information issued by fdisk -l in my message, am I correct to assume that my Grub resides in the Ubuntu partition and that it points to (hd1,1) ? This is where my perplexity arises : if in fact that were true, (hd1,1) is what I originally used to restore Grub : root (hd1,1) and then setup (hd1). But, even if the routine shown in Terminal indicated success, I did not get my dual boot menu back, just a normal Win XP boot. Also, in going through menu.lst I see that root is indicated to be (hd0,1). To sum up : if this problem comes up again, what should be the correct indication to restore grub - setup (hd1,1) or (hd0,1). Finally, am I correct to assume that my grub is located at the beginning of the Ubuntu partition, not at the beginning of HD 2 ? I very much appreciate if you could throw some light on this issue because, even if I know I can now count on the CD, I would like to have a better understanding of the context I am dealing with, not just doing things blindly. And I thank you again for your guidance and time. Sorry to have made such a long story of a small problem.

---

### Post by quixote on 2010-01-27
When you can't boot your system, it's not a small problem! :)

My answer to your question is a guess, because I'm not sure how it works myself, but, as far as I can tell, you can install grub on a partition, but there needs to be *something* in the MBR of the primary drive that points to it.  When the computer starts up, it only checks the drive MBR for further instructions, not the whole disk or any secondary disks.

Windows has a bootloader, but it doesn't like to point to anything but Windows.  There are ways to force it to see other OSes ([Preserving Windows Bootloader]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")), but why would anyone want to? ;)  When you were in the situation where you could boot Windows, but nothing else, that's because the Windows bootloader had taken over.

What Supergrub did was recreate the MBR instruction to look for grub in the right place.  (I think.)

Yes, your grub is located on the Ubuntu partition (hd1,1). Yes, that is the beginning of the ubuntu partition on HD2, not the beginning of the whole drive.

I think where the difficulty comes in is that the setup command needs to go to (hd0), the MBR of the first drive.  sd**a** is what your computer sees as the first drive.  sdb is the second, and it's not going to look there.  Therefore, pointing setup to (hd1) (=MBR of the second drive), or to (hd1,1) the ubuntu partition on the second drive, won't do anything.

The actual booting needs to be done on the second drive, but it takes drives a while to become active during the boot process, and grub doesn't expect this.  You can tell it to wait longer, but I've forgotten where I saw that.  (Supergrub, on the other hand, just deals with it.)  When you did this and the install grub command returned "success" that's because the *command* to install grub was successful.  Grub just wasn't going to work when you needed to use it.  Unix and Linux can be helpful that way. :p

What to do for the future?  Easy solution: keep the Supergrub CD in a safe place and use it if there's a problem.

Less easy (and I'm not sure whether it'll work in a multi-drive setup): figure out where exactly the setup command should point. (My guess is (hd0)), and how to tell the system to wait a bit so the second drive can come up.  And in case menu.lst also needs fixing, I would copy the current working menu.lst to a backup (eg menu-lst-supergrub.txt).  (root (hd0,1) makes no sense, but if it works, go with it!) Then, if it happens again, boot with a liveCD, any liveCD, and copy your backup over menu.lst.  Then reboot.

---

### Post by coredeal on 2010-01-27
Hello Quixote,

and thank you for taking so much time trying to figure it all out. You see, when I first installed Jaunty I loved it, probably because I hated Windows so much. Everything basic is there and works right out of the box - word processing, spreadsheet, video, etc. But I am not a person who likes to stop there. I like testing new apps, delving more into the system. And that's when Linux becomes too complicated. There is too much syntaxis to apply (even for a guy like me who has a DOS background); installing apps is adventurous - too many times you install it with Synaptic and there is no way to find a button, a name to click to run it, you just don't know where the installed application is or where the executable is. Learning Linux takes many, too many hours, and it is regrettable because it is a great system. But not for the masses. It is not simple enough. But I will continue trying, and learning, because I am an optimist. It has been a pleasure dealing with you.

---

### Post by oldfred on 2010-01-27
Computers actually are not too bright. They only can boot from whatever we tell them. The process is that the BIOS using very little code knows to jump to the MBR master boot record or first sector of a drive and do what that says. The MBR is still very small, so it just has enough code to tell it where on the hard drive to jump to to continue booting. 

The windows boot loader in the MBR looks for a partition with the boot flag (* in fdisk) set on and jumps to the PBR partition boot record or the first sector of the partition.
Lots of info on windows Vista booting and it applies to booting in general.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Grub is a little smarter than the windows boot loader and looks for additonal files to continue to boot. It also can chainboot other operating systems that have some (like windows) or all (like another grub) in the PBR.

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://www.pcguide.com/ref/mbsys/bios/bootSequence-c.html](http://www.pcguide.com/ref/mbsys/bios/bootSequence-c.html)

If you have more than one drive you can put different boot loaders in each drive and select different drives to boot from. But grub can do the same thing so it is not usually necessary, although I do it as a backup way to boot.

---

### Post by efflandt on 2010-01-28
What can make it even more confusing is that on most modern PC's it is possible to initially boot from the mbr of a drive other than the 1st primary hard drive, but that has to be configured in the BIOS (CMOS set up from the BIOS splash screen before even grub or anything else starts to boot).  And that can cause problems for some operating systems like Windows if they do not "think" they are on the primary boot drive.  So grub may have to be configured to do some drive shuffling on the fly to get some Windows versions to think they are booting from the 1st drive.

For example Linux can be installed on a USB drive with grub in the mbr of the USB drive (if you make sure it is put there), and if grub is properly configured can boot from that USB drive on different computers.  But the BIOS has to be capable of and configured to boot from USB, and sometimes you may still have to do something during boot (like press a certain key to select boot device) because the system may try to protect you from accidentally booting from a different drive than intended.

The first and only virus I ever caught (Stoned Empire Monk, or Monkey for short) was a boot sector virus spread by floppy disks (before the internet as we know it).  It infected any floppy inserted in the computer.   Things like that could also be spread by CD, DVD, or shared USB drive (autorun).

---

### Post by quixote on 2010-02-01
@efflandt: boot viruses are the pits.

@coredeal: let us know how things work out.  As to linux being complicated, any OS has a learning curve.  Once you're used to ubuntu and you find yourself going back to Windows because you have to fix something for someone, you'll find yourself sitting there saying, "My God, did I really put up with this once upon a time?" :D  Really.  It's happened to everyone I know who's used Ubuntu for any length of time.  

As to where program shortcuts go, they're not on the desktop....  They'll almost always be under one of the headings in the ubuntu start menu.  If not, programs installed through synaptic are almost always accessible through /usr/bin/ or /usr/share/bin/.  You can go to System > Preferences > Main menu, select to add an item under the heading where you want it, browse to the program, and click add.

---

