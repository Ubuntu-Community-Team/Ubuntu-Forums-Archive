---
title: "Installation problem!!!!!"
date: 2006-03-30
forum: Desktop Environments
---

### Post by dragan1 on 2006-03-30
I used to have two partitions on my PC

C: with Win98 installed
D: With WinXP

I had to have both of these for educational purposes.
When booting, I would be promped to choos between the two OS-s after the POST had been done.

When I heard about Ubuntu, I ordered it and after testing, decided to install it.
My idea was to install it over Win98, and keep WinXP, which I had alot of different applications installed on.

During the installation process, I followed all instructions closely and kept the process as automatic as it could be in order not to make a bad sten as an unexperiened user.
the installation went fine and no problems were reported.
Now Ubuntu works fine, but i do not have access to WinXP.
In the Ubuntu's Disks Manager Partition List, it says that I have three partitions.
Partition 1, with Ext3 file system, Access path-"/" and Status Accessible.
Swap partition.
Partition 5, with "WindowsNTFS", Access Path-"none", Status "inaccessible".

so i would appeciate if somebody could help me to solve this problem without having to format WinXP partition and lose all data.

Thanks in advance
New Guy in Ubuntu

---

### Post by Sef on 2006-03-30
> Partition 1, with Ext3 file system, Access path-"/" and Status Accessible.
Swap partition.
Partition 5, with "WindowsNTFS", Access Path-"none", Status "inaccessible".

I see a problem.  Windows needs to be on the first partition when you have a dual boot.  

To get windows up, I would try a windows boot floppy and see if you could boot it up.  If you are able to, then I would [B]back up[B] your data, and reinstall Ubuntu.

However, I am not sure how to move your Windows partition to partition 1 without reinstalling Windows.

---

### Post by achim_59 on 2006-03-30
[QUOTE=Sef]I see a problem.  Windows needs to be on the first partition when you have a dual boot.  

To get windows up, I would try a windows boot floppy and see if you could boot it up.  If you are able to, then I would [B]back up[B] your data, and reinstall Ubuntu.

However, I am not sure how to move your Windows partition to partition 1 without reinstalling Windows.[/QUOTE]

