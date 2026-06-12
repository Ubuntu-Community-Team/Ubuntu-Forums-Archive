---
title: "Target Filesystem doesn't have /sbin/init"
date: 2009-05-23
forum: General Help
---

### Post by 9047boy on 2009-05-23
Hello.

I cannot boot my ubuntu 9.04. When it tries ti mount the filesystem at boot i get this error : Target Filesystem doesn't have /sbin/init .

I booted from a livecd and tried to mount the partition and i got this error :

ubuntu@ubuntu:~$ sudo mount -t ext4 -o rw /dev/sda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg|tail returns : 

ubuntu@ubuntu:~$ dmesg|tail
[  249.564577] sd 2:0:0:0: [sda] Write Protect is off
[  249.564581] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  249.564624] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  249.564672] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[  249.564697] sd 2:0:0:0: [sda] Write Protect is off
[  249.564701] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  249.564742] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  249.564752] JBD: Failed to read block at offset 23189
[  249.564761] JBD: recovery failed
[  249.564765] EXT4-fs: error loading journal.

Tried an fsck also and this is what i get :

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

I'm stuck at this. Could someone tell me what to do ? If not to boot , at least to recover my data from the disk. Thank you.

---

### Post by KhurramM on 2009-05-23
use recovery mode on the grub.

It will auto-fix your issue.

This is the safest.

Else it might be ext4 issue.

Or n live mode see if it is mounted?

use:

cat /proc/mounts

if yes then umount it, or go into it if possible.

---

### Post by 9047boy on 2009-05-24
Ok . I managed to fix the problem by checking the partition with the partition editor from the live cd , which is basically :

e2fsck -f -y -v /dev/sda2

This seems to have solved the problem .

---

### Post by The Knight on 2010-04-24
Just want to say that I had the same problem and that this worked for me too - so thank you :]

---

### Post by 9047boy on 2010-04-25
Glad you could fix it :D

---

### Post by spoolboyy on 2010-05-14
This solution solved my problem as well on 10.04, boot failed and I didn't even make it to Grub.

I had the warning:

> 
target filesystem doesn't have /sbin/init
No init found try passing init = bootarg


While booted into the live CD for 10.04, my boot drive wouldn't mount giving me some error I forgot to write down (sorry).  

If anyone stumbles across this problem in the future, here's how to start gparted fromthe live CD for those who'd like to use this method:

> 
sudo gparted


once there, you can select your hard disk from the drop down menu at the upper right corner of the software.  As long as the drive/partition you are interested in repairing is unmounted, you can right click on it and select 'Check.'  This has the effect of checking the disk and if possible, repairing any issues, (for those from the windows world its much like chkdsk).

I drilled down into the 'Details' view of the Check and it showed the exact same command that 9047boy used (except of course with my partition name instead of his):

> 
e2fsck -f -y -v /dev/sdb1


Thanks a million 9047boy and I hope this helps others in the future!

-Adam

---

### Post by nash108 on 2010-06-18
I also have the same problem .. it comes  up with 

mount: mounting /dev/disk/by-uuid/020c2c5b-59ec-49cf-a0d5-6bc9c1bee82f on /root failed: Invalid argument 
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  

