---
title: "The Saga continues..."
date: 2006-10-02
forum: Desktop Environments
---

### Post by morequarky on 2006-10-02
The Saga continues...

stage one:  wife gets viruses on laptop
stage two:  said laptop gets formated.
stage three: wife adds XP Home to XP64 install while formating two linux partitions, and the master boot record.
stage four: husband, me, reinstalls the correct "grub"
stage five: linux kernel boots fails to find filesystem.
stage six: reinstall in order.
stage seven: Dapper Live CD doesn't see any partitions on my harddrive.  Which might explain why the linux kernel can't load the file system when it can't find a single partition on the drive.

(note: drive contains XP64bit and various linux partitions including swap from the "destroyed install")

Where do I repair the "table of contents for a drive"?

thanks

---

### Post by morequarky on 2006-10-02
This is a serious bug.  A patch of XP or Vista could wipe the partition table or some such thing after install and dual boot is impossible as of now because gparted can't see a single partition.  How do you dual boot under those kinds of conditions??? YOu can't, period.  Kiss dual booting goodbye.

This problem needs fixing and fixed in a way Windows and Vista can't exploit it.

Serious bug!!

---

### Post by cptnapalm on 2006-10-02
Warning: I have no idea what I am talking about.

If is a Windows thing, then there isn't much anyone can do about it.  If Windows can write to the partition table, then only MS can do anything about it; I seriously doubt they would do anything about it.

Something to give a shot: boot with the Live CD and run cfdisk on your hard drive (/dev/hda probably, /dev/sda possibly).

---

### Post by morequarky on 2006-10-02
Thanks for the attempt.

running "cfdisk" from the command line with a LIVECD of dapper gives me a "fatal error, press any key to exit"

Reading some of the cfdisk man file didn't help me.  eg. cfdisk -z returned the same error.

Could I have installed grup incorrectly and messed with the partition table that way?

Thanks

---

### Post by morequarky on 2006-10-02
Going to "system - admin - disk" gives me a listing of the partitions and allows me to access them.

Why can the live CD access various partitions, while "gparted" and the "installer" claims there isn't a thing on the drive?

Strange

---

### Post by morequarky on 2006-10-02
I am going to try to use the alternate CD and see what happends.

---

### Post by crazymonkey on 2006-10-03
I had a similar problem when i switched from XP to Ubuntu, I had Norton GoBack installed and i had lots of trouble to get it deleted (it installs in the MBR)

