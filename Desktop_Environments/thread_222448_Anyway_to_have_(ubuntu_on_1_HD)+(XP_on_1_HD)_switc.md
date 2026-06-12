---
title: "Anyway to have (ubuntu on 1 HD)+(XP on 1 HD) switch with BIOS?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by shoki on 2006-07-25
Hello All,

Well I got my ubuntu pretty much where I want it. Thing is I want to maintain 2 OS's on one machine without having to dual boot. I think I have things pretty screwed up currently but I thought I could do the following.

ubuntu HD on Primary IDE
unplug XP drive on Secondary IDE
load ubuntu

Plug the XP drive back in and install XP.

Then I can switch between drives with the BIOS. Each drives boot-loader is only aware of it's own drive. I can tweak and reinstall each to my hearts content. 

Here is what I think is the tricky part. Id like to create a 20GB partition on each drive to back the other one up. This way if one drive goes down I can retrieve it from it's backup that is stored on the remaining drive.

Thanks for the help.
--Shoki




Now for a little back story.
-I originally had a 200GB drive on the primary IDE with XP/ubuntu. 
-I yanked out a CD-burner and the floppy and unplugged the 200GB.
-Installed a new 160GB into the primary IDE and installed ubuntu on it.
-Plugged the 200GB into the secondary IDE and rebooted.

results:
-bios set to 160GB ubuntu boots but can't access the 200GB.
-bios set to 200GB pick XP from grub and XP boots.
-bios set to 200GB pick ubuntu from grub ubuntu starts to load and then hangs up looking for missing parts I guess.


I am willing to start completely over format/partition/re-install as needed but I wanted to find out if there was a good way to keep completely separate installs that are selected with BIOS.

The guy at the FRY's suggested a power toggle... I think that would work but I want to be able to use the drives to save data for each other.

Thanks again,
--Shoki

---

### Post by shoki on 2006-07-25
hmmm

Sorry I did some more search tricks and found:

