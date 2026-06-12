---
title: "Discussion - https://help.ubuntu.com/community/MigrateWubi"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Support threads should be posted in normal forums.

Thank you.

---

### Post by bcbc on 2012-10-06
I've updated the wiki for release 2.3 of the script.

There are no specific changes required to support Ubuntu 12.10, but there  are a couple of bug fixes:
1. Fix problem for grub-legacy users (original install was on Ubuntu 9.04 or earlier).
2. Fix issue for French language users when parsing fdisk output.

I've also added signed checksums of the scripts so that users can verify them before using.

---

### Post by supermango on 2012-11-30
Once you restart after migration completes, how do you verify that you are now booted into the correct partition and not the wubi?

---

### Post by bcbc on 2012-11-30
> **supermango said:**
> Once you restart after migration completes, how do you verify that you are now booted into the correct partition and not the wubi?

I posted a response on the other thread you posted on. I'll add some notes to the wiki as well so it's clear for others. Thanks

---

### Post by supermango on 2012-11-30
> **bcbc said:**
> I posted a response on the other thread you posted on. I'll add some notes to the wiki as well so it's clear for others. Thanks

Thank you.

---

### Post by krishna.988 on 2013-03-07
What are the prequisites to do such a migration? Do I need to create partition and format according to Linux file system?

---

### Post by bcbc on 2013-03-07
> **krishna.988 said:**
> What are the prequisites to do such a migration? Do I need to create partition and format according to Linux file system?