How to solve this ? :( I don't have the live CD. if we use recovery mode on the grub. the thing is when I go to the grub menu .. which one do I choose ? on my grub menu I have ..

Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

help me :(

---

### Post by requimrar on 2010-06-22
> **nash108 said:**
> I also have the same problem .. it comes  up with 

mount: mounting /dev/disk/by-uuid/020c2c5b-59ec-49cf-a0d5-6bc9c1bee82f on /root failed: Invalid argument 
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  

How to solve this ? :( I don't have the live CD. if we use recovery mode on the grub. the thing is when I go to the grub menu .. which one do I choose ? on my grub menu I have ..

Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

help me :(

Ok. First, I would like to ask you how you are writing this if you have an unbootable ubuntu. If it's from a dual boot Windows, then you can go to Ubuntu's site and download and burnit to CD or DVD and boot. If not, then you choose Memory Test first, as sometimes this is a memory problem. If memchk passes, use the latest recovery console(2.6.32-22) for yours. Else, I'm also stuck. I have a similar problem... also take note that you should NEVER format that liveCD of yours, no matter how old it is. I personally have every liveCD from 5.04 to 10.04. NEVER throw them away. sometimes old is reliable.

---

### Post by Transmutable on 2010-08-19
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  

(initramfs)

I am getting this as well. I have a LiveCD of 10.04 but when I boot from that I just get the purple Ubuntu screen and the dots just keep changing from white to orange and back again. I have tried it on another computer and it will boot, so it's not the CD (it's brand new). I'm really stuck. :( 

I haven't updated recently, but my laptop battery died this morning and when I plugged it in and restarted, that's when this started happening.

---

### Post by Transmutable on 2010-08-19
I made a CD of 8.10 (9.04 and 9.10 have some weirdness with my hardware) and that boots up fine. But I really don't know what to do from there...

---

### Post by Transmutable on 2010-08-23
Oh this is maddening, when I boot from the 8.10 LiveCD, it doesn't boot all the way. I get the Ubuntu logo with the orange status bar below it; the orange bounces back and forth for a while and then starts to fill up. When the bar is full the screen flashes a few times like it used to and then... nothing. Just a backlit black screen. Meanwhile, 10.04 is still thinking about white and orange dots.

I'm almost thinking of just backing up my hard drive and doing a complete reinstall, but restoring my data has been utter chaos every time I've had to do that before. There just has to be an easier way.

---

### Post by georges2051 on 2010-08-30
**Re: Target Filesystem doesn't have /sbin/init**             
                                                                This solution solved my problem as well on 10.04, boot failed and I didn't even make it to Grub.

I had the warning:

     Quote:
                                                 target filesystem doesn't have /sbin/init
No init found try passing init = bootarg                                 

Per the other posts I ran the live cd.
While booted into the live CD for 10.04, my boot drive wouldn't mount either.

 
While running the live cd disc I went to the applications / accessories and terminal
and typed sudo (space) and the following command as directed by the previous posts
                                            e2fsck -f -y -v /dev/sdb1                                 
Thanks to  9047boy and spoolboyy for their notes...saved my bacon !!!
Much apprceiated !!!

George

---

### Post by El_Cucuy on 2010-10-06
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb1 
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ 

Looks like my HD is dead

---

### Post by GriFF3n on 2010-11-11
> **9047boy said:**
> Ok . I managed to fix the problem by checking the partition with the partition editor from the live cd , which is basically :

e2fsck -f -y -v /dev/sda2

This seems to have solved the problem .

Had the same problem and this worked for me as well. Anyone know what causes this problem?

---

### Post by zahanm on 2010-11-13
If the 10.04 live disk refuses to load past the little dots stage.
Hit the right arrow key and you might see this: GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0) ) - then just use an older Ubuntu distro.

[Karmic]("http://releases.ubuntu.com/karmic/") works well, for instance.
I didn't try 10.10 as I just assumed it would be even more buggy.

From then on out
> sudo gpartedand you know the rest.

Thanks for the help!

---

### Post by skakillers on 2010-11-23
I'm getting the same error as the OP on boot. I've booted to a livecd to try to repair my partition, but when I run 
    sudo e2fsck -f -y -v /dev/sda2
I get the output
    e2fsck: Device or resource busy while trying to open /dev/sda2
    Filesystem mounted or opened exclusively by another program?

If I look in my /dev folder there's nothing there, and executing
    sudo umount /dev/sda2
returns
    umount: /dev/sda2: not mounted
I also cannot open gparted, if I try from the system menu it just closes, but if I open from the command line with
    sudo gparted
it returns
    glibmm-ERROR **:
    unhandled exception (type std::exception) in signal handler:
    what: basic_string::_s_create

what do I do?

---

### Post by skakillers on 2010-11-23
Further info:
gparted won't launch from the livecd, but disk utility will. I've been able to run the check and repair function from there, but all it returns is

This filesystem is NOT clean!

and it doesn't seem to do anything else. I thought the drive might be failing, so I did a read speed test, again using disk utility, and it worked fine. This indicates that there is nothing physically wrong with the disc. I'm just unsure of what is wrong with my filesystem, or what it is that's going on. I can't even get the disk to mount so I can get my files off and go for a reinstall.

---

### Post by skakillers on 2010-11-23
I really need help with this, the problem is on my laptop, and I'm about to go home for Thanksgiving where it will be my only machine. I have schoolwork I absolutely have to get done this week that requires the use of LaTeX, and I also have files on the laptop that are not backed up. All of my schoolwork is in my dropbox, so that's not an issue, but I'd prefer not to lose a bunch of photographs if I have to do a clean reinstall.

---

### Post by ezzie on 2010-11-24
I had the same problem as [skakillers]("http://ubuntuforums.org/member.php?u=787998"), I attempted to start ubuntu and got the error "target filesystem doesn't have /sbin/init."
So I booted ubuntu off my USB drive to run fsck as I had a similar problem before and this had worked for me. But fsck returned "Device or resource busy while trying to open /dev/sdc1 Filesystem mounted or opened exclusively by another program?"
When I ran " e2fsck -f -y -v /dev/sdc1" I got the same error.

I gave up last night and this morning I started at it again, and ubuntu notified me of a crash of "gvfs-gdu-volume-monitor" I thought this may be what was making the drive busy, so I ran "fsck -f /dev/sdc1" again and it worked.

So skakillers, you could try going system>administration>system monitor. Then going to processes and killing gvfs-gdu-volume-monitor if that doesn't work then try killing the other "*-volume-monitor" ones.

Let me know if it works. Although, if it doesn't then I have no idea what else to do, I was out of ideas when this happened, I was just lucky.

---

### Post by Gruu on 2010-11-28
> **ezzie said:**
> I had the same problem as [skakillers]("http://ubuntuforums.org/member.php?u=787998"), I attempted to start ubuntu and got the error "target filesystem doesn't have /sbin/init."
So I booted ubuntu off my USB drive to run fsck as I had a similar problem before and this had worked for me. But fsck returned "Device or resource busy while trying to open /dev/sdc1 Filesystem mounted or opened exclusively by another program?"
When I ran " e2fsck -f -y -v /dev/sdc1" I got the same error.

I gave up last night and this morning I started at it again, and ubuntu notified me of a crash of "gvfs-gdu-volume-monitor" I thought this may be what was making the drive busy, so I ran "fsck -f /dev/sdc1" again and it worked.

So skakillers, you could try going system>administration>system monitor. Then going to processes and killing gvfs-gdu-volume-monitor if that doesn't work then try killing the other "*-volume-monitor" ones.

Let me know if it works. Although, if it doesn't then I have no idea what else to do, I was out of ideas when this happened, I was just lucky.

I had the same problem as you did, but I couldn't get it to work using an Ubuntu LiveCD, since Ubuntu always mounts the drive. Instead, I used slax ([http://www.slax.org/](http://www.slax.org/)) and ran the same e2fsck command, which worked perfectly and solved my problem.

---

### Post by JoelBondurant on 2010-12-03
Thanks 9047boy, I had the same problem on Ubuntu 10.10 and just ran the partition fixer utility (which said it ran that command). Problem fixed.

---

### Post by tolhe on 2011-01-12
I am having the same problem on an Ubuntu VM in VirtualBox on a Windows 7 machine. How can I apply the live cd fix mentioned earlier on this machine.

Thanks,
tolhe

---

### Post by mlduncan96 on 2011-01-18
Well, after my Ubuntu netbook wouldn't start this morning this thread seemed to be most like what I was experiencing. But I couldn't get the USB CD drive to mount with the disc I used to install the OS on my netbook. I got all kinds of errors. I took it back home from work and used an earlier version I had on a USB drive and was able to get it to boot to the USB. When I tried the command I got the same message as El_Cucuy did earlier thinking his HD was bad. I brought up the drive and it said it was healthy and earlier test showed it was okay also, as well as the memory. I tried the command a second time and it worked the second time. I don't know what the difference was, but it worked! So I am up and running again. Thanks everyone for you help in recording what you have experienced and done.

---

### Post by I hate my life on 2011-01-19
I've been using Ubuntu 10.10 for a few weeks.
Just like everyone else here, I applied new updates last night, from the Update Manager.
This morning it doesn't boot. I takes me to a screen with boot options, none of which work, instead showing Ash, which won't let me do anything, no functions work.
I managed to boot off a Live USB after several failed attempts, and Disk Utility is telling me I have 10 bad sectors, but won't let me mount or repar the disk. Please, what should be the next step?

Acer Extensa 
4420-5817
Ubuntu 10.10 single boot
Broadcom wireless built in

---

### Post by kOoLiNuS on 2011-02-22
the Gparted LiveCD worked for me too (with an Ubuntu 10.04, ext4, installation)

---

### Post by Wi11 on 2011-02-24
I have the same problem as everyone else in this place has had. I've tried just about everything that everyone has posted except for Slax, which I am moving onto next, and the GParted LiveCD. I am holding out hope that one of those work..
 
I keep getting the "Filesystem is busy or possibly opened by another program" when I try terminal, even after I have booted from the Ubuntu 10.04 LiveCD and tried every other option this forum gave. If Slax or the GParted CD doesn't work I will be at my wits end.
 
When I try the Gparted in the terminal it pops up and I run check and apply, but it doesn't work either. While I would hate to have to do a fresh install that is what it is looking like for me at this point, that is if Gparted CD or Slax doesn't work for me first.
 
I am just wondering if I have missed something during everything, is there anything else I can try? I can't unmount the thing in Gparted, the umount is greyed out, and when I try to mount it by going through Computer it just pops up an error. 
 
Going to try Slax now, hopefully it all works out, if not I don't know. Thanks for any information anyone might be able to provide, and the time you took to answer this post in the first place.

---

### Post by natman on 2011-02-28
Hey,
Just a piece of advice if you need to do a fresh install, make sure you create separate partitions for / and /home that way you can re-install again and again without losing your /home.
Good luck!

---

### Post by kask1984 on 2011-03-17
had a same problem in ubuntu 10.10 could fix it by 9047boy's solution thanks a lot.

---

### Post by Geiseric on 2011-03-24
Thanks so much 9047boy. I often use this forum but have never created an account so I can says thanks - but the live CD for 10.04 really got me out of trouble.

---

### Post by ChiJoan on 2011-04-04
Yippee!! Thank you Barry and the Puppy Linux team. Last night, I tried their Puppy LuPu 511, which could at least mount and see my files after an unclean shutdown seemed to have occurred. But I wanted help for a fix of some kind. After all I know how to repair WinXP with their CD.

Well it seems my prayers were answered and Puppy LuPu 525, just released on Distrowatch.com did the repair automatically without the command line. Hey, that's even better than Window$ or OpenSuse, that resorts to command line still, as far as I know.

Now to let Distrowatch and a few other places know about this lifesaver.

Joan in Reno

---

### Post by g.gasp on 2011-06-06
> **9047boy said:**
> Ok . I managed to fix the problem by checking the partition with the partition editor from the live cd , which is basically :

e2fsck -f -y -v /dev/sda2

This seems to have solved the problem .

Good afternoon,

I am an new member and I have the same problem as the one above. I have Ubuntu 10.04 dual boot with windows 7 and there was not any problem until this morning. I was writing in my pc when everything stuck. I reboot it but I saw the message: Target Filesystem does not have /sbin/init and all the other thing. I tried various things I read on internet but nothing worked. I am now writing using a live cd (Ubuntu 8.04). I executed the command:
sudo e2fsck -f -y -v /dev/sda3 but it displayed:

e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3 has unsupported feature(s): extents FEATURE_I9 huge_file gdt_checksum dir_nlink extra_isize
e2fsck: Get a newer version of e2fsck!

To begin with, after executing : sudo fdisk -l it shows:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84c9f6cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10199    81816576    7  HPFS/NTFS
/dev/sda3           10199       15055    39007232   83  Linux
/dev/sda4           15055       60802   367457281    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           15298       60802   365504512    7  HPFS/NTFS
/dev/sda6           15055       15298     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order

and as I understand my linux is on /dev/sda3.

I tried sudo apt-get update in order to get a newer version but nothing changed.
I also used other live cds such as 8.10, 9.04, 9.10, 10.04 but in all I have the same problem. They cannot see any device. So I couldn't do anything. 

What can I do?

thnx in adcance,

george

---

### Post by g.gasp on 2011-06-06
> **g.gasp said:**
> Good afternoon,

I am an new member and I have the same problem as the one above. I have Ubuntu 10.04 dual boot with windows 7 and there was not any problem until this morning. I was writing in my pc when everything stuck. I reboot it but I saw the message: Target Filesystem does not have /sbin/init and all the other thing. I tried various things I read on internet but nothing worked. I am now writing using a live cd (Ubuntu 8.04). I executed the command:
sudo e2fsck -f -y -v /dev/sda3 but it displayed:

e2fsck 1.40.8 (13-Mar-2008)
/dev/sda3 has unsupported feature(s): extents FEATURE_I9 huge_file gdt_checksum dir_nlink extra_isize
e2fsck: Get a newer version of e2fsck!

To begin with, after executing : sudo fdisk -l it shows:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84c9f6cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10199    81816576    7  HPFS/NTFS
/dev/sda3           10199       15055    39007232   83  Linux
/dev/sda4           15055       60802   367457281    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           15298       60802   365504512    7  HPFS/NTFS
/dev/sda6           15055       15298     1951744   82  Linux swap / Solaris

Partition table entries are not in disk order

and as I understand my linux is on /dev/sda3.

I tried sudo apt-get update in order to get a newer version but nothing changed.
I also used other live cds such as 8.10, 9.04, 9.10, 10.04 but in all I have the same problem. They cannot see any device. So I couldn't do anything. 

What can I do?

thnx in adcance,

george

Hello again,

could anyone help me because I am in a very difficult condition right now.

Thanx again

---

### Post by Chepech on 2011-06-30
I have the same issue but in my case its happening every 2 or 3 weeks (it has happened 5 times now). The way I fixed is booting from a live cd (I have a Ubuntu v9.10) and selecting **Check disk for errors** This solves the problem. But my concern is that eventualy it happens again. How do I get rid of this for good?

---

### Post by Objekt on 2011-06-30
I had the subject problem earlier today.  The system (an Acer netbook) would not resume properly from hibernation, getting stuck at a perpetually blank screen.  I had to cycle power manually.  Afterward, I got the filesystem errors and could not proceed further than the "intramfs" prompt.

Fixed it with Gparted.  I do wonder what happened with the hibernate session, however.  It worked fine until now.

---

### Post by lukejohnson on 2011-07-11
I was receiving a similar message when booting to Ubuntu 10.04 and was at a bit of a loss on what to do. I tried what you suggested it worked great. 

Thanks 9047boy for the suggestion. 

After reading the man I have one thought (sorry if someone else pointed this out) but I would suggest not using the -y option unless you are sure that you have the drive unmounted. The man file warns against saying yes to preceding with a mounted drive.

---

### Post by simonrose on 2011-07-19
> **spoolboyy said:**
> This solution solved my problem as well on 10.04, boot failed and I didn't even make it to Grub.

I had the warning:



While booted into the live CD for 10.04, my boot drive wouldn't mount giving me some error I forgot to write down (sorry).  

If anyone stumbles across this problem in the future, here's how to start gparted fromthe live CD for those who'd like to use this method:



once there, you can select your hard disk from the drop down menu at the upper right corner of the software.  As long as the drive/partition you are interested in repairing is unmounted, you can right click on it and select 'Check.'  This has the effect of checking the disk and if possible, repairing any issues, (for those from the windows world its much like chkdsk).

I drilled down into the 'Details' view of the Check and it showed the exact same command that 9047boy used (except of course with my partition name instead of his):



Thanks a million 9047boy and I hope this helps others in the future!

-Adam

I have the same problem. Ran the above fix and can mount the HDD under the live CD but when I reboot I get the same error:

Target filesystem doesn't have /sbin/init.
run-init: /etc/init: Permission denied
[    1.982792] Kernel panic - not syncing: Attempted to kill init!

I then can't do anything other than hard reboot...

Any ideas on what I need to do to fix this?

Thanks
Simon

---

### Post by kessi on 2011-07-29
Thanks to spoolboyy and 9047boy. I managed to fix the problem. I followed their recommendations.
Booted with the live CD for 10.04. Did the trial install choice.
Once the desktop came up giving me access to the top panel, I clicked on Applications>Accessories and opened a terminal window.
Entered: sudo gparted.
Checked and my unmounted volume was sda1.

Went back into terminal window and entered:

e2fsck -f -y -v /dev/sda1
A whole lot of data was processed.

I then shut down and after my CD was spat out I rebooted.

Bob's your uncle, all is back to normal.

This is my first post just to thank the folk who help so much to keep us going with their knowledge.
cheers
kessi

---

### Post by mosaic2s on 2011-07-30
> **spoolboyy said:**
> This solution solved my problem as well on 10.04, boot failed and I didn't even make it to Grub.

I had the warning:



While booted into the live CD for 10.04, my boot drive wouldn't mount giving me some error I forgot to write down (sorry).  

If anyone stumbles across this problem in the future, here's how to start gparted fromthe live CD for those who'd like to use this method:



once there, you can select your hard disk from the drop down menu at the upper right corner of the software.  As long as the drive/partition you are interested in repairing is unmounted, you can right click on it and select 'Check.'  This has the effect of checking the disk and if possible, repairing any issues, (for those from the windows world its much like chkdsk).

I drilled down into the 'Details' view of the Check and it showed the exact same command that 9047boy used (except of course with my partition name instead of his):



Thanks a million 9047boy and I hope this helps others in the future!

-Adam

I have similar issue. Backing up data presently after booting through liveCD and connecting to network. will try gparted as suggested to run the check.

unmounted the hdd. then ran the chk on the linux partition, works fine. thanks everyone. saved me much time.

though i am not able to use the USB ports since then.

---

### Post by alvin727 on 2011-08-06
> **nash108 said:**
> I also have the same problem .. it comes  up with 

mount: mounting /dev/disk/by-uuid/020c2c5b-59ec-49cf-a0d5-6bc9c1bee82f on /root failed: Invalid argument 
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  

How to solve this ? :( I don't have the live CD. if we use recovery mode on the grub. the thing is when I go to the grub menu .. which one do I choose ? on my grub menu I have ..

Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

help me :(


I had a similar issue with UBUNTU 10.04 on my hard drive.  I caused my own problems by interrupting the boot cycle.   I tried to use UBUNTU 10.04 Live CD to fix it, but got the same messages.  The 10.04 Live CD would not load, it worked in the past.   

I tried a UBUNTU 11.04 Live CD and it loaded just fine.  I installed a fresh version of GRUB and everything is back to normal with the UBUNTU 10.04.  

Very strange - go figure!!!

---

### Post by cyber-monk on 2011-10-04
Using VirtualBox on Windows 7 and Ubuntu 10.04 as the guest OS.  My system crashed and then when restarting the VM (to a clean snapshot) I was getting bumped into the ```
initramfs
``` prompt.  I used the **10.04 live CD** and tried both command line and gparted to clean up the disk  

  ```
$> e2fsck -f -y -v /dev/sda1  (or use sudo gparted)
```

I was getting the following error:

  ```
Filesystem mounted or opened exclusively by another program?
```

I came across this page [[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526")] and realized that **the 10.04 live CD doesn't work, but the 9.10 live CD does**.  You can download the 9.10 live CD here [[http://old-releases.ubuntu.com/releases/9.10/ubuntu-9.10-desktop-i386.iso]("http://old-releases.ubuntu.com/releases/9.10/ubuntu-9.10-desktop-i386.iso")]

---

### Post by kozlex on 2011-10-27
Thanks all for your comments. 

I fixed this using slax as posted before. I could't execute e2fsck since looks like sda1 was mounted while using a "live CD" which actually was a .iso loaded at virtualbox.

I had a vm with ubuntu and the issue described. I installed slax on the same vdi then on slax terminal executed:

e2fsck -f -y -v /dev**/hda1**

Notice that I used hda1 instead of sda1. Of course on sda1 was my ubuntu distro installed.

Regards!
.Kozlex

---

### Post by kozlex on 2011-10-27
IMPORTANT! It is highly recommended that after you system has been recovered execute again e2fsck; if not you might experience some freezing or grub lost.

If grub is lost try again your recovery from slax, then apply immediatly internal e2fsck.

Happy programming! 
.kozlex

---

### Post by cuthbert75 on 2011-11-17
Hi!
I have 2 hard disks connected do 2 different controllers on motherboard. One has ATA connector and work on first controller  and the second one has SerialATA connector and works on second controller. Unfortunately my motherboard has only one ATA connector.

From a long time ubuntu has recognized my disks as sda (ATA) and sdb (SerialATA).  In the past I had situation when system swapped my disks so in fstab I named my disks by UUID.

A few days ago I've got "Target Filesystem doesn't have /sbin/init" message.
I'm 100% sure the reason is that BusyBox tries to mount system from sda but my system is on sdb disk. When I switch off ATA disk (physically), my system starts normally.
The bad news is that I can't to force my system (BusyBox?) to start from sdb disk.

One more thing: GRUB starts correctly from sdb disk.

My system is Kubuntu 11.10.
Regards
Andrzej

---

### Post by chorew on 2012-02-20
> **9047boy said:**
> Ok . I managed to fix the problem by checking the partition with the partition editor from the live cd , which is basically :

e2fsck -f -y -v /dev/sda2

This seems to have solved the problem .

Thanks!!!!

That solved my problem.

---

### Post by Pramod8 on 2013-03-11
i am using 2 hard disks

one file was deleted and while rebooting i got following error

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have eequested /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) build-in shell (ash)
Enter 'help' for a list of bulit-in commands.

(initramfs)

i tried
used live CD in terminal

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e48a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         426     3417089    5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sda2             426        9730    74732544   83  Linux
/dev/sda5               1         183     1464320   82  Linux swap / Solaris
/dev/sda6             183         426     1951744   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96b196b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         128     1024000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2             128         319     1536000   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sdb3             319        9729    75588161   83  Linux
ubuntu@ubuntu:~$ 



-- any solution to this problem

---

