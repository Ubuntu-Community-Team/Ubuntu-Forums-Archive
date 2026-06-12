---
title: "USB pen not working after using USB Startup Disk Creator."
date: 2009-04-27
forum: General Help
---

### Post by ophysis on 2009-04-27
Hi,

After I used USB Startup Disk Creator, I tried to boot from the USB.

The system apeared to be loading and then I got a black screen with the following text:

chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'
chown: invalid group: `syslog:adm'

* Starting kernel log deamon...
chown: invalid group: `klog:klog'
chown: invalid group: `klog:klog'

(before this i don't remember what was written...
And it stoped there...

Had to turn off laptop.

Now my 8Gb pen drive doesn't seem to work.
Before it was perfect, worked great, mounting automatically when inserted, etc...
But now, Can't mount, can't format, system doesn't list it anywhere but in places > computer. But cannot mount, I get:
-----------------------------
Unable to mount location
Can't mount file
-----------------------------

The Partition Editor can't find it either.
Now I just want to format it and get it to work, but... How?

I don't know much, so I'm not sure what info to post. Ask away.

Thanks in advance

Andre

I'm on Jaunty

---

### Post by cariboo on 2009-04-27
Open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n15
```

when you plug your device in. Paste the output in your next post.

---

### Post by ophysis on 2009-04-28
Hi,

Here it is:

```

[ 8857.352357] Buffer I/O error on device sdb, logical block 0
[ 8857.354355] end_request: I/O error, dev sdb, sector 0
[ 8857.355605] end_request: I/O error, dev sdb, sector 24
[ 8857.356853] end_request: I/O error, dev sdb, sector 24
[ 8857.358355] end_request: I/O error, dev sdb, sector 0
[ 8857.359478] end_request: I/O error, dev sdb, sector 0
[ 8857.359492]  unable to read partition table
[ 8857.359656] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 8857.359778] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 8857.386109] end_request: I/O error, dev sdb, sector 0
[ 8857.387354] end_request: I/O error, dev sdb, sector 0
[ 8857.537532] end_request: I/O error, dev sdb, sector 0
[ 8857.538771] end_request: I/O error, dev sdb, sector 0
[ 8859.449462] end_request: I/O error, dev sdb, sector 0
[ 8859.450833] end_request: I/O error, dev sdb, sector 0

```

Thanks

---

### Post by ophysis on 2009-04-29
Anyone? :)

---

### Post by timcredible on 2009-04-29
i made a live usb a couple days ago with 9.04, it works fine, i used it to install 9.04 on 4 different machines already.  so, maybe just re-try it?  also, i didn't use a cd as the source when i ran the program to create the live usb drive, i used the .iso file, not sure if that makes a difference.

---

