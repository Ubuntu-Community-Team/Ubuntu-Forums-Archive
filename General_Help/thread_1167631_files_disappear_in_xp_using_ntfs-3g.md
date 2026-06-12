---
title: "files disappear in xp using ntfs-3g"
date: 2009-05-23
forum: General Help
---

### Post by p-dh on 2009-05-23
I have a jaunty machine with the most recent upgrades. I use ntfs-3g to mount ntfs drives created by xp-sp3. 
1. In Ubunutu, I have no problems reading and writing files/directories created on an ntfs partition by xp. 
2. In Ubuntu, if I create files/directories on an ntfs partition, I have no problems reading and writing to those files/directories.
3. In XP, if I try to open files/directories created or edited on an ntfs partition by Ubuntu, they disappear in both XP and Ubuntu.

In attempting to fix this, I have:
1. Checked the version of ntfs-3g. It is the latest in the repositories (although not the latest by ntfs-3g.org).
2. Created a Polish locale with dpkg and changed the locale setting in fstab.
3. I have changed the fstab settings to allow user to mount ntfs drives.

Can anyone point me in the right direction to get this fixed? I have noticed this to be an issue with my USB drive (files show up in Ubuntu, not xp), but did not see it as serious until I lost a day's work by trying to edit some docs created under Ubuntu while running xp.

TIA.

Paul

---

### Post by dhinchak on 2009-11-12
same problem here...

i was using ubuntu 9.04 and everything was just fine. until one day, i installed ubuntu 9.10.....

i created some new text files, folders, some documents and dwonloaded a movie over the internet on a ntfs partition (i share this partition with my windows dual boot). after restart, i booted into windows and just didnt find any of the files! then i again restarted and booted into linux and files werent there either. i tried repairing the mft, but no help.

they were some really imp documents. so if somebody could help me recover them, or atleast give a suggestion on how to avoid such issues, it would be greatly appreciated.

---

### Post by registering on 2009-11-12
That's very scary and a show stopper! I hope someone has some suggestions. I was about to play with 9.1 but use a similar setup, so I'll hold-off until this is fixed.

---

### Post by John Bean on 2009-11-12
Did you dismount the ntfs volume cleanly? The reason I ask is that I have found by bitter past experience that sometimes there is unwritten data not flushed to my external USB drive after closing down (or rebooting) without explicitly unmounting the disk first. Trial and error led me to believe that on booting XP it then silently "cleans up" the disk and can, depending on the corruption, lose whole folders which are gone forever even after rebooting Ubuntu. If on the other hand I reboot Ubuntu without having used XP it doesn't seem to notice the data damage and everything appears to be ok - but isn't really.

But on the whole I'm very comfortable with ntfs-3g and have had no recent problems of this sort, perhaps because I've developed a habit of always dismounting ntfs volumes before shutting down... just to be on the safe side.

Incidentally ntfs-3g deliberately flags the disk as "dirty" if it has written to it, which is what triggers XP's check in the first place.

---

### Post by nuke01 on 2009-11-13
i have the same problem. this seems to be a major bug. 