I used this thread [http://www.ubuntuforums.org/showthread.php?t=236614]("http://www.ubuntuforums.org/showthread.php?t=236614")
in which i found a command to completly clear the MBR. Run the following from the livecd :```
sudo dd if=/dev/zero count=1 bs=512 of=/dev/hda
```
Change /dev/hda if you need to.

[COLOR="Red"]This will TOTALY DELETE any reference to your existing partitions[/COLOR]

> stage seven: Dapper Live CD doesn't see any partitions on my harddrive. Which might explain why the linux kernel can't load the file system when it can't find a single partition on the drive.

The fact that you have no partition on the disk before installing should'nt be a problem, gparted should propose you to create a new partition table.

If the command i gave you above doesnt do the trick i would try to go on your disk manufacturer site and try to find a bootdisk which include tools to change all the harddrive to its original state by writing all 0 on it. (You can get the one from Western Digital [here]("http://support.wdc.com/download/index.asp?cxml=n&pid=17&swid=36"))

I hope this helps!

EDIT: Once you get everything back to normal try installing in the following order : XPhome, XP64 (and any other Windows version) and after install Ubuntu. The reason for this is that Ubuntu detect other OS installation and integrate them to GRUB while Windows thinks its alone on the system and will completly rewrite the MBR without detecting linux OS.

---

### Post by morequarky on 2006-10-03
Are you telling me to reinstall XP?

So may situation has gone from reinstalling Ubuntu keeping my /home to reinstalling windows as well do to what?  I would like to know exactly what happened to my machine that requires this?  That ticks me off.

I can boot the machine into XP Home or XP64.  I can boot the linux kernel even, but the kernel dies do to filesystem unlocated.  So I have to reinstall XP too?  Grub is on the MBR now.  Grub works fine.  Ubuntu is skrewd here.  How can my ubuntu be so messed up that I have to reinstall XP!!!!!

---

### Post by crazymonkey on 2006-10-03
Sorry then, i misunderstood the situation...

---

### Post by doobit on 2006-10-03
> **morequarky said:**
> Thanks for the attempt.

running "cfdisk" from the command line with a LIVECD of dapper gives me a "fatal error, press any key to exit"

Reading some of the cfdisk man file didn't help me.  eg. cfdisk -z returned the same error.

Could I have installed grup incorrectly and messed with the partition table that way?

Thanks

Either you are not booting from the live CD and you need to change the boot order settings in your BIOS, or your install CD was a bad download that didn't meet the checksum, or you have a faulty CDROM drive. cfdisk is a very small command line program that runs in bash from the terminal. If you are booting the live CD and able to get to the Ubuntu desktop, then cfdisk will run without any error. it doesn't require a lot of resources. The error you have stated suggests that the CD is not booting completely, so you have got something going wrong before you even get to Ubuntu. The fact that you can't get Gparted to work tells me the same thing. Your hardware is not configured properly in the BIOS, or the CDROM drive is going bad, or you are having trouble burning the CDs from the isos you are downloading.

---

### Post by morequarky on 2006-10-03
"If you are booting the live CD and able to get to the Ubuntu desktop, then cfdisk will run without any error."

WRONG.  I am booting to the LIVECD ubuntu desktop and cfdisk DOES throw this error.  The checksum on the LIVECD is 'OK'.  Selecting "check CD for errors" returns NO ERRORS.  I tried to install from a fresh "alternate" CD and the partitioning failed, by telling me my only options were RAID or formatting the whole drive. (I ran md5sum on the download before burning the CD ). It refused to give me a partition list.

Trying a "rescue" on the alternate CD gave me a partition list and I correctly selected my kernel partition '/' and it gave me a prompt.  I don't know what to do at the prompt.  I need to reinstall, but every partitioner included with dapper install methods fail to find any partitions on the drive.

The liveCD is booting correctly, period.  No matter how many or which type of dapper I use.  My computer boots XP or XP64 fine and there isn't a thing wrong with my bios from that perspective.

"System - admin - disk" can see my partitions with no problem and allows me to access the partitions....attempting to rescue my install finds my partitions as well....THEREFORE I believe in my case the code for dapper- installer partitioners is faulty and this is a BUG involving multiple windows kernels perhaps, but I doubt that because GRUB is working flawlessly.(xp Home & xp64)

(Maybe my computer is hacked in such a way that only dapper partitioners fail.)

Is it possible for me to use some backup method and the "dd" command and burn my whole drive and send it to those who care to allow them to see that I am not out of my mind.

You try it.  Install xp64...install ubuntu64...install xp Home inside xp64's partition...then reinstall GRUB.  See what happens.  See if you can reinstall ubuntu.  I bet you'll end up with a similar problem as me.
(note: ubuntu is spread out across many partitions)

later

---

### Post by podunk on 2006-10-03
If you go to disk administration in XP - does it see your Linux partions? If so - try deleting the Linux partions from there and see what happens.

If you're trying to save your Linux install I ain't got a clue.

---

### Post by morequarky on 2006-10-03
podunk...good idea...I am not at home now, but when I go home I'll try that. Do you know where they menu for that is?

Thanks

---

### Post by podunk on 2006-10-03
Start
Control Panel
Administration
Disk storage ? maybe?

I know it's somewhere in Administration section of the control panel &#8211; I can't open the XP machine, it's backing up.

It's got a very nice graphical output of all your partitions. Linux partitions are &#8220;Unknown type&#8221;

Right click and you can chose to delete them.

If you only have one hard drive &#8211; would suggest you do several defrags before reinstalling Ubuntu

---

### Post by morequarky on 2006-10-04
Found it.

Deleted all but /home.

Took out the liveCD and rebooted.

GRUB error 17.  Nothing.  Can't boot windows now.

Going to try the alternative CD and reinstall GRUB.

---

### Post by morequarky on 2006-10-04
This is absolutely the craziest thing.

I now have to totally reinstall two versions of windows AND ubuntu.

I have no idea how my wife, installing XP Home blowing up the MBR, has caused a total reinstall of the whole machine, LOSING EVERYTHING, including unreplaceable baby pictures, that aren't backed up anywhere.

Thanks for all the attempts.

later.

---

### Post by podunk on 2006-10-04
I hate to read stuff like this. :-( I feel for you. 

It's unfortunate and has always irked me that MS doesn't offer a good back up built it. The program that comes with 98 is sort of a joke, and can't be read by the XP Pro backup (this is “planed behavior” according MS Knowledge base) , and of course there is no back up at all in XP home.

Do you have another computer? If you do and you have anything at all like a partition left you might be able to take the hard drive and slave it into another Windows computer to get your pictures and stuff back.

There is a website 
grc.com

and they offer a disk utility called spin right (I think that's the name – it's been years) that does an amazingly good job of recovering data from a hard disk. It was sort of pricey if I recall.

Once you get windows reinstalled, a good inexpensive back up program called Renaissance is out there, you can create a view and burn that to a DVD, then it updates files that change on the fly, it's very fast. Only drawback is this takes up quite a bit of space.

If can get your data back suggest storing it in a native Linux partition, Ubuntu backups are amazingly easy and fast!

---

### Post by morequarky on 2006-10-04
I am going to install all the windows junk on FAT32, no NTFS hassles and it isn't like XP needs to be installed very "special" to just surf, so forget NTFS.

I think I'll buy another small junk harddrive, aka 10-20gig small cheap to backup everything on...err...windows.  Ubuntu is stable, hardly need to back it up. I am the only virus Ubuntu has to deal with on my computer.

I want to use Ubuntu to backup the windows(FAT32) to the extra harddrive, but I haven't found the easiest way to do that. "podunk": how do you backup your drive so easily?

Later.

---

### Post by podunk on 2006-10-05
This backed up my Ubuntu perfectly:
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /
```

I unplugged from the network before running (wasn't sure if it would mix my samba shares in from the Kubuntu computer) and edited fstab so my windows drives weren't mounted, then rebooted, then ran.

The first time I did it I had a minus instead of an equal in one of the exclude= ;s and it backed up the tarball while backing up to the tarball. :-) It aborted when it ran out of hard drive space.

The second time I did it I spent a few deleting all the directories I had laying around from compiling stuff. Also i deleted the directories created by Simple backup.

I don't know what would happen if I tried backing up Windows with that. I doubt I'll try, I have a valid and proven back up of Windows, no need to waste a lot of time on an obsolete OS.

It was by far the simplest and fastest back up I ever ran. I did a restore with it and that was perfect also. Archive Manager read it fine also (took a while to load) so I assume you can restore individual files.

---

### Post by anaconda on 2006-10-05
> LOSING EVERYTHING, including unreplaceable baby pictures, that aren't backed up anywhere.

This seems to be your biggest problem. (I don't think reistallation is that big a problem, but valuable data loss is sad..)

Here is a link to some (free)tools for lost partition recovery.
[http://www.s2services.com/partitionmgrsfreeware.htm](http://www.s2services.com/partitionmgrsfreeware.htm)
I used one of those succesfully to get a lost partition back, and while windows wasn't bootable anymore I was able to rescue all valuable data after restoring the partition..

And I think cfdisk is used like: sudo cfdisk /dev/hda
I have noticed that sfdisk works better with corrupted partition table.. atleast it can show the contents of partition table even if it is full of BS.. And is able to edit those.. (while cfdisk wasn't able to do anything..)dont know if sfdisk is included in dapper..

Oh! did you already install something on top of your valuable "lost" data.. then it would truly be lost. As long as you dont overwrite your data it is still on your hd, and there are programs, that can "sniff" and rescue files from hd-surface. It is a WERY SLOW process.. but atleast you would get your pictures back..

---

### Post by morequarky on 2006-10-07
Thanks for the link and info on cfdisk.

the backup information sounds great too.  thanks bunches.

---