In fact the problem is more complex, though what you say is true for Win98. It's just that there is more to it than having WinXP on the first partition. Starting with Win2000 multi boot setups got a bit trickier. I've done a number of them and here's what I had to do to get Win2000 working with Fedora Core (Linux), the same should work for XP:
1. Windoze has to be installed and working.
2. Defrag so that all the Win files are at the start of the drive.
3. When partitioning, set aside a 50MB /boot partition for Linux (this may in fact be the first on the drive if you wish - I'll get back to that).
4. Set aside an OS-Share partition that both systems can use (This should be fat32 not ntfs, since ntfs support under Linux is dodgy at best).
5. Set up the Linux & Linux Swap partitions.
Note: all the above steps can be done when installing Win2000/XP if you're starting from scratch (just setting up a partition doesn't involve formatting it).
6. After Windoze is installed and running, you can install the Linux system. 
7. The /boot partition (which should be formatted to ext2 or ext3) is where linux.bin will be installed. I don't use lilo so I cannot comment, but for grub it may be necessary to edit grub.conf to install the windows entry, which should look like:
```

title WinXP
<tab>rootnoverify (hd0,0)
<tab>chainloader +1
```
In the above <tab> stands for the tab character (which I believe is required). Also the 2nd zero in (hd0,0) assumes that WinXP is the first partition. If it's the second this should read (hd0,1) and so on.
8. Now you'll need a command line. To achieve this you might just have to reboot, since Ubuntu installation doesn't give you that option as far as I know. This would mean finishing the Linux installation very carefully... don't overwrite any boot sectors!
9. Now reboot with the live CD, which I surmise you have, and call up a terminal. You can probably also use the install disk in rescue mode.
10. Mount the fat32 partition (osshare or whatever you called it) if it isn't already mounted. You may need to create a mount point in /etc/fstab (you'll need to use sudo).
```
sudo gedit /etc/fstab
password:<enter your password>
```
The entry should look like:
```
/dev/hda5      /osshare     vfat  defaults  0  0
```
This assumes that the device name for your fat32 partition is hda5 (yours could be different). To find out which one it is (if you didn't take note whilst partitioning), you might try ```
df -t vfat
```
You'll have to reboot if this step was necessary... Sorry:( 
11. Now you need to copy the data from the /boot sector to /osshare
```
mount /osshare  <...if it's not already there...>
dd if= /dev/hda2 of=/osshare/linux.bin bs=512 count=1
```
This assumes your /boot is /dev/hda2
12. Now be extra careful... Reboot... Windoze should fire up by default and you should log in as an administrator.
13. In Explorer go to Tools>Folder Options>View and set the system to show hidden system files (that means deselecting the checkbox "Hide protected operating system files") and selecting the option to display all files (a radio button). Sorry, I've got a German version so I don't know for certain what it says in English.
14. Copy the linux.bin file from the osshare drive [probably D:\ ] to C:\
15. Change the attributes of the file C:\boot.ini so that it can be editted.
16. Add the following line to the end of the file:
```
c:\linux.bin = "Linux"
```
17. Reset the file settings so that you don't damage them accidently.

After this you should first get the windows boot manager and afterwards get grub.
The order of the drives/partitions isn't all that important but do try to keep your /boot partition before cylinder 1024 (unless your BIOS supports boot sectors after that position (more modern machines should... I just can't remember the technical term for it).

This whole mess occurs because WIn2000/XP require the windows boot-loader, and this must be present where the windoze install puts it. Doing the old trick of Making sure that Windoze is the First partition on the system and overwriting the MBR with lilo or grub just won't work. I tried that once and then found out the bad news through google! I had to reinstall Windoze. Thankfully I had backups, so it wasn't too painful. I'm not at all certain what our friend dragan1 is going to do.

I am not a linux guru (more of a geek-wannabe) and I cannot claim that the notes above are exhaustive or 100% error free. I wrote down what I did and that's pretty much what you see there. Maybe a real guru can provide a solution to the problem of the winXP installation (maybe some trick similar to using an install disk in rescue mode ... at least to get some backups).

Good luck to anybody who tries this... it's a real pain.

If anybody finds a mistake... please do correct it... then I can update my notes.

Achim

---

### Post by munga_bill on 2006-03-30
> In the Ubuntu's Disks Manager Partition List, it says that I have three partitions.
 Partition 1, with Ext3 file system, Access path-"/" and Status Accessible.
 Swap partition.
 Partition 5, with "WindowsNTFS", Access Path-"none", Status "inaccessible".
Well I'm not perfectly clear here about which partition number goes with which partition, Ubuntu is partition 1 by the looks (hd0,0) in Grub's numbering, Windows XP is partition 5 you say? That doesn't sound right, that would mean it's on a 'logical' partition, which would be more typical for a swap area.

Presuming you made a mistake and swap is partition 5, that would mean WIndows XP would be partiton 2, (hd0,1) I'm guessing, in grub's numbering. 
It's quite likely I'm wrong, so just substitute whatever numbers are in fact correct here, or try  the following several times with different numbers.

Now here's what you can try before you start going to too much work, just try booting with GRUB from the command line, (type 'c' at the GRUB menu to get to the command line) and try out these commands:
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
It could be that Grub is a little confused about your partition numbers too, and you might be able to find which partition numbers will work and when you get it to boot, write down the correct commands and then edit your /boot/grub/menu.lst with the corrections.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Another idea would be to try a boot manager like GAG, which you can download for free off the internet and install on a CD, floppy disk or your MBR (hard disk).
GAG is also found on 'System Rescue CD', if you have one of those handy. There is no logical reason why GAG would work when GRUB fails but it would be worth a try anyway first before you go to too much other trouble. 
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
I hope I'm being helpful, regards, munga_bill

---

