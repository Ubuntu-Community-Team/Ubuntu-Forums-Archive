---
title: "dell dimension e520 unable to install ubuntu 9.10"
date: 2009-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SuperEngineer on 2009-11-08
[FONT=Tahoma]UNABLE TO INSTALL 9.10 either as a full install from the CD or running in windows (XP) - the install hangs(?) shortly after the 9.10 'spotlight' splash - I have waited for 2 hours for the 'busy' icon to disappear or for further HDD activity. Running as a 'live cd' all is ok (but wireless USB dongle will not connect to the wireless network - the wireless network itself IS recognised).
I initially tried an upgrade from 9.04 to 9.10 but was very disappointed with the [slower?] boot & loss of internet (same symptons as described above), so I deleted the partition and went back to 9.04. I have now done this twice -same result both times. On (twice) trying a fresh install from scratch (Jaunty completely removed first) there are many, many 'squashfs' errors shown during the (failed) install. Install fails. Hard disk checks out ok as do the several CD's tried,

see [https://answers.launchpad.net/ubuntu/+question/89090](https://answers.launchpad.net/ubuntu/+question/89090) for full story

I also found this old thread and wonder...
(April 2008 thread in Ubuntu Forums)

[/FONT] [FONT=Tahoma]"Ubuntu wont install on a Dell Dimension E520"
[http://ubuntuforums.org/showthread.php?t=744640](http://ubuntuforums.org/showthread.php?t=744640) is the URL.[/FONT] 
 [FONT=Tahoma]Any possibilty that this could be a reintroduced SATA driver / SATA support problem that was cured in or before 9.04 but re-introduced in 9.10?
(I have 2 SATA disks fiited, 1st as main disk & 2nd for back-ups).[/FONT]
[FONT=Tahoma]
[/FONT]
[FONT=Microsoft Sans Serif][FONT=Tahoma]Thanks in anticipation for any clues or help.[/FONT][/FONT]

---

### Post by ridgeland on 2009-11-09
I have Ubuntu 9.10 and MythBuntu 9.10 running on my Dell E520N.  I have two SATA drives.  I bought this PC from Dell without Windows, just Ubuntu.  So I can only report that my Dell E520 can run 9.10.  I wish they had not gone with Grub2 (rather Grub-almost-2).

---

### Post by SuperEngineer on 2009-11-10
the problem does not seem to be running 9.10 - it ran ok when 9.04 upgraded TO 9.10.  The problem is actually installing 9.10 from scratch (to gain benefit of faster boot etc.)  the problem replicates everything found in the [FONT=Tahoma]
[http://ubuntuforums.org/showthread.php?t=744640](http://ubuntuforums.org/showthread.php?t=744640) refered to.

I'm jealous if you got it running from a fresh install rather than upgrade from 9.04 - let me know the magic sometime :D
 [/FONT]

---

### Post by ridgeland on 2009-11-11
I'll add a little detail.
I posted a bug report about this issue.
[http://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441907](http://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441907)
called:
grub2 cannot boot when installed on sdb (hdb1)

In my case Grub2 is the problem.  Ubuntu 9.10 installs Grub2, the user does not get a choice.  The user does not get a choice of installing to a partition rather than MBR either.  Big point for Mandriva 2010.0 which still lets the user choose how grub is installed.

Grub2 forces me to install only on sda.  Installing to anywhere on sdb bricks the PC.  Unfortunately I had /Data on sda and OS partitions on sdb.  I only had three sda partitions for OS.  Fortunately I don't have a Windows partition.  My work-around was to physically swap the drives in the computer and change /etc/fstab for all the Linux OSes that I have.  Grub2 can boot the sdb partitions by just editing /boot/grub/grub.cfg (something that is "forbidden")

What do you have for partitions and where are you trying to install Ubuntu 9.10? ($ df) Maybe I could suggest something.

---

### Post by SuperEngineer on 2009-11-14
Sorry for late reply. I've been away on a course and the little spare time I had was spent on work emails, updating bug report in Launchpad and the like (bug# 478547) 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478547)

I have windows xp and ubuntu 9.04 both on sda  (I can't remove xp as I need it for support reasons and 2 windoze only utils I need - I dont want to use Wine and comprimise the smug smile I have when in a linux system).

SO...  my setup is:

sda... windowsXP & Ubuntu9.04
sdb... backups etc.

sda:
  sda1 ntfs (windows) 78GB
  sda2 extended partion  (155GB) as:
    sda5 ext3 Ubuntu
    sda6 ext3 Ubuntu 9.04 (mount-point /)
    sda7 linux-swap

sdb:
  sdb1 ntfs (55GB)
  sdb2 ext3 (20GB)

Cheers, & thanks in advance for any help or ideas.

---

### Post by et_tu_brute on 2009-11-14
I have only run this virtualised my Dell e520 via VirtualBox withot problems, however on my Dell Studio XPS 1640, I had all sorts of issues trying to install, mostly related to missing drivers etc. That was with the 32 bit CD ISO version.

I checked the Dell Community forums and I saw a suggestion re the DVD edition having most of the applicable drivers that suit Dell hardware that are missing from the CD edition. I have just downloaded the DVD 64 bit edition ISO and it installed quickly without hitches, including going and getting the ATI video drivers. Wireless-N worked without a hitch immediately which was a problem with the CD edition.

Whilst not directly related, the DVD edition may help you resolve the problem. Check the Dell Community forums as well as you may also meet a fellow traveller there who has had the same issue.

Good luck

---

### Post by ridgeland on 2009-11-14
I partition like this:
```
/dev/sda14                9273      6444      2359  74% /
/dev/sda1                  981       205       726  23% /UserHome
/dev/sda5               196858    160244     26615  86% /mnt/sda5_Data
/dev/sda6                 9281      4802      4008  55% /mnt/sda6
/dev/sda7                 9273      5867      2936  67% /mnt/sda7
/dev/sda8                 9281      1647      7163  19% /mnt/sda8
/dev/sda9                 9273      5250      3552  60% /mnt/sda9
/dev/sda10                9273      5318      3485  61% /mnt/sda10
/dev/sda11                9281      4802      4008  55% /mnt/sda11
/dev/sda12                9273      2709      6094  31% /mnt/sda12
/dev/sda13                9281      1823      6988  21% /mnt/sda13
/dev/sdb1                 2950        69      2732   3% /mnt/sdb1
/dev/sdb5               190387    153903     26814  86% /Data
/dev/sdb6                 9845      3483      5862  38% /mnt/sdb6
/dev/sdb7                 9845      2711      6635  30% /mnt/sdb7
/dev/sdb8                 9837      2377      6960  26% /mnt/sdb8
```
Don't know how clear that will display but I mount /dev/sdb8 on /mnt/sdb8
I use large Data partitions and 10GB OS partitions.  That way I have lots of partitions to try a new distro or version and not let go of past versions for awhile.  It's not the same as a /home partition because /home has user settings specific to the OS.  Data is jpg, mp3 etc which are OS independent, also "cp -a" backups of keeper OS partitions.
I would split the 155 GB partition into more 10 GB partitions for OS and keep a large Data partition.

Reading the bug report the problem may or may not be grub2, as was my case.  I install to sda with grub2 with no problem.  Since you did install that means you are now using grub2, no?  Try in grub2's grub.cfg to comment out the search line (change grub.cfg to rw first).  I found it causing hangups for me.

---

### Post by ridgeland on 2009-11-14
et_tu_brute,
Good idea.
I'm using on-board Intel graphics and no issues with drivers.  I think Intel got the drivers into the kernel.  I had similar issues with 9.04 and an old Dell monitor when the monitor went to "Out of Range" and there boot ended.  There xorg edits can help.

---

### Post by SuperEngineer on 2009-11-15
Thanks to both Ridgeland and et_tu_brute.

To be honest I wasn't even aware that a DVD edition was available!  Will give that a look next week hopefully. Cheers, et_tu_brute.

Ridgeland's idea re splitting the 155GB partition was already on my list of things to do... but then I backed away from the idea thinking 'get 9.10 installed first and get the exisiting partitions shrunk during 9.10 install - hoping (or just being lazy perhaps) that the 9.10 install partition manager would get some of the work done at the same time as the install.  Unfortunately the install didn't get to that point and after 3 or 4 attempts it was time to get back to a clean 9.04 install and recover etc etc !!!

Thanks for the reminder, Ridgeland, guess it's time to get round to doing it  :)
Question... is it best to leave the 'spare' partition/s as any particular file system or just leave them unformatted?

Thanks for help to date and again, thanks in advance for any help and suggestions.

---

### Post by ridgeland on 2009-11-15
I cannot think of a reason to leave any space unformatted.
During a Linux installation you can choose to reformat an ext3 partition to ext4, etc.  Installation lets you resize too, but I've never done that.  I use gparted for such tasks.  
Since you still have Windows you may want to put the Data in an NTFS file system so Windows can play the mp3s.  Then you loose Linux features like file permissions and links.  Data you want to share between Linux OSes should be in a Linux partition ext2, ext3, ext4.
I stop at 15 partitions because I had trouble trying to use a 16th partition.  I like having enough partitions to have Mandriva, Fedora and SuSE as well as Ubuntu 7.04, 8.10, 9.04 and 9.10. 10GB each.  Grub can hold pages of choices.
Have Fun!

---

### Post by SuperEngineer on 2009-11-15
Hi, Ridgeland - Thanks for quick reply.  Been offline for a while (and sweating)... spent the day re-sizing, moving & imaging (damn slo-as-hell Partition Mngr imaging - time to switch to Partimg methinks!).  All survived ok...  XP & Jaunty now down to half their original sizes (40 & 80 Gb respectively - -  105Gb  now spare waiting to partition & format.  sdb deliberately destroyed and fresh partition images & rsync done all ok.  (oh for a 3rd bakup of bakujp disk!!!)

All of the re-partioning done with gparted - glad i'm not the only one in love with it - imaging however - YUK to partition mngr - would you recommend PartImg or something similar instead?

Anyway... now back to the real prob - getting 9.10 installed! .....

---

### Post by SuperEngineer on 2009-11-15
[duplicate posting deleted by SuperEngineeer]

---

### Post by ridgeland on 2009-11-15
Don't know about PartImg.
I used something like that or partition-image or such until someone said to just use "cp -a".  The partition-image software cloned a 10GB partition to 10GB even if it was half empty.
To backup a Linux OS partition I use something like:
$ sudo cp -a /mnt/sda6/* /Data/Backup/date_sda6/
If a 10GB partition is half full then the copy is only 5GB.  Never use cp -a to backup the current root/OS.  That is never do the above while booted into /dev/sda6, boot into sda5 first.

To clone a partition I use "gksudo nautilus" to delete everything in the target partition (like say /dev/sda7/*)
Then from /dev/sda5 I use
$ sudo cp -a /mnt/sda6/* /mnt/sda7/
Then sudo gedit /mnt/sda7/etc/fstab and if grub1 edit /mnt/sda7/boot/grub/menu.lst else if grub2 edit /somewhere/boot/grub/grub.cfg.  You cannot use the "cp -a" to copy the active OS.  That is boot up /dev/sda5 to use cp -a to copy /dev/sda6, don't copy /dev/sda5 while running /dev/sda5.  This is how I keep a safe fast bootable backup.  Now I'm learning Ubuntu 9.10.  I have it on /dev/sda9 with a bootable clone on /dev/sda10.  If I install a package that dorks /dev/sda9, I just switch to the other and catch back up.  From the previous post you see both are about the same size, thats why.  I think of Linux as a bunch of files not a partition when backing up or cloning.

---

### Post by SuperEngineer on 2009-11-21
Thanks Ridgeland.  That's what I call seriously useful info.  Thanks again [and, yet again - sorry for slow reply, the weekdays are a bit "stupid" on my current contract!; whoopee... it's weekend again :)

---

### Post by SuperEngineer on 2009-12-05
[SOLVED?] installed Linux Mint 8 which took GRUB to 1.97 (beta4)... don't like Lnx Mint but so what.  Then was able to install Karmic (from same CD as b4) without any prob. BUT... Grub was still the Mint version and now not showing either Jaunty or Karmic!  Restarted Mint in Safe mode and used Grub Rescue to relocate both successfully.
Now booted to 9.10 BUT STILL FOUND SAME KARMIC PROB AS MANY OTHERS HAVE FOUND... LOSS OF USE OF USB WIRELESS MODEM.  Plugged in mobile broadband dongle and, although Karmic doesn't seem to like it (7 re-starts b4 it was recognised!) spent hours letting Update Manager do it's stuff.  This updated GRUB again & allowed me to choose sda0 or sda1 for location.  sda0 chosen and now back to a proper Grub boot choice (Karmic / Jaunty / Mint / XP).
What a hassle just to work around Karmic install probs!!!
Now... anyone got an idea as to how to get USB wireless modem to connect to the network that Jaunty has no problem with????

---