### Post by shel-hall on 2009-04-29
> **ophysis said:**
> Anyone? :)
I had a 4GB USB key decide to quit booting, even when it was properly formatted and the boot flag set.  After much fooling around, I managed to restore it by using the key manufacturer's "Remove U3" repartitioning and reformatting tool.  Unfortunately, it's a WinXP app.  I got it from a link on the U3.com website ([http://www.u3.com/support/default.aspx#CQ3](http://www.u3.com/support/default.aspx#CQ3)), I think.

After running the U3 tool (which doesn't actually care if the U3 stuff is on the key), I used Ubuntu's "gparted" to create an ext2 partition on the key.  After that, I was able to re-load 8.10 on the key, boot, run, etc.

-Shel

---

### Post by ophysis on 2009-04-30
> **timcredible said:**
> i made a live usb a couple days ago with 9.04, it works fine, i used it to install 9.04 on 4 different machines already.  so, maybe just re-try it?  also, i didn't use a cd as the source when i ran the program to create the live usb drive, i used the .iso file, not sure if that makes a difference.

I tried to re-try it, although the "usb startup disk creator" can see the pen it can't format it. Nor can GParted, does't even show it.

I used the iso file as well.

Now I just want the pen back, don't care about having Ubuntu on it.

Thanks

---

### Post by ophysis on 2009-04-30
> **shel-hall said:**
> I had a 4GB USB key decide to quit booting, even when it was properly formatted and the boot flag set.  After much fooling around, I managed to restore it by using the key manufacturer's "Remove U3" repartitioning and reformatting tool.  Unfortunately, it's a WinXP app.  I got it from a link on the U3.com website ([http://www.u3.com/support/default.aspx#CQ3](http://www.u3.com/support/default.aspx#CQ3)), I think.

After running the U3 tool (which doesn't actually care if the U3 stuff is on the key), I used Ubuntu's "gparted" to create an ext2 partition on the key.  After that, I was able to re-load 8.10 on the key, boot, run, etc.

-Shel

Hi Dude,

I shall give it a go when I get my hands on a windows machine. Probably at work or so.

Anyone else with good ideas? I would love to sort it out with the almighty ubuntu.

Thanks

---

### Post by ophysis on 2009-04-30
Anyobody who can help?

---

### Post by ophysis on 2009-05-03
Anyone out there...?

:(

---

### Post by edujose on 2009-05-03
Hi, to format your USB pen drive you can follow the steps in post #3 in this thread: [http://ubuntuforums.org/showthread.php?t=1105038]("http://ubuntuforums.org/showthread.php?t=1105038"). From the output of your dmesg in a previous post it seems your USB pen is seen as drive sdb, so the command to type in a terminal would be

sudo mkfs.vfat -F 32 /dev/sdb

If this does not work, you can try downloading and using the 'unetbootin' program as said in post #7 from thread [http://ubuntuforums.org/showthread.php?t=1116267]("http://ubuntuforums.org/showthread.php?t=1116267"). You must have winXP or Vista to use this program, though.

Hope that helps.

---

### Post by ophysis on 2009-05-04
> **edujose said:**
> Hi, to format your USB pen drive you can follow the steps in post #3 in this thread: [http://ubuntuforums.org/showthread.php?t=1105038]("http://ubuntuforums.org/showthread.php?t=1105038"). From the output of your dmesg in a previous post it seems your USB pen is seen as drive sdb, so the command to type in a terminal would be

sudo mkfs.vfat -F 32 /dev/sdb

If this does not work, you can try downloading and using the 'unetbootin' program as said in post #7 from thread [http://ubuntuforums.org/showthread.php?t=1116267]("http://ubuntuforums.org/showthread.php?t=1116267"). You must have winXP or Vista to use this program, though.

Hope that helps.

Thanks for your post.

But it doesn't help because it assumes I can format my pen.
My problem now is that I can't get it formated.
If I try:

sudo mkfs.vfat -F 32 /dev/sdb

I get

```
~$ sudo mkfs.vfat -F 32 /dev/sdb
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdb' (use -I to override)
```

And then:
```
:$ sudo mkfs.vfat -I /dev/sdb
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: failed whilst writing reserved sector
```

Tried GParted, it doesn't detect it.
With XP I was unable to format the thing as well (but I will try again).

It's pissing me off that I can't get my 8Gb pen back. It's new and it was working perfect just before the "USB Startup Disk Creator" incident.

Hope someone out there can help.

Thanks 

Andre

---

### Post by Niniel on 2009-05-04
You can't format it in Windows?
What have you tried to do so far? Just Format it in Explorer?
XP can also partition drives (just not format them in ext2/3 or anything like that).
Go to Start > Control Panel > Performance and Maintenance > Administrative Tools > Computer Management > Storage > Disk Management and see if you can delete the existing partition on your stick from there, and then create a new fat32 one on it.

---

### Post by edujose on 2009-05-04
Hi ophysis, sorry I didn't undertand you formerly .

So the problem seems to be your pen has lost its partition table (overwritten or corrupted when using USB Startup Disk Creator), so it shows no partitions. Correct me if this is not the case.

Well, in case the partition table is lost, you can recreate it with linux's fdisk command. It's a command-line program, but interactive -once you execute it, it allows one-letter commands to perform its various tasks-. It looks complicated, but it isn't so: just keep in mind that all operations you perform with fdisk on the pen drive don't take effect until you commit them to the pen with the 'w' (write) command. In case something goes wrong, you can just type 'q' to exit fdisk without saving any changes you made.

Here are the steps you can take to recreate your pen drive's partition table and partition, and give the latter a proper filesystem (what's called "formatting the partition" in windows land).

To begin with, run in a terminal (assuming your pen drive is 'sdb' for your computer):

sudo fdisk /dev/sdb

once done, you are presented with some info about your drive (usually warnings, happen even in right-functioning pen drives) and then a prompt like this:

Command (m to get help):

You can type 'm' (without the quotes) to see the list of possible commands. After that, type 'p' to print the current partition table on your drive. You can select the text with the mouse and go to Edit | Copy in the terminal window to copy and then post it here -it's the info about the bad partition table-.

Then create a new partition table using the command 'o'. After that command, use 'p' again to print the new partition table of your pen drive and add it to the post (to see the differences with the old, seemingly corrupt one-).

Now create a new partition using the command 'n' (new partition). The program asks if you want an extended (e) or primary (p) partition, type 'p' (primary). Then it asks the partition number (between 1 and 4), type '1' (it's the firt one). After that, it asks for the first and last cylinders of the new partition, type the default values it offers.

Type 'p' to see the partition table and its new partition at the bottom; it's /dev/sdb1, and is listed as having type'Linux'. We are going to change it to be of type w95 FAT32 (LBA); you can press 'l' (list) to see the partitions fdisk knows about -ours is identified with hexadecimal value c). Now, to change the partition type press 't', and when asked by the hexadecimal code to employ, type 'c'. Then type 'p': now the partition is of type FAT32 (LBA).

After all this, at the prompt type 'w' (write partition table to pen drive and exit the program).

Then just issue the command

sudo mkfs.vfat -F 32 /dev/sdb1

to make the file system in the first (and only) partition of the pen drive, /dev/sdb1. This is the comand I did wrongly show in my prev post, and you're right: it just "formats" a partition with the given file system type (FAT32 filesystem for a FAT32 partition). Me bummer! :-)

Now your pen drive should be mountable, visible by gparted, nautilus and any other program.

Hope this is of any help. If you have doubts or problems, just ask here.

---

### Post by ophysis on 2009-05-05
> **Niniel said:**
> You can't format it in Windows?
What have you tried to do so far? Just Format it in Explorer?
XP can also partition drives (just not format them in ext2/3 or anything like that).
Go to Start > Control Panel > Performance and Maintenance > Administrative Tools > Computer Management > Storage > Disk Management and see if you can delete the existing partition on your stick from there, and then create a new fat32 one on it.

No, can't format in Windows. Tried explorer (does nothing), disk management (drive greyed out), some other apps, all no go.

Thanks for the suggestions, though. I'll try anything.

Andre

---

### Post by ophysis on 2009-05-05
> **edujose said:**
> Hi ophysis, sorry I didn't undertand you formerly .

So the problem seems to be your pen has lost its partition table (overwritten or corrupted when using USB Startup Disk Creator), so it shows no partitions. Correct me if this is not the case.

That's right, that seems to be the problem. And one of the blocks or sections (whatever) doesn't seem to be readable or inaccessible.

> **edujose said:**
> Well, in case the partition table is lost, you can recreate it with linux's fdisk command. It's a command-line program, but interactive -once you execute it, it allows one-letter commands to perform its various tasks-. It looks complicated, but it isn't so: just keep in mind that all operations you perform with fdisk on the pen drive don't take effect until you commit them to the pen with the 'w' (write) command. In case something goes wrong, you can just type 'q' to exit fdisk without saving any changes you made.

Here are the steps you can take to recreate your pen drive's partition table and partition, and give the latter a proper filesystem (what's called "formatting the partition" in windows land).

To begin with, run in a terminal (assuming your pen drive is 'sdb' for your computer):

sudo fdisk /dev/sdb

After doing that, I get this:
```
~$ sudo fdisk /dev/sdb

Unable to read /dev/sdb

```

But if I do sfdisk, I get the following:
```
~$ sudo sfdisk /dev/sdb
[sudo] password for dreani: 
Checking that no-one is using this disk right now ...
BLKRRPART: Input/output error
OK

Disk /dev/sdb: 7648 cylinders, 64 heads, 32 sectors/track
read: Input/output error

sfdisk: read error on /dev/sdb - cannot read sector 0
 /dev/sdb: unrecognised partition table type
Old situation:
No partitions found
Input in the following format; absent fields get a default value.
<start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
Usually you only need to specify <start> and <size> (and perhaps <type>).

/dev/sdb1 :

```

I have no clue about what to write in there. I have tried different things after reading "man sfdisk", the dsmeg output changes but I get nowhere closer. Any suggestions?

> **edujose said:**
> once done, you are presented with some info about your drive (usually warnings, happen even in right-functioning pen drives) and then a prompt like this:

Command (m to get help):

You can type 'm' (without the quotes) to see the list of possible commands. After that, type 'p' to print the current partition table on your drive. You can select the text with the mouse and go to Edit | Copy in the terminal window to copy and then post it here -it's the info about the bad partition table-.

Then create a new partition table using the command 'o'. After that command, use 'p' again to print the new partition table of your pen drive and add it to the post (to see the differences with the old, seemingly corrupt one-).

Now create a new partition using the command 'n' (new partition). The program asks if you want an extended (e) or primary (p) partition, type 'p' (primary). Then it asks the partition number (between 1 and 4), type '1' (it's the firt one). After that, it asks for the first and last cylinders of the new partition, type the default values it offers.

Type 'p' to see the partition table and its new partition at the bottom; it's /dev/sdb1, and is listed as having type'Linux'. We are going to change it to be of type w95 FAT32 (LBA); you can press 'l' (list) to see the partitions fdisk knows about -ours is identified with hexadecimal value c). Now, to change the partition type press 't', and when asked by the hexadecimal code to employ, type 'c'. Then type 'p': now the partition is of type FAT32 (LBA).

After all this, at the prompt type 'w' (write partition table to pen drive and exit the program).

Then just issue the command

sudo mkfs.vfat -F 32 /dev/sdb1

to make the file system in the first (and only) partition of the pen drive, /dev/sdb1. This is the comand I did wrongly show in my prev post, and you're right: it just "formats" a partition with the given file system type (FAT32 filesystem for a FAT32 partition). Me bummer! :-)

Now your pen drive should be mountable, visible by gparted, nautilus and any other program.

Hope this is of any help. If you have doubts or problems, just ask here.

Yeah, man. Great post, thanks for your time.
Now I just need to know what to write in the above prompt. Do I? Is that what I need considering fdisk doesn't work?

Thanks again,

Andre

---

### Post by edujose on 2009-05-05
Hi ophysis, hmm seems fdisk gets no clues from your pen drive. It's curious it just bails out with that error message and no further info.:confused:

Well, sfdisk looks pretty obscure, better don't use it.

I've googled a bit and found some blogs were people borked their USB pen drives (partition tables corrupted or lost, pen drive bricked) and they seemed to repair them using gparted.

You said in a former post that gparted can't even see your pen drive. Is this the case still? When I plug a USB pen and then start gparted (I'm now running off a Jaunty live CD) it just shows the hard disk (/dev/sda) and its partitions. But if I click the rightmost button, it lists both drives, and clicking the second (/dev/sdb, my USB pen drive) shows its partitions. Ok, ok, my USB drive is not corrupted, but read on.

So you could try booting from a jaunty live CD, plug your pen drive, start gparted, click its right button (the one showing your disk name and size) and try selecting the second drive (/dev/sdb, your USB drive). Then you can click the gray rectangle (your empty drive) to select it, and use Device | Create partition table from the menu to create a new partition table (an msdos one, that's fine). From that on all would be hopefully well and you could create a FAT 32 partition in the empty space. After all this, just click the Apply button to really apply all the operations to the drive.

(In a related note of hope, this morning one coworker told me her USB pen had gone corrupted after a blackout while using it in winXP. Now it showed no content. We tried gparted from a 9.04 Jaunty live CD, and there it was her pen drive, though empty (no partition table nor partitions in it). But at least we could see the drive from gparted, and could select Device | Create partition table (I'm translating, mine is in another language) to recreate it and then fill it with a partition.)

---

### Post by dcstar on 2009-05-05
SSD devices only have a finite quantity of writes, then they die.

---

### Post by ophysis on 2009-05-07
> **edujose said:**
> Hi ophysis, hmm seems fdisk gets no clues from your pen drive. It's curious it just bails out with that error message and no further info.:confused:

Well, sfdisk looks pretty obscure, better don't use it.

I've googled a bit and found some blogs were people borked their USB pen drives (partition tables corrupted or lost, pen drive bricked) and they seemed to repair them using gparted.

You said in a former post that gparted can't even see your pen drive. Is this the case still? When I plug a USB pen and then start gparted (I'm now running off a Jaunty live CD) it just shows the hard disk (/dev/sda) and its partitions. But if I click the rightmost button, it lists both drives, and clicking the second (/dev/sdb, my USB pen drive) shows its partitions. Ok, ok, my USB drive is not corrupted, but read on.

So you could try booting from a jaunty live CD, plug your pen drive, start gparted, click its right button (the one showing your disk name and size) and try selecting the second drive (/dev/sdb, your USB drive). Then you can click the gray rectangle (your empty drive) to select it, and use Device | Create partition table from the menu to create a new partition table (an msdos one, that's fine). From that on all would be hopefully well and you could create a FAT 32 partition in the empty space. After all this, just click the Apply button to really apply all the operations to the drive.

(In a related note of hope, this morning one coworker told me her USB pen had gone corrupted after a blackout while using it in winXP. Now it showed no content. We tried gparted from a 9.04 Jaunty live CD, and there it was her pen drive, though empty (no partition table nor partitions in it). But at least we could see the drive from gparted, and could select Device | Create partition table (I'm translating, mine is in another language) to recreate it and then fill it with a partition.)

GParted doesn't see it.

I'll try booting from live cd though. One never knows.

EDIT: Tried the live CD, same thing. No go.

Tks

---

### Post by ophysis on 2009-05-07
> **dcstar said:**
> SSD devices only have a finite quantity of writes, then they die.

Yes, I'm aware of that. Like I said before, it's a new pen drive. Not used often.
It doesn't seem to be dead. The light works, blinks, etc... Windows recognizes it when I plug it in. In Ubuntu it only shows in places>computer.
In windows, in disk management, is also shows, just says it has no partition table, or that it is unreadable, or so...

Any other ideas? Anyone?

Thanks

---

### Post by edujose on 2009-05-07
Ugh, tough drive to get alive!

Just some more possible steps to try.

One: Try rewriting the MBR (MAster Boot Record, record 0 or sector 0 of the USB drive) with a good one. For this, install package "mbr", connect the USB pen, be sure it's NOT mounted (if an icon representing it appears on the desktop, though unlikely, right-click and select "Unmount Volume"), open a terminal and run:

sudo install-mbr /dev/sdb

(after that, open gparted and see if the USB pen drive appears there. If so, create msdos partition table and FAT32 partition).

Two. Go to the web site of the pen drive manufacturer and search under Support or Downloads for some utility (surely windows-based) to reformat your pen drive. This would be the best route I believe. (What's your pen drive's manufacturer, out of curiosity?)

If none of these work, someone more knowledgeable can give you a solution.

Also, please report a bug about USB creator in Launchpad (the bug system of Ubuntu). Just go to Launchpad, make an account for you and file a bug where you tell the details (what you did, what happened to your drive, its brand/size, ubuntu version used, steps you have taken to recover it, whatever could be useful to solve the bug) and assign as affected package "usb-creator".

To see the current list of bugs for this package: [https://bugs.launchpad.net/ubuntu/+source/usb-creator]("https://bugs.launchpad.net/ubuntu/+source/usb-creator"). I think none of them is exactly like your problem, so you could file a new bug. And an interesting bug (or feature request) that seems related to your problem: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/273481]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/273481").

Anyway the non-geek, non-satisfactory solution could be saving for another pen drive. But who wants to do this? :-)

---

### Post by ophysis on 2009-05-08
> **edujose said:**
> Ugh, tough drive to get alive!

Just some more possible steps to try.

One: Try rewriting the MBR (MAster Boot Record, record 0 or sector 0 of the USB drive) with a good one. For this, install package "mbr", connect the USB pen, be sure it's NOT mounted (if an icon representing it appears on the desktop, though unlikely, right-click and select "Unmount Volume"), open a terminal and run:

sudo install-mbr /dev/sdb

(after that, open gparted and see if the USB pen drive appears there. If so, create msdos partition table and FAT32 partition).

Two. Go to the web site of the pen drive manufacturer and search under Support or Downloads for some utility (surely windows-based) to reformat your pen drive. This would be the best route I believe. (What's your pen drive's manufacturer, out of curiosity?)

If none of these work, someone more knowledgeable can give you a solution.

Also, please report a bug about USB creator in Launchpad (the bug system of Ubuntu). Just go to Launchpad, make an account for you and file a bug where you tell the details (what you did, what happened to your drive, its brand/size, ubuntu version used, steps you have taken to recover it, whatever could be useful to solve the bug) and assign as affected package "usb-creator".

To see the current list of bugs for this package: [https://bugs.launchpad.net/ubuntu/+source/usb-creator]("https://bugs.launchpad.net/ubuntu/+source/usb-creator"). I think none of them is exactly like your problem, so you could file a new bug. And an interesting bug (or feature request) that seems related to your problem: [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/273481]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/273481").

Anyway the non-geek, non-satisfactory solution could be saving for another pen drive. But who wants to do this? :-)

Ehehe,

Yeah man, it's a tough one...

I tried the mbr but all I get is this:

```
:~$ sudo install-mbr /dev/sdb
[sudo] password for dreani: 
install-mbr: Error reading /dev/sdb: Input/output error

```

The pen is from DANE-ELEC (never heard of it before) I think they call it a "Zlight", 8Gb.

I contacted their support, waiting for a reply...

Thanks once again, man.

Stay cool.

---

### Post by salvachn on 2009-05-14
I fried my pen drive a couple of years back (it was barely a month old) when I switched on my friend's PC with the drive inserted. Seems there was a voltage spurt and it baked the drive. It might be the case with you too.

---

### Post by ophysis on 2009-05-18
> **salvachn said:**
> I fried my pen drive a couple of years back (it was barely a month old) when I switched on my friend's PC with the drive inserted. Seems there was a voltage spurt and it baked the drive. It might be the case with you too.

Mmmm, don't know... If you read the thread, you'll agree that it's not likely...

Anyone has a genius pen drive reviving piece of wisdom about this? :)

---

### Post by ophysis on 2009-06-06
Still in need of assistance...

Anyone?

---

### Post by ophysis on 2009-06-12
Anyone, please.............

---

### Post by donpedroc21 on 2010-11-08
hey ophysis man, 

sorry bout ur usb.
 am gonna keep it simple explaining how to get it back, the same thing
applied to me aswell. then i went through ur forum, but dint find anthing useful, all the guys
where talking about using windowxp or vista, but i have ubuntu also.

i was trying to change my usb format to FAT32 in Gnome "partition" so it can work with my xbox 360, but i changed it and guess what after saving i went to unplug my usb and plug it in again, BANG[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG], it dint appear on my destop screen or anywhere on my computer, so i came online when i saw ur question, n go through, but nothing worked as i said before.

so i said to my self the same programm that corrupt my file will fix it again "Gnome"

"PROBLEM SOLVE"

I WENT BACK TO gnome partition AND PLUG IN MY USB AND SELECT MY USB ON THE TOP RIGHT OF THE SCREEN (GNOME PARTITION)
AND THEN I CLICK ON PARTITION, IT DINT SHOW ME WHAT IT DID BEFORE, INSTEAD IT SHOWED ME A DROP DOWN MENU, N I WENT FORMAT AND I SAW ALL THE FORMATS SO I CLICK ON FAT32 AND APPLY IT.

Now it works, hope the same works for u too man[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