Dualboot Two Hard Drives
[http://ubuntuforums.org/showthread.php?t=179902&highlight=unplug+bios](http://ubuntuforums.org/showthread.php?t=179902&highlight=unplug+bios)

Trying to Dual Boot, using two HD's
[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

heh.

I'll check them out tomorrow. If there is any updated trick to do what I am trying let me know. Also if not anybody know a way i can wake back my old ubuntu on the 200GB drive... after removing/moving drives around?

Thanks again,
--Shoki

---

### Post by andb on 2006-07-25
> **shoki said:**
> 
Now for a little back story.
-I originally had a 200GB drive on the primary IDE with XP/ubuntu. 
-I yanked out a CD-burner and the floppy and unplugged the 200GB.
-Installed a new 160GB into the primary IDE and installed ubuntu on it.
-Plugged the 200GB into the secondary IDE and rebooted.

results:
-bios set to 160GB ubuntu boots but can't access the 200GB.
-bios set to 200GB pick XP from grub and XP boots.
-bios set to 200GB pick ubuntu from grub ubuntu starts to load and then hangs up looking for missing parts I guess.

Thanks again,
--Shoki

First, do you really want to always have to switch bios setings to change the system you boot? If you could have both drives always attached, and grub let you easily (and properly) select between OSes, would that be better? For sure, this is what you'll need for your backup scenario... You can have the seperate OSes ingnore the partitions of the other system in normal operation...

Your result #3, exactly how far does it get, do you see splash screen? If not my first guess would simply be the grub menu settings. Can you post your /boot/grub/menu.lst file? And how are your drives partitioned (the partition numbers are of paticular importance)?

---

### Post by shoki on 2006-07-25
Thanks for the reply.
Primary IDE = Ubuntu/Swap
Secondary IDE = XP/Ubuntu/Swap

I was going to check out GAG but maybe it's more of a gimmik.
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

I did want to keep the drives very independant of each other but still have a clean logical install.

I am learning alot. I haven't had my machine torn down and all over the floor like this for quite awhile.

The ubuntu on the XP drive comes to splash screen... I'll have to watch it to see exactly where it stops. Do you think it's because I moved the drive to secondary IDE or because of the removed/added parts?

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thanks for all the help,
--Shoki

---

### Post by shoki on 2006-07-26
Strange...

I moved the 200GB drive back to Primary IDE and it boots up fine. It did not seem to like being booted from the Secondary IDE (not slave) spot.

Does Linux have a problem booting from the Secondary IDE or could it be my motherboard/bios?

Anyway I'll be using the technique from
 Dualboot Two Hard Drives
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
to do it right using grub.

Thank you,
--Steven Walters

---

### Post by bulldog on 2006-07-26
When you install Ubuntu on one drive and XP on the other,all you have to do is unplug the not wanted hard disk.
And you have two Ubuntu's on two different HDD's if I understand it correct?
Why should you want to do that?
The reason that Ubuntu will not boot is the path isn't correct.
If you want a backup partition format it FAT32 and it is reachable from Ubuntu as XP as well.
I should consider to make a separate /Home on your Ubuntu when you do a fresh install.
If something goes wrong you won't loose your home partition when you do a new install.

If I where you I start all over again and you should install one copy of Ubuntu instead of two.
Make a / partition for Ubuntu of about 10 Gyg and a swap of 1 a 2 Gyg.
Make a /Home partition from the rest of your hdd but keep in mind that you have to make a FAT32 partition for your backups.
You can always mount your NTFS partitions later in Ubuntu, but read only.
Now you can run Fix mbr from your XP-cd on your other hdd with XP on it.
So you get grub removed and XP start up again.
Remove the second Ubuntu on your XP hdd and make a FAT32 partition if you want.
I think it should work this way but it's early here in Holland:D

---

### Post by shoki on 2006-07-26
Hello,

Thanks for the Partition information.
Speaking of that how would you suggest I partition my new ubuntu install?
I have 160 Gigabytes and I think I'd like to set up 4 users. Should I do something like:

/root 15gb
/home user1 34gb
/home user2 34gb
/home user3 34gb
/home user4 34gb
/backup 4gb
/swap 2gb

or is that a bad way to set up the user space?


As far as the 2 drives... I had ubuntu dual booting with XP but decided I like ubuntu so much that I want to run it on it's own hard drive. The ubuntu that is on the XP drive I did a lot of testing and tweeking on. I have the ubuntu pretty messed up but it still runs better and faster than my clean XP install. Banshee 0.11.0-CVS with the podcast plug-in and Democracy Player are doing a great job of grabbing my Audio and Video Casts. I'll start over probably this weekend so I am going to keep using the ubuntu on the XP drive till I do. 

Thank you,
--Shoki

---

### Post by andb on 2006-07-28
Hi Shoki! Sometimes doing it yourself is the best way to learn!

First, there is a great driver for windows xp that will let it read ext2/3 drives. its at [http://www.fs-driver.org/](http://www.fs-driver.org/) . Great stuff. So, if you want to share between systems, dont do fat32, just minimize the NTFS partitions, since now even windows can read ext2/3. The key is that it doesnt use journaling, so it uses ext3 as if it were ext2. Do worries, just dont turn off your machine suddenly ;)

User space. Dont do it. you'll get anonyed when people fill stuff. Unix was designed for multiple users, of course. There's software to handle user space allocation limits. You can set soft limits (user gets a warning email), hard limits, and ever-capacity limits for limited time. Imagine a ruleset like-at 32gig a warning is sent, user can go up to 40gig for 5 days and gets a warning email every day, at five days files are deleted down to 32gig. I think the software either does oldest or largest files first, but dont remember for sure. If yuo really had to have seperate partitions, you could do it with LVM (logical volume management), and when you need more pace you could include more partitions in the group. This one is easier than it sounds, makes growth really easy.   

Want a version of ubuntu or xp to play with? Try emulation! I like Qemu most (simple, free) but for some applications I use VMware Server (no-charge beta, comercial software). The Ubuntu package doesnt support the acceleration module for i386 architecture. Install the package with apt-get if you have AMD, but if you use intel, go to install quemu: [http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+script](http://www.ubuntuforums.org/showthread.php?t=187413&highlight=qemu+script)

Swap 2 gig? Ever look at how much is actually used? Try using 'top' on the command line. Ive got Azureus, aMule, Qaim, Skype, Ekiga, QuodLibet, Swifox, Gnomebaker, Evolution and 4 or 5 more small things running. Mem 512, all used, Swap 512, --14mb-- used. I'm not an expert on memory management, but Ive never needed more than 512. If you do video editing, ok, maybe 2 gig, but then again, if you did that you'd want windows or a mac or avid anyway... Id rather use the space for a film or three.

About booting on the slave, Ive actually never tried moving a system drive between controlers. See the line in menulist.conf that says:
root		(hd0,1)
Probably the drive shifts to (hd1,1). Grub starts numbering at 0, commands like mount and such start at 1. Fun! Im not sure what references are in startup to the actual drive, but thats what happened probably. You could find all the drive references at start up, edit them and it ought to work. Good education. Or you can move it and reinstall. Easy work.

Good luck this weekend. By the way my partitions look like this:
/dev/hda5             1.5G  462M  919M  34% /
varrun                248M  120K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
udev                  248M  152K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  230M   8% /lib/modules/2.6.15-26-686/volatile
/dev/hda3             243M   45M  186M  20% /boot
/dev/hda9              61G   54G  4.1G  93% /home
/dev/hda7             486M   33M  433M   7% /tmp
/dev/hda8             4.0G  2.9G  886M  77% /usr
/dev/hda6             956M  498M  448M  53% /var
/dev/hda2             5.1G  3.4G  1.7G  68% /home/andrew/winxp


Its not like windows where you need gigs and gigs for your programs. Why do I have things seperated? usr can be mounted read-only. Talk about virus proof! Root will never fill up because of some mistake, logs have just enough space... If I install a windows game by the way, I put it in /home.

Hope this has helped a bit, let me know if I've missed something you needed.

---

### Post by shoki on 2006-07-29
Awesome!

Thanks so much. I'll check out Qemu and Ext2 IFS. I am really enjoying ubuntu. They sent me a bunch of stickers so I am putting them on all my PC's and Macs!

Thanks again,
--Shoki

I'll let you know how it goes.

---