everything I did, was trying to save a document from the web in my work folder (<- all important documents in there :( ). the save dialog wasn't reacting quite a while, as I tried to access this folder/harddisc. so I opend it in nautilus but everything seemed fine. than suddenly the save to disc dialog worked, but as I opened the "work" folder, some subfolder were missing. the same in nautilus. i restarted (so I assumed it unmounted how it should do it) and started again in windows. ever since I'm running an recovery programm. this is not good.

joe out
ps.: append the mandatory: "sry, for my bad english, not first language"

---

### Post by nuke01 on 2009-11-15
ok, no recovery, even with stellar phoenix.

can somebody help?

i think this is a major bug of 9.10 and I'm really angry.

---

### Post by reddevilcanada on 2009-11-15
I am having the same problem on 9.10 with external usb drives and Windows 7 partition on the same drive, it looks like everything is there you can even read the file, reboot and everything is gone! Went into Win7 and some of the files were there some were not, mostly not...

---

### Post by gamerz300 on 2009-11-23
i had this problem as well but i have some great news...
i have a 1TB lucky i made a few partitions and the problem partition is a 50GB

so far i removed all visible files off the 50GB putting them some where else and doing both Full and Empty Tests...

Go to [http://en.kioskea.net/faq/sujet-729-recovering-lost-files](http://en.kioskea.net/faq/sujet-729-recovering-lost-files) look for Photorec&Testdisk (gave the link due to other programs which may work better) or go to their actual site which has the latest version (im not using, im using the one in the link above) [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Extract the zip file somewhere ***You should put it in a place which has a lot of free space as its default dir to transfer files is in its own folder***

so far what i have seen both Free and Whole scans seem to be getting the files, i think its because their both physically showing on the total disk usage and not showing up in the directory. However it seems (using the version in the first link) you will get a bunch of text files however so far its doing a great job finding the files needed.


Here is the painful part tho... it will name the files F####### but will keep their extensions :)

which one is faster tho? umm does it really matter? but with no visible files on the partition the full one is moving slightly faster and with out the 80000 text files extra :shock:

It works under anything Dos really or up to Vista... im guessing the next release will have 7 but works in Ubuntu as well ;)

---

### Post by Brilnius on 2010-01-03
Has anyone updated information about this problem?

I lost huge quantity of files two days ago and I would like not to have the same problem again.
On my previous PC, everything was ok with a "shared" partition using FAT32.

My details:
- Ubuntu 9.10 (fresh install + updates) and Windows 7
- Logical NTFS partition (dev/sda8)
- /etc/fstab entry:
  UUID=4034F82434F81E9A /media/data ntfs defaults,nls=utf8,umask=007,gid=46 0 0
- Maybe noteworthy: I often use "suspend to disk"

---

### Post by bbdimitriu on 2010-04-19
Any news about this?

The problem happens to me as well when I write files from Ubuntu 9.10 (with the latest updates). Last time I moved a film (~700Mb) from my ext4 to the NTFS partition (not the one which has got the Windows 7 installation on), restarted, booted into Windows 7 -> file was not where I copied it. I went back into Ubuntu and I COULD see the file on the NTFS partition where I moved it and I managed to copy it back entirely on the ext4 partition (I guess I was lucky compared with others).

A few months back when I installed 9.10 and I configured NTFS access the first time, something even more weird happened: the access from Linux was fine, but when I booted back into Windows 7 I could see all the root directories as duplicate (e.g. 2x Program Files, 2x Windows etc.). Windows 7 didn't seem to be bothered, but I was, so I ran the disk check application and this issue was sorted.

Has anybody got any insight into this problem? Unfortunately I don't have access to my computer right now, but I'm quite certain that the partition is mounted in /etc/fstab like Brilnius has it:

> 
UUID=AA34F82434F81E34 /media/data ntfs defaults,nls=utf8,umask=007,gid=46 0 0


Maybe UTF-8 has something to do with it?

---

### Post by Larkster on 2010-05-02
This is by no means a solution, but hopefully my observation will help put someone on the right track:

I too am experiencing this issue.  I copied some files from 10.04 Lucid 64bit to my mounted Windows 7 partition and when I rebooted into Windows, the files were missing.  However, sometimes such a file transfer is persistent and works as expected.  Here seems to be the difference: the broken behavior occurs when Windows is in a hibernating state.  If Windows is fully shutdown and Ubuntu is booted into, files transferred will work properly.

It would be nice if this issue is resolved as I frequently want to switch OS's without having to close everything up, thus making hibernation a necessity.

---

### Post by theblackkat on 2010-07-08
> I too am experiencing this issue. I copied some files from 10.04 Lucid 64bit to my mounted Windows 7 partition and when I rebooted into Windows, the files were missing. However, sometimes such a file transfer is persistent and works as expected. Here seems to be the difference: the broken behavior occurs when Windows is in a hibernating state. If Windows is fully shutdown and Ubuntu is booted into, files transferred will work properly.

It would be nice if this issue is resolved as I frequently want to switch OS's without having to close everything up, thus making hibernation a necessity.

**_EXACTLY_** my problem too... Don't want to give up hibernation, but it seems to be the only way for now :(

---

### Post by John Bean on 2010-07-09
Hibernation is a different matter. If you modify the disk of a hibernated Windows system it *will* cause data corruption when the system is brought out of hibernation.

It's nothing to do with the system that writes the data, it's down to the restored Windows system having disk cache data inconsistent with disk content, similar (but not the same as) the effect of losing power during a disk write.

Modifying the system disk of a hibernated system is a big no-no; it would probably be better if ntfs-3g forced such disks to mount read-only.

---

### Post by JedMeister on 2010-07-17
Sounds like the underlaying issue is Windows not cleanly unmounting HDDs. Obviously in a Windows system, when hibernated, the HDD is still mounted, but in a frozen state. I guess thats why you don't get the option to boot into another Win OS on (Win only) dual boot systems if one of the OSs is in hibernation.

In my experience, other times when this problem can occur is if portable drives are not unmounted properly. It rarely seems to be a problem with flash based USB storage (although that's possibly because they're usually FAT). HDDs on the other hand seem to often get corrupted if removed without "safely" removing from Windows.

You may not ever notice a major problem if you use Windows only but within Ubuntu it seems to somehow hide the files that that are corrupted (even if the corruption is relatively minor). Once Ubuntu hides these files they are also hidden in Windows (Ubuntu possibly deletes their entries in the HDD index/TOC or whatever it is).

I recently 'lost' 100GB of files off a portable NTFS HDD. After doing a full chkdsk (under Windows) they all reappeared with the chkdsk fragments totaling only a couple of bytes!

So the lesson here is: Don't touch a NTFS filesystem with Ubuntu (or probably any Linux distro) which hasn't been cleanly unmounted when last used in Windows.

Out of interest I found under Xandros (on my old 701 EeePC) that it checks for possible corruption on NTFS volumes prior to mounting. If there is any inconsistency it refuses to mount it. In this scenario the solution often simply lays in mounting the HDD in Windows and "safely" removing it again. I guess Xandros' implementation of ntfs-3g does something along the lines of John Bean's suggestion (except doesn't mount at all instead of mounting read only).

---

### Post by xfctr on 2011-04-20
I'm still getting the same problem on Maverick - creating new files in an NTFS partition under Ubuntu, later booting to Windows 7, and - boom - they are gone, nowhere to be found neither by Windows, nor by Ubuntu. I can sometimes initially see the top created folder in Windows, and when I try to open it - an error and everything's gone. 

Today I spent a couple of hours downloading covers for my music collection under Ubuntu - all newly downloaded covers are now gone. Also all the music under a folder named with a Cyrillic name.

In the past I have seen problems, where Windows would complain about the names of files, downloaded from torrents under Ubuntu (with Transmission). 

I feel ntfs-3g is somehow abusing the NTFS naming rules, but that may be a wrong clue - all the downloaded covers were named with the ordinary "cover.jpg". 

I'm now concerned about my work setup, where my data is written by Linux on a NTFS partition - if I ever install and boot to Windows there, will all the data disappear! Means I should backup and format the partition to some other filesystem instead.

Is there a bug-report anywhere about this? Sounds to me like a massively major issue.

---

### Post by xfctr on 2011-04-20
Aaah, my bad. I just recalled that I had hibernated Windows instead of shutting it down and I now read that it is, well, a NO-NO. So, remember to always shut Windows fully down before booting to Ubuntu if they are sharing the same NTFS drive. 

On the other hand, Ubuntu should in this case NOT allow me to mount the drive for writing.

---