The first paragraph from the guide:
> [COLOR=#333333][FONT=Ubuntu]This document describes how to migrate a Wubi install to partition. The partition(s) must be created already. [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]The examples shown below assume the target partition is /dev/sda5 and the swap partition (if required) is /dev/sda6.[/FONT][/COLOR]

They must already be type '83 - Linux' and '82 - Swap'. Creating an ext2/3/4 partition and a swap partition using e.g. GParted will give you that. While it's possible to format an NTFS partition (type 7) as ext4, the script will reject it. For safety reasons, the partitions have to be correctly created and empty.

It might be good to have more detail in the guide (but I'm trying to keep it simple.)

---

### Post by BlueTiger33 on 2013-05-13
[I][COLOR=#008080][B]G'day everyone! :) 
First off, thanks for this product and I really appreciate it. I'm hooked on Ubuntu w/ Wubi. :D

((I used Wubi for about a week as a web browser/email client [/B][/COLOR][B][COLOR=#008080]and to read up on linux before I finally make the switch. Got a bit of a handle on sudo now and running programs from a term and editing (slightly) with vim--still working out all the keyboard shortcuts . :P))
[/COLOR]

My Current Setup:
[/B]((Well to be honest, it was the setup right before creating this thread & testing everything thoroughly.))
[/I]* Asus G73JH laptop
* Non-usable DVD drive (watched a lot of DVDs while deployed)
* A single Windows 7 partition
* Wanting to completely replace my windows partition with Ubuntu/Linux.[I]

**What I did:**
[/I]1. Downloaded Wubi from official site.
2. Installed it and realized it's its own virtual image within windows.
3. Then realized I couldn't really ever get rid of windows while it was housing my Ubuntu.
4. Started looking around at partition managers and ways to get a new partition, then hopefully transfer linux to it and my windows files and then delete the windows partition, change the linux partition to incorporate the entire drive and be done with windows finally.[I]

[B]My Guide (or steps) to get it all working:
[/B](After installing Wubi and currently booted into windows.)
[/I]1. I went and got a partition manager from download.cnet.com (the one I used was MiniTool Partition Wizard.) After I hit apply to the new drive settings (ext4 for the new partition as well as having a 16GB swap file) it reset the laptop and booted windows into a program that did the actual work.
2. I then booted back into Windows just to ensure everything was still working and a-ok. ((This is when I realized it touched the virtual image of my current wubi install and I had to uninstall and reinstall wubi after having the partitions setup.))
3. Restarted the PC and went into Ubuntu.
4. Followed the guide here and got the image onto another partition.
5. Copied over all the windows files I needed (mainly my two games) over from the /host folder.
6. Used GParted to remove the windows partition. 
7. I now have Ubuntu but I have a 120GB partition I'm not sure what to do with or how to add into my regular "home?" partition.
[COLOR=#008080]
***I hope this helps anyone or provides insight. It's basically a "rough" version and I'll tidy it up if I can. (Also mods/admins are welcome to spruce it up if anyone wants...heh.) I am now a happy Ubuntu user without having to use my defunct DVD drive or having to buy a new one!***[/COLOR]

---

### Post by BlueTiger33 on 2013-05-13
[COLOR=#008080]***Just to confirm, everything is working a-ok and it's all (mostly) setup exactly how I wanted, including my games. :)***[/COLOR]

---

### Post by dasaint80 on 2013-07-06
Hey all, 

I have a Macbook pro 3,1 with 2 HDD. First drive has OSX installed the second has WIndows 7 and I want to install ubuntu along side. I was getting black screens when trying to install from boot. So i used the Wubi installer from windows, that seemed to work.

Now I'm trying to migrate to the partition for Ubuntu and I get the following error when runing Wubi-move.

```
dasaint80@ubuntu:~/Downloads/wubi-move-2.4$ sudo bash wubi-move.sh /dev/sdb1
wubi-move.sh:  Validating migration source...
wubi-move.sh:  Source for migration validated successfully:
wubi-move.sh:    Wubi host partition: /dev/sdb2
wubi-move.sh:    Size of install: 3772082 K
wubi-move.sh:    Size of /boot: 60695 K
wubi-move.sh:    Size of /usr: 2190409 K
wubi-move.sh:    Size of /home: 103981 K
wubi-move.sh:  Validating migration target(s)...
wubi-move.sh:  Target(s) for migration validated successfully:
wubi-move.sh:    Size of / partition: 219953972 K
wubi-move.sh:  Target partition size is sufficient

wubi-move.sh:  Grub2 will be installed to /dev/sdb

wubi-move.sh:  Please close all open files before continuing.
wubi-move.sh:  About to format the target partition (/dev/sdb1).
wubi-move.sh:  Proceed with format (Y/N)
y
wubi-move.sh:  Formatting /dev/sdb1 with ext4 file system

wubi-move.sh:  Copying files - please be patient - this takes some time
wubi-move.sh:  Copying from / (root)
wubi-move.sh:  Copying from /usr
wubi-move.sh:  Copying from /boot
wubi-move.sh:  Copying from /home
wubi-move.sh:  Copying completed

wubi-move.sh:  Starting chroot to the target install.
wubi-move.sh:  Removing lupin-support on target...
**[COLOR=#ff0000]wubi-move.sh:  An error occurred within chroot[/COLOR]**
[COLOR=#ff0000][B]wubi-move.sh:  Error is: /usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
wubi-move.sh:  Attempting to exit chroot normally...
wubi-move.sh:  Exiting from chroot on target install...

wubi-move.sh:  Migration did not complete successfully.[/B][/COLOR]

```

When I mount the partition that Wubi-moved copied to I can see all files. 

Should I run update-grub?

How can I boot onto the newly copied partition?

Anything I can do about this?


Thanks

Steve

---

### Post by bcbc on 2013-07-06
Steve, I don't have much experience with Macs. Obviously Grub isn't working 'by default' as it should, so I would proceed cautiously - doing some research about dual booting first. The Wubi-move script relies on the expertise of Grub itself and doesn't attempt to 'figure out what to do' since Grub has many experts working on it that know better than me, so I'd be nervous about manually taking control of installing Grub without knowing what you are doing.

In the meantime there shouldn't be any harm running "sudo update-grub" on the Wubi install and then booting the migrated install (which will appear on the bottom of the Grub menu), since it is all copied over and the /etc/fstab should be setup correctly. Then once you figure out what to do, you can install Grub while booted from the migrated install.

Hope that helps

---

### Post by Mephisto Pheles on 2013-09-11
In trying to install/move my xubuntu 12.04.3 LTS wubi I ran into some problems.

The script crashed my desktop in a pretty bad way when I wanted to run it via my XFCE shell... 
my display was displaying "snow" nothing else.. fortunately nothing bad happened.
I made sure there was no more drive activity and had to do a hard reset.
I tried again later with the same result. 
Don't know if this is related to XFCE, or Xorg or my nvidia drivers or whatever else (kernel 3.8?).
Maybe test it yourself.

I finally managed to move it using ctrl+alt+F1on the xubuntu login screen, and working from that shell.
 Maybe a good idea to add this to your instructions; drop to the root shell and excute it from there.

Also.. add using gparted to prepare the partitions - obvious to all but newbies,
but those are very likely the ones who used wubi to start with.

Thanks for the script.

mephisto

---

### Post by bcbc on 2013-09-11
mephisto,

Thanks for the feedback. I'll investigate the problem you reported.

PS I've avoided giving partitioning advice, because that's something that you can find outside of the Wubi-specific migration. But I'll add a link to [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Mephisto Pheles on 2013-09-11
you're welcome, I'm grateful for the script. Doing something back by giving some feedback is the least I can do. ;)

Given the fact that one has to use a shell anyway, I suppose - after my own "psychedelic" experience, and it sure was that, the very weird display I got there - that it's safer to use a shell not affected by any window/desktop manager. Just in case.

- mephisto

---

### Post by bcbc on 2013-09-12
> **JkbrrLJ said:**
> you're welcome, I'm grateful for the script. Doing something back by giving some feedback is the least I can do. ;)

Given the fact that one has to use a shell anyway, I suppose - after my own "psychedelic" experience, and it sure was that, the very weird display I got there - that it's safer to use a shell not affected by any window/desktop manager. Just in case.

- mephisto
I confess, I am a little puzzled as to what could have happened. The script doesn't change anything on the local system except it does create some udev rules to prevent a [problem in 12.04]("http://askubuntu.com/q/121569/14916") that results in a Nautilus window popping up when partitions are mounted. This causes problems with the script (because it cannot unmount the partitions while Nautilus is presenting the window) as well as being visually confusing. I can't recall now whether other file managers respond to this in the same way... e.g. Thunar. Everything else the script does is fairly basic terminal commands (formatting, copying, chroot) - there are no graphical popups/messages etc. 

It's certainly okay to run it from a non-graphical virtual terminal, but shouldn't be necessary. I'd like to avoid root shells as well - generally dangerous and again unnecessary.

Anyway - I'll install 12.04 Xubuntu with Wubi and try it. As long as it's not something hardware-specific to your machine I should be able to figure it out. We shall see.

---

### Post by bcbc on 2013-09-13
mephisto, 

I went to write up an issue on Github and found this: [https://github.com/bcbc/Wubi-move/issues/21](https://github.com/bcbc/Wubi-move/issues/21) (which I had forgotten about). It sounds the same as what happened to you, so I think your issue probably is also a udev bug. I updated a 12.04 (Ubuntu) install I had to 12.04.3 and reran the migration to make sure it's not something incompatible between the script and 12.04.3 and it works fine. I also confirmed that it still needs the udev rule or else it pops up nautilus (so I am reluctant to remove it).

I wonder if you can run:
```
sudo udevadm trigger
```

and see what happens (it should do nothing since the rules won't have changed - it will just reapply existing rules). If it hangs up, try [Alt+SysRq REISUB]("https://en.wikipedia.org/wiki/Magic_SysRq_key") before hard-powering off. Or better, check your logs from the time you ran the migration to see if you had the same issue. Then reporting it as a udevadm bug would probably be best. I can add a Known Issue to the migration page to caution about this, but it's difficult for me to fix via the script without knowing the cause and having some other workaround to prevent Nautilus windows popping up.

I'm still going to load up a Xubuntu install and play around some more... 

PS the wubi migration script writes entries to syslog, so grep'ing /var/log/ for wubi-move will steer you to the right place

---

### Post by cello75 on 2013-09-24
Well I am sorry for the inconveniance but I have made a 'special case': Before I tried to migrate my wubi-installation from /dev/sda3 with its mountpoint /media/UBUNTU I managed somehow (...) to copy my home folder from inside wubi-rootdisk to /dev/sda4. I now would like to migrate from above named directories to /dev/sd4 (second partition-in-line on second s-sata-harddrive) and swap to /dev/sdb3 (now after creating and formatting as ext4 partition /dev/sdb4 FOURTH partition-in-line.... ). BUT the move.sh gives out after typing: 
ubuntu@ubuntu:~/wubi-move-2.4$ sudo bash wubi-move.sh --root-disk=/media/UBUNTU/ubuntu/disks/root.disk --homedev=dev/sda4 /dev/sdb4 /dev/sdb3

the following strange comment (not findable on internet): 

wubi-move.sh:  Validating migration source...
wubi-move.sh:  Root disk (/media/UBUNTU/ubuntu/disks/root.disk) missing required directories.
wubi-move.sh:  If the original release was prior to 9.10 then it can
wubi-move.sh:  not be migrated from the root.disk.
wubi-move.sh:  Validation of migration source failed



Please, WHAT  is: "missing required directories"??? .... in my ubuntu folder on /media/UBUNTU/ there are 3 folders named: disks - install - winboot (in this order) ----> maybe I have to edit move.sh (with gedit, by the way?) 



Thank you in advance for reading
BY THE WAY: 

my rootdisk is about 31 GB in size and my new ext4 partition 32 GB - and my content of 'disks' is the folder 'boot' and the files: rootdisk and swap. In the 'boot'-folder there is only a folder named 'grub' with nothing inside..

---

### Post by bcbc on 2013-09-25
> **cello75 said:**
> Well I am sorry for the inconveniance but I have made a 'special case': Before I tried to migrate my wubi-installation from /dev/sda3 with its mountpoint /media/UBUNTU I managed somehow (...) to copy my home folder from inside wubi-rootdisk to /dev/sda4. I now would like to migrate from above named directories to /dev/sd4 (second partition-in-line on second s-sata-harddrive) and swap to /dev/sdb3 (now after creating and formatting as ext4 partition /dev/sdb4 FOURTH partition-in-line.... ). BUT the move.sh gives out after typing: 
ubuntu@ubuntu:~/wubi-move-2.4$ sudo bash wubi-move.sh --root-disk=/media/UBUNTU/ubuntu/disks/root.disk --homedev=dev/sda4 /dev/sdb4 /dev/sdb3

the following strange comment (not findable on internet): 

wubi-move.sh:  Validating migration source...
wubi-move.sh:  Root disk (/media/UBUNTU/ubuntu/disks/root.disk) missing required directories.
wubi-move.sh:  If the original release was prior to 9.10 then it can
wubi-move.sh:  not be migrated from the root.disk.
wubi-move.sh:  Validation of migration source failed



Please, WHAT  is: "missing required directories"??? .... in my ubuntu folder on /media/UBUNTU/ there are 3 folders named: disks - install - winboot (in this order) ----> maybe I have to edit move.sh (with gedit, by the way?) 



Thank you in advance for reading
BY THE WAY: 

my rootdisk is about 31 GB in size and my new ext4 partition 32 GB - and my content of 'disks' is the folder 'boot' and the files: rootdisk and swap. In the 'boot'-folder there is only a folder named 'grub' with nothing inside..
When you migrate from the root.disk, the script checks to make sure that /home and /usr are all present on the root.disk. If not, it tries to mount additional virtual disks to see if it contains these directories. It does this by mounting the root.disk, looking in /etc/fstab and then loading each .disk file it finds. But it has limitations. First, it assumes that the path to the virtual disk in /etc/fstab is /host/ubuntu/disks/, and secondly it expects that the physical virtual disk file is in the same location as the root.disk (i.e. the path specified with --root-disk=)

So, if you have /home mounted from /media/xxx/home.disk then it won't find it; in this case the message you see is "Root disk (<filename>) missing required directories."

The way around this is to migrate from the running Wubi install, which is always the easiest option. Then /home and everything is mounted already. The root.disk migration is generally only required if you're migrating from a backup or you want to migrate over the partition that you had the root.disk on before.

You could probably manually edit the script if you're comfortable doing that. Look in check-source.sh:
```
# this code goes through each line in /etc/fstab
# and makes sure the virtual disks are not mounted
# and mountable. It assumes that /host/ubuntu/disks/xxx.disk
# means that xxx.disk is in the same location as the current
# root.disk that whose /etc/fstab contains xxx.disk
    while read fDEV fMTPT fTYPE fOPTS fDMP fPASS; do
case "$fMTPT" in
          /home|/usr)
            disks_path=`echo $fDEV | sed -e "s/\(^\/host\/ubuntu\/disks\/\)\(.*\)/\1/"`
            if [ "$disks_path" = "/host/ubuntu/disks/" ]; then
                virtual_disk=`echo $fDEV | sed -e "s/\(^\/host\/ubuntu\/disks\/\)\(.*\)/\2/"`
                if [ ! -f "$rootdiskpath"$virtual_disk ]; then
                   error "Root disk contains a reference to: "$virtual_disk""
                   error "This cannot be found in: "$rootdiskpath""
                   error "Please fix and retry"
                   exit_script 1
                fi
                check_disk_mount "$rootdiskpath"$virtual_disk"\ "
                mkdir -p "$root_mount"$fMTPT
                mount_virtual_disk "$rootdiskpath"$virtual_disk "$root_mount"$fMTPT
            fi
          ;;
        esac
done < "$root_mount"/etc/fstab
}

```

---

### Post by cello75 on 2013-10-01
At first, Thank God I had some time for my little wish to come, Thank you so much for answering. I will exactly try that and post after some time what has happened. love&peace. Cello

---

### Post by cello75 on 2013-10-04
well, thank you again so much for your reply - I copied the named text into check-source.sh over the appropiate lines and executed sudo bash wubi-move.sh /dev/sdb4 /dev/sdb3 (for swap on /dev/sdb3 and new ext4 on /dev/sdb4) but it hangs then (graphics are blurred) and shortlybefore that, I can read something like: "Validation of source failed " ,, mmh - I do not think I can handle this at the moment ,, but thank you so much anyway

---

### Post by bcbc on 2013-10-04
> **cello75 said:**
> well, thank you again so much for your reply - I copied the named text into check-source.sh over the appropiate lines and executed sudo bash wubi-move.sh /dev/sdb4 /dev/sdb3 (for swap on /dev/sdb3 and new ext4 on /dev/sdb4) but it hangs then (graphics are blurred) and shortlybefore that, I can read something like: "Validation of source failed " ,, mmh - I do not think I can handle this at the moment ,, but thank you so much anyway
The migration script has nothing to do with graphics - it's command line only. However, it appears that there is a udevadm bug or at least a bug triggered by udevadm (possibly pulse audio) that does affect graphics. Unfortunately the udevadm is required, otherwise another bug makes Nautilus pop up browser windows whenever the script mounts partitions, which is a) irritating and b) can cause the script to fail by preventing umount operations. [long story]. In any case, a poster a few posts up mentioned that running the script in the VT console (ctrl-alt-f1) was a workaround.

But that doesn't solve your issue. This is what I suggest:
1. create a new thread - this one isn't really for support, it's for discussion of the migration wiki page
2. PM me the thread so I can find it
3. Include your script mods as well as your /etc/fstab on the root.disk (if you have it), or a list of virtual disks
4. provide the command line you use to trigger the script as well as the list of files in that directory
5. you can probably also grep /var/log/syslog to get the wubi-move.sh entries to see how things go (it's not full diagnostics but might help). And note if you are running from a live CD, you need to get this after running the script and before shutting down:
```
cat /var/log/syslog | grep wubi-move
```

I am happy to help. The core of the migration process isn't that complicated and I'm sure we can figure out what's going wrong.

---

### Post by bcbc on 2013-10-04
FYI I've updated the Wiki page to add a link to community partitioning documentation, and also to add a Known Issue regarding the udevadm problem.

I've decided to remove the udevadm trigger (it seems to be more trouble than it's worth) and just add a message to ignore Nautilus windows that pop up. I'll also increase the Timeouts to prevent problems with umount.

I don't have a lot of time to work on the script and test anymore - my wubi machine packed up recently (hdd failure) - so I can't promise when these changes will appear in the script. But as I normally do a new release test anyway,  I'll try to get this out for the release of Saucy. (Note Wubi use has dropped off significantly since it was announced that it would be dropped for 13.04; and I suspect it really will be dropped at some point, maybe even for Saucy; hence I am not too concerned about it lately).

---

### Post by cello75 on 2013-10-04
ok - third announcement of mine: I DID IT !! :-) :-) with MigrateWubiManually - I simply followed the steps and I am already posting from my NEW Ubuntu - thanky you so much for interacting - things get better when you do them together ..

---

### Post by bcbc on 2013-10-04
> **cello75 said:**
> ok - third announcement of mine: I DID IT !! :-) :-) with MigrateWubiManually - I simply followed the steps and I am already posting from my NEW Ubuntu - thanky you so much for interacting - things get better when you do them together ..
Cool :) Glad you got it sorted out!

---

### Post by lesliek2 on 2013-12-30
I want to migrate from having Ubuntu 12.04 running via WUBI to having it installed on its own partitions. To do that, I have first to shrink the very partition on which root.disk and swap.disk are in order to have space to create the additional partitions I need. Those two files occupy a significant part of the used space on that partition. Is it possible to transfer those files to an external drive, so that I can shrink the partition much more than I otherwise could, and then run the migration with the two files on the external hard drive?

---

### Post by bcbc on 2014-01-22
> **lesliek2 said:**
> I want to migrate from having Ubuntu 12.04 running via WUBI to having it installed on its own partitions. To do that, I have first to shrink the very partition on which root.disk and swap.disk are in order to have space to create the additional partitions I need. Those two files occupy a significant part of the used space on that partition. Is it possible to transfer those files to an external drive, so that I can shrink the partition much more than I otherwise could, and then run the migration with the two files on the external hard drive?
Yes there is an option to migrate from the root.disk (while running a live USB/DVD). Note that the live environment has to be the same architecture (32/64bit) as the Wubi install, and I recommend using the same release. 

You don't need the swap.disk for this, only the root.disk (and if you have them usr.disk and home.disk have to be in the same directory as the root.disk). For the syntax see the MigrateWubi page:
[COLOR=#333333][FONT=Ubuntu]
*To migrate from the root.disk when running from a live CD/USB:*[/FONT][/COLOR]
```
sudo bash wubi-move.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda5 /dev/sda6
```

---

