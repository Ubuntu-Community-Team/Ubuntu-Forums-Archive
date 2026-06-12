---
title: "Help a poor noob with permissions."
date: 2005-12-13
forum: General Help
---

### Post by Supernewb on 2005-12-13
I am ultra new to Linux and not all that bad with Windows.  I want to use Linux for all the good philosophical reasons... but Im seriously thinking about going back to the evil empire as I feel learning chinese from fortune cookies would be simpler at this point.

So please help a poor newb with good intentions.  And if the questions seem stupid, please be patient.  Just remember that at one point in your life, a *kernel* meant the guy on a KFC box for you too. 

My problem is basically this: I dont have permission to do anything.  

First of all, my desktop displays two icons, most likely hardrives (called hda1, and hda5).  I actually have one physical hardrive in my computer, with 4 partitions, 2 for winxp, one for linux, and one called a swap (installed by default, I think, by Ubuntu for god knows what).  Both of those hardrives are about 20GB each.  That is odd, because I only assigned one 20gb partition for linux (ext3 file system, does that make sense:confused: ).  I wonder why its disaplying two hardrives.  Why isnt it showing my other 60gb main windows partition, for exemples.  Its not that I want to have access to it from linux, but if its diplaying one windows partition, then why not both. Anywho... thats the least of my worries right now.  If your not bored to death, please go on reading.

If I double click on either of those HD icons on the desktop, I am told <<the folder content cannot be diplayed>>.  It seems I don't have permission to even view the content of my hardrives.  When I right click on the icon, and go to properties, and go to the <permissions> tab, I cant change anything (and a message at the bottom says that I'm not the owner.  I wonder who is :confused: 

I also wanted to change the priority in Grub to boot from my other operating system by default. I cant edit the menu.lst in the root/grub directory.  I dont have permission, and cant change permissions either.

I downloaded a game from the internet. The file appeared on my desktop.  that time I was able to change the permissions by rightcliking, a great moment if my linux life :p .  The program actually started to install (another triumph), but at the end it told me that I dont have permissions to complete the install... arghh...etc... etc...

To sum it up: I have read ubuntu user manuals and tried to <run as diffrent user> root, but to no avail.  I either get no confirmation that I am now under root, or it doesnt change anything, or some error message about some <child> no 178 appears.  I have a child :confused:

