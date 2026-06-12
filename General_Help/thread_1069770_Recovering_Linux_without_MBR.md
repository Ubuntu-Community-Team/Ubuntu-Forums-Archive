---
title: "Recovering Linux without MBR"
date: 2009-02-14
forum: General Help
---

### Post by 1ronlung on 2009-02-14
Hi guys..

I've got myself in a right old mess ....

I had kbuntu installed on a USB drive.  Had MBR set on it so that if I quick-booted via BIOS to that drive, grub was automatically loaded and I had an easy boot.  If I didn't boot to USB drive, windows booted as usual.

Now, after much fecking about with Super Grub Disk and using windows to fixboot and fixmdr (a little knowledge is a bad thing!)I'm in a state of turmoil..

Windows won't recognise the drive at all ... When I view it in SGD, the drive is shown with a size of 0K and no partitions. (There should be 2 partitions.. NTFS and EXT2).

I'm currently using Ontrack recover in windows to get back  everything on my NTFS partition (all my mp3s.. phew ... ).  I can see from ontrack the Linux partition along with the starting and ending cylinders, but *no* cluster size - Ontrack doesn't support EXT2.

I'm a newbie to Linux and have spent a great amount of time over the past few months customising and adding to my kubuntu install.. I can't face going through that again !

Is anybody aware of a windows (or Linux, if it contains O/S) application that will allow me to restore my EXT2 partition ?

Much Thanks in advance!

---

### Post by caljohnsmith on 2009-02-14
Probably one of the best programs for recovering linux partitions is "testdisk". To use it, how about booting your Live CD (the Ubuntu install CD), 
download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct drive and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing. And lastly, please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by 1ronlung on 2009-02-14
Wow.  I know you guys are helpful, but you're super good :)

Am just on my way to a wake, but should have those results tomorrow evening.

ironlung

---

### Post by 1ronlung on 2009-02-15
Holy crap Batman.. That software is like .. super good :)
Did the brief analyse and everything showed was as it should be, so I went ahead and wrote the changes.

Restored my NTFS, Linux.. everything ..

Had to use super grub disk (which got me in this problem!) to get Kubuntu automatically booting from USB again.

A big thing for me ... I have a dell laptop.  I used to be able to re-install windows to factory setting by doing a CNTL-F11 (I have no win CD)
Since installing Kubuntu this no longer works.

For the first time I've seen this hidden partition and restored it.  About to give it a go now.  I've decided to take the plunge and have Linux as a permenant fixture on my laptop...

Final question.. Good program for backing up MBR (and grub, hopefully) to USB ?  Don't wanna have to go through this again ;)

Thanks,
ironlung

---

### Post by adult swim on 2009-02-15
you can usually reinstall grub with an ubuntu live cd.  all you have to do is boot the live cd, go to a terminal and enter in ```
sudo grub

root (hdX,Y)

setup (hdX)

quit
``` and reboot

X here represents the hard drive number, counting from zero.  say you had one internal hard drive and your usb drive attached.  your internal drive would be seen as 0 and your external drive as 1.  
Y represents the partition that /boot folder is in.  if it was on the first partition it would be 0

to sumarize, if you only have one internal drive and ubuntu is installed on the first partition of your usb drive you would run
```
sudo grub

root (hd1,0)

setup (hd1)

quit
``` and when you rebooted grub would be back in order.

---

### Post by caljohnsmith on 2009-02-15
> **1ronlung said:**
> 
Final question.. Good program for backing up MBR (and grub, hopefully) to USB ?  Don't wanna have to go through this again ;)

Thanks,
ironlung
I'm really glad to hear that you recovered your partitions. About backing up your MBR, I actually would not recommend it since I don't think it is necessary; if you back up the MBR somewhere, you would have to use something like the Live CD to copy it back into place, and as long as you are going to use the Live CD, I think it is better to just reinstall Grub like Adult Swim showed how to do. But, what I would recommend is backing up your partition table (which is maybe also what you meant), so then it is easy to restore your partitions if they somehow accidentally get deleted or something like what happened in your case. You can back up your partition table by doing:
```
sudo sfdisk -d /dev/[COLOR="Blue"]sdX[/COLOR] > partition_table.txt
```
Where sdX is the drive in question, and then at any time if you need to restore that partition table, all you need to do is:
```
sudo sfdisk -f --no-reread /dev/[COLOR="Blue"]sdX[/COLOR] < partition_table.txt
```
One small caveat though, there are at least two different standards for how to create extended partitions, and sfdisk uses the more restrictive standard; therefore, if your logical partitions are not in disk order (the physical order they are on the drive), you might have problems using sfdisk to restore your partition table. In that case you can use "fdisk" to restore your partition table, but it's just not as easy as the above sfdisk method. Anyway, hope that helps; cheers and glad you successfully recovered your partitions. :)

---