If you want to help, please know this: I am the epitomy of a noob.  Dont assume that I even know what a kernel is (i don't, and I am starting to think that my life was simpler before I knew there was life beyond the evil m$ empire).  I can only guess what a terminal is for: when I open it up, I get terrible flachbacks of the entire days I would spend on my commodore 64 typing in codes in basic just to see a dot cross the screen or change color.  (Please dont hate me, but I actually think a GUI is a giant leap for mankind).

So... can anyone help, or should I just go back to the numbfull bliss of windows (I would put a question mark here, but, you guessed it, I cant configure it for my keyboard).

Thanks.

---

### Post by kairu0 on 2005-12-13
To sort out this problem, the first thing you will have to do is sort out how your hard drive is partitioned. You said that you have 2 Windows partitions (20gb and 60gb unless I'm mistaken), one Linux partition (20gb and ext3), and a swap partition. To sort out this mess, open up a Gnome terminal and type:

```
sudo fdisk /dev/hda
```

Type your user's password. Next, type "l" and push enter.

This should give you a breakdown of your hard drive's partitioning. Select all of the information with the mouse, and copy and paste it into this thread.

---

### Post by aysiu on 2005-12-13
[QUOTE=Supernewb]
I have read ubuntu user manuals

If you want to help, please know this: I am the epitomy of a noob.[/QUOTE] These two statements (along with the partition and grub stuff) made me think you really need to read this:
[http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide_05.12.pdf)

You're the target audience.

After your shot at Ubuntu, if the command-line scares you off, you should seriously consider Mepis--it's entirely point-and-click.

---

### Post by Supernewb on 2005-12-13
Hi.  Thanks for trying to help.  I'm not sure I'm doing things right, but here is what I got anyways:

After entering my password, I got this:

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Then, I pressed * l * and got this:

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT


I'm afraid to ask: does this make sense

---

### Post by rykel on 2005-12-13
[QUOTE=Supernewb]I am ultra new to Linux and not all that bad with Windows.  I want to use Linux for all the good philosophical reasons... but Im seriously thinking about going back to the evil empire as I feel learning chinese from fortune cookies would be simpler at this point.

So please help a poor newb with good intentions.  And if the questions seem stupid, please be patient.  Just remember that at one point in your life, a *kernel* meant the guy on a KFC box for you too. 

My problem is basically this: I dont have permission to do anything.  [/QUOTE]

i might be wrong, but there are essentially two places in ubuntu linux where u can modify the permission levels for the files. one would be the right-click on each file, and the other would be the **fstab** file in /etc/fstab.

for the right-clicks to work, you might have to:
[INDENT]1. open a terminal.
2. use **sudo nautilus** to launch a root file manager.
3. right-click any file and change its user/group/permissions.[/INDENT]

as for setting up fstab, please refer to the unofficial **[ubuntu guide]("http://www.ubuntuguide.org")**.

> 
First of all, my desktop displays two icons, most likely hardrives (called hda1, and hda5).  I actually have one physical hardrive in my computer, with 4 partitions, 2 for winxp, one for linux, and one called a swap (installed by default, I think, by Ubuntu for god knows what).  Both of those hardrives are about 20GB each.  That is odd, because I only assigned one 20gb partition for linux (ext3 file system, does that make sense:confused: ). 

well, i would suggest tat u use reiser file system (reiserfs) the next time. the swap is the equivalent of the windows virtual memory file, only that it is more reliable in terms of "remembering" things, since it is placed in a partition of its own. a 1GB swap partition is sufficient for practically anything.

hda1 and hda5 are probably your two windows NTFS/FAT32 drives, to which you have assigned a mount point when installing ubuntu, since by default, your linux and swap partitions will NOT be displayed on your desktop.

if the two icons are NOT your windows partitions, and you have verified it by actually opening them up to see wat they contain, AND you find your linux folders (such as **boot, var, etc, usr** etc. in them, then indeed something weird is going on.

looking at your next statements below, the two icons are in fact your two windows partitions, so linux has done its job correctly and well.

> 
I wonder why its disaplying two hardrives.  Why isnt it showing my other 60gb main windows partition, for exemples.  Its not that I want to have access to it from linux, but if its diplaying one windows partition, then why not both. Anywho... thats the least of my worries right now.  If your not bored to death, please go on reading.

If I double click on either of those HD icons on the desktop, I am told <<the folder content cannot be diplayed>>.

as i mentioned, the two icons ARE in fact your windows partitions then. reason why they cannot be displayed is tat their permissions are set to allow only the linux root user access.

to access both partitions, use **sudo gedit /etc/fstab** in a terminal to bring up **fstab** file as root.

then either change or add the following two lines to it:

[INDENT][B]/dev/hda1       /media/windows1  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/windows2  vfat    iocharset=utf8,umask=000   0       0[/B][/INDENT]

just make sure tat the hda1/5 corresponds correctly. the first line is for NTFS (usually C:\) and the second for FAT32. (usually D:\)

> 
It seems I don't have permission to even view the content of my hardrives.  When I right click on the icon, and go to properties, and go to the <permissions> tab, I cant change anything (and a message at the bottom says that I'm not the owner.  I wonder who is :confused: 

I also wanted to change the priority in Grub to boot from my other operating system by default. I cant edit the menu.lst in the root/grub directory.  I dont have permission, and cant change permissions either.

like i mentioned above, open a terminal and launch your file manager using **sudo nautilus**.

> 
I downloaded a game from the internet. The file appeared on my desktop.  that time I was able to change the permissions by rightcliking, a great moment if my linux life :p .  The program actually started to install (another triumph), but at the end it told me that I dont have permissions to complete the install... arghh...etc... etc...

if your game is available as an **[autopackage]("http://www.autopackage.org")**, download tat and install! autopackages allow you to install a game easily, resolving any dependency problems AND as a user if you do not have system password.

you will love autopackage, trust me.

> 
To sum it up: I have read ubuntu user manuals and tried to <run as diffrent user> root, but to no avail.  I either get no confirmation that I am now under root, or it doesnt change anything, or some error message about some <child> no 178 appears.  I have a child :confused:

If you want to help, please know this: I am the epitomy of a noob.  Dont assume that I even know what a kernel is (i don't, and I am starting to think that my life was simpler before I knew there was life beyond the evil m$ empire).  I can only guess what a terminal is for: when I open it up, I get terrible flachbacks of the entire days I would spend on my commodore 64 typing in codes in basic just to see a dot cross the screen or change color.  (Please dont hate me, but I actually think a GUI is a giant leap for mankind).

i absolutely agree with you... BUT, however, we have to live with the fact tat linux IS a commandline OS. its relationship to the GUI is very much like DOS and Windows 3.11. ie. the GUI is a layer on top of the commandline.

of course, tremendous efforts are going in all directions to enhance all the GUI-based linux programs so tat they are able to iconise all the functions available to a commandline command. some great examples of GUI tat has already captured all possible options in their commandline command would be ***Synaptic Package Manager***.

> 
So... can anyone help, or should I just go back to the numbfull bliss of windows (I would put a question mark here, but, you guessed it, I cant configure it for my keyboard).

Thanks.

well, hope i have helped you. took me abt 20 minutes to draft this message!!

and hope you graduate from noob to intermediate soon... coz your linux experience will become much sweeter.    =)

---

### Post by kairu0 on 2005-12-13
[QUOTE=Supernewb]I'm afraid to ask: does this make sense[/QUOTE]

My bad! I meant "p", not "l".

---

### Post by Supernewb on 2005-12-13
Hi.  

I'm impressed with the help I am getting (and very thankful).  I'm in the process of reading rykel's answer.  In the mean times, heres what I'm getting when I follow Kairuo's instructions

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          65        9522    75971353+   7  HPFS/NTFS
/dev/hda2            9523       12399    23109502+   f  W95 Ext'd (LBA)
/dev/hda3               1          64      514048+  82  Linux swap / Solaris
/dev/hda4           12400       14593    17623305   83  Linux
/dev/hda5            9523       12399    23109471    7  HPFS/NTFS

Partition table entries are not in disk order

Tx again.

---

### Post by tiresias on 2005-12-13
Thank you, Rykel!  That was very helpful to me too!

[QUOTE=rykel][B]/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000   0       0[/B][/QUOTE]

The meaning of the first three parameters on each line is clear:  the first one (**/dev/hda1** for instance) is the name by which the system knows that partition, the second (**/media/windows** for instance) is the directory at the mounting point, and the third (**ext3** or **ntfs**, say) is the partition type.

Two questions:
[list=1][*] Won't there be a problem if you try to mount two different partitions to the same directory as in the example above?
[*] More importantly, could someone quickly explain the meaning of the last three parameters?  The **fstab** file calls them: **options**, **dump** and **pass**.  ("**Pass**" as in "password"???)[/list]

---

### Post by Supernewb on 2005-12-13
Hi Rykel.

Great help.  After days of searching on the web, Im finally starting to get answers.  By doing the sudo nautilus thing, I was able to browse both HD and figure out that they are, indeed, my two windows partitions.  I guess they have been <mounted>.  I'll try to figure out how I can unmount them.  

I'll keep reading.  tx.

---

### Post by tiresias on 2005-12-14
[QUOTE=Supernewb]I guess they have been <mounted>.  I'll try to figure out how I can unmount them. [/QUOTE]

I am a noob too, but from my experiments of the last fifteen minutes, it seems that, to unmount them, you can just "comment out" the two lines that correspond to each of them in the **/etc/fstab** file.  (To "comment these lines out", simply add a **#** at the beginning of each of these two lines.)

---

### Post by tiresias on 2005-12-14
[QUOTE=Supernewb]By doing the sudo nautilus thing[/QUOTE]

By the way, in the **Applications** menu at the top left corner of the screen, go into **System tools**:  you'll find a GUI version of **sudo**, through which you can launch any application as *root*...

---

### Post by rykel on 2005-12-14
[QUOTE=tiresias]Thank you, Rykel!  That was very helpful to me too![/QUOTE]

you are VERY WELCOME!!! i love linux, and i love to help people.    :) 

> 
Two questions:
[list=1][*] Won't there be a problem if you try to mount two different partitions to the same directory as in the example above?
[*] More importantly, could someone quickly explain the meaning of the last three parameters?  The **fstab** file calls them: **options**, **dump** and **pass**.  ("**Pass**" as in "password"???)[/list]

thanks for pointing out my mistake! i have edited my initial post. yes, it should be "windows1" and "windows2" or watever names u give to your two windows partions. SUSE simply calls them "c" and "d", which i kind of like.

as for the parameters, i am afraid i do not know much about them. fstab is still a mystery to me!   hehe

---

### Post by amohanty on 2005-12-14
> More importantly, could someone quickly explain the meaning of the last three parameters? The fstab file calls them: options, dump and pass. ("Pass" as in "password"???)

Some useful docs:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Unix manfile:
[http://unixhelp.ed.ac.uk/CGI/man-cgi?fstab+5](http://unixhelp.ed.ac.uk/CGI/man-cgi?fstab+5)

HTH

---

### Post by RAOF on 2005-12-14
"Options" is just that - the options for mounting the filesystem.  Like read-only.  These options are (unfortunately) specific to each of the filesystem types.  The most important ones are:
*) defaults - (everything) most options will start with this one

*) umask=xxxx - (ntfs,vfat) This determines the access restrictions for files & directories on the partition.  Particularly important, since these filesystems don't have support for permissions themselves.  The 4 numbers mean, in order -

Something technical that should always be 0
What permissions **not** to give to the owner of the files
What permissions **not** to give to the group who owns the files
What permissions **not** to give everyone else.

Each of these digits is given by the sum of the permissions.  "4" is read, "2" is write, "1" is execute.  Add up the numbers corresponding to the permissions, and that is your digit.  So 6 = 4+2 corresponds to "read & write".  7 = 4+2+1 corresponds to "read,write,execute".  Because the umask deals with what permissions **not** to give, umask=0000 corresponds to give everyone everything, and umask=0777 corresponds to give everyone nothing.
*) user - (everything) allow an ordinary user to mount the partition.  Ordinarily, only root can mount a partition.
*) users - (everything) same as above, but the user who mounted it can also unmount it.
*) fmask=xxxx - (ntfs,vfat) like umask, but only for the files.
*) dmask=xxxx - (ntfs,vfat) like umask, but only for the directories.
*) uid= - (everything, I think) set the id of the owner of everything on the partition.
*) gid= - (everything, I think) set the id of the group who owns everything on the partition

"Dump" and "Pass" should be zero, for anything you add to fstab.  I'm not sure what "Dump" does, and has always been 0 for everything I've seen.  "Pass" corresponds to the order in which partitions should be checked on startup.  The root partition (the one mounted at /) should be checked first, and have 1 here.  0 here means "do not check at startup"

---

### Post by carlosqueso on 2005-12-14
supernewb:  

I had a similar problem.  You first need to type (in a terminal) ```
sudo umount /media/hda1
sudo umount /media/hda5
``` this unmounts both of them. They should both disappear.

Then, type ```
sudo gedit /etc/fstab
```
and in the file, make sure the entries for the drives look like this:
```
/dev/hda1 /media/windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/windows2 ntfs nls=utf8,umask=0222 0 0
```

then go back into the terminal and type ```
sudo mount -a
``` and you should be able to read your windows partitions.  Unfortunately, while you can theoretically write to ntfs partitions, it has the potential to destroy your data, so you use umask=0222 to prevent you from accidentally doing that.

---

### Post by tiresias on 2005-12-14
Thanks, you all!  I know this wasn't my thread to start with but all these explanations are greatly helpful to me too.  I've been on Ubuntu for just under two weeks, and I'm starting to feel that it was really worth it!

---

