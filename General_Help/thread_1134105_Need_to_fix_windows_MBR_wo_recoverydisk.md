---
title: "Need to fix windows MBR w/o recoverydisk"
date: 2009-04-23
forum: General Help
---

### Post by losthawken on 2009-04-23
So here's the deal,

I was screwing around at work and decided to install Ubuntu on a personal portable drive.  To do so I popped the install disk in my work PC (running XP) rebooted and installed to a new partition on the portable drive.  

It worked great!  The only problem is that the MBR on the desktop seems to have been replaced by GRUB which is only on the portable.  Now I can't boot up windows w/o the protable drive connected.  But I can boot everything with the drive connected.

I don't have a recovery CD because this is a work computer managed by the IT dept; who due to another incident aren't super pleased with me, and I don't really want to go back there...

I've looked into SUPER GRUB, but I'm not confident that it will do what I need (or that I will be able to get it to do what I need) and I don't want to muck around and mess more stuff up.

To sum up, I need a hand repairing the windows boot manager so that windows will boot normally w/o my ubuntu portable drive connected.  Any suggestions?

---

### Post by kanikilu on 2009-04-23
Without a Windows disc, I don't think you can easily restore the MBR, however, there are alternative boot managers you could use. For example:

[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

---

### Post by oldos2er on 2009-04-23
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ajgreeny on 2009-04-23
RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

### Post by coffeecat on 2009-04-23
There's a whole load of ways of restoring the Windows MBR in this link:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Some won't be suitable for you, but sixth down - Replace GRUB in MBR with ms-sys - looks to be worth a try since you can do it from within Ubuntu, even from a live CD.

---

### Post by losthawken on 2009-04-23
> **ajgreeny said:**
> RESTORE WINDOWS MBR FROM UBUNTU LIVE CD

You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

Yeah, I'm still having trouble.  I tried apt-get lilo from my Ubuntu OS on the portable drive.  It started to load, but seemed to hang at 0% while connecting to the archive.

I then booted from the CD and got:

ubuntu@ubuntu:~$ apt-get install lilo
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ 

I'm a newb here.  I apperently know just enough to be dangerous...

As to other suggestions, thanks, but ms-sys is not available for Ububtu 8.0.4

---

### Post by regor210 on 2009-04-23
When you set the Bios to boot from your &#65279;personal portable drive did you make sure the computers hard drive is still boot-able?

---

### Post by losthawken on 2009-04-23
> **regor210 said:**
> When you set the Bios to boot from your &#65279;personal portable drive did you make sure the computers hard drive is still boot-able?

I didn't do anything to change the bios boot.  It should still boot from the Windows drive if there are no other boot disks available right?  I'm not sure why the windows MBR would be eliminated on a different drive from what GRUB was going into.

---

### Post by regor210 on 2009-04-23
yes your right. If you did not change the Bios then the Bios is not the issue.

Can you burn a CD?

---

### Post by clancymf on 2009-04-23
> **losthawken said:**
> Yeah, I'm still having trouble.  I tried apt-get lilo from my Ubuntu OS on the portable drive.  It started to load, but seemed to hang at 0% while connecting to the archive.

I then booted from the CD and got:

ubuntu@ubuntu:~$ apt-get install lilo
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ 

I'm a newb here.  I apperently know just enough to be dangerous...

As to other suggestions, thanks, but ms-sys is not available for Ububtu 8.0.4

It doesnt look like you put sudo infront of apt-get like instructed.

---

### Post by regor210 on 2009-04-23
Here's the deal Grub installs to your computers hard-drive but Grub its self is in your Ubuntu boot folder. So when you start your computer the hard-drive is seeking the Grub program that is in Ubuntu on your potable drive.

---

### Post by clancymf on 2009-04-23
Try the link the other poster posted:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

mbrfix.exe looks like it may help.

---

### Post by losthawken on 2009-04-23
> **regor210 said:**
> yes your right. If you did not change the Bios then the Bios is not the issue.

Can you burn a CD?

Yes, I can boot any OS Ubuntu or XP with full functionality (as far as I can tell).  U have something in mind?

---

### Post by coffeecat on 2009-04-23
> **clancymf said:**
> Try the link the other poster posted:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

mbrfix.exe looks like it may help.

[FONT=Bitstream Vera Sans Mono]It takes a bit of finding. A link to a link to a link and so on, but it eventually leads to

[http://packages.debian.org/etch/i386/ms-sys/download](http://packages.debian.org/etch/i386/ms-sys/download)

**losthawken**, download the deb file onto your desktop. Double-click to install. If it complains of unmet dependencies, install them through Synaptic first. 
[/FONT]

---

### Post by losthawken on 2009-04-23
SOLVED

Thanks all, I never expected so much help so fast.

The final solve:  MBRFix

[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Seems to have taken care of the problem.  

You all ROCK!

~Justin

---

### Post by losthawken on 2009-04-23
Hey all,

Now that the Windows machine is fixed I'd like to get Ubuntu working the way I would like.

I thought that by just installing Ubuntu onto the portable HD and setting the boot order to check the USB for an OS first that I could load Ubuntu instead of Windows by just plugging in the Ex-HD and restarting.  

Now it seems a little more complicated, esp since I already have Ubuntu installed onto the Ex-HD.  I tried restarting with the Ex-HD plugged in and it just loaded Windows instead.  

How can I get Ubuntu to load now?

---

### Post by coffeecat on 2009-04-23
Your problem is that stage 1 of Grub (only a little over 400 bytes long) replaces the Windows MBR on the master drive. Stage 1 calls stage 1.5 which is on an otherwise unused small area just after the partition table, also on the master drive. Stage 1.5 calls Grub stage 2 which, with menu.lst, is in /boot/grub of your Linux partition (in your case the portable HD). Which is why Windows wouldn't load when you removed the portable HD - your needed the bits of grub that were in your Linux partition.

Two options that I can think of:

Brave souls have edited the Windows bootloader (somewhere in C:\Windows) and successfully got Linux booting that way. I wouldn't know where to find a link.

Or - 

Consider installing Ubuntu with [Wubi]("https://help.ubuntu.com/community/Wubi"). Which, of course, means a fresh install.

**Edit**, I should think it might be possible to install grub stages 1 and 1.5 to that portable drive, and set the BIOS in the computer to boot from that first if plugged in. But your IT guys may not like you delving into the BIOS.

---

### Post by ajgreeny on 2009-04-23
What you need to do is install grub itself to the external drive, not the MBR.  I am not sure if you can do that with the live CD, but you certainly can with the Alternate install CD.  Having done that you just set the machine to boot first from the external drive and second from the internal hare drive.  If the external is attached grub will appear and allow you to choose ubuntu or windows, if it is not attached the windows boot will occur normally, without grub appearing.

It may even be possible to install grub to the external disk in other ways from the running ubuntu, but I am not sure how.

---

### Post by coffeecat on 2009-04-23
> **ajgreeny said:**
> What you need to do is install grub itself to the external drive, not the MBR.  I am not sure if you can do that with the live CD, but you certainly can with the Alternate install CD.  Having done that you just set the machine to boot first from the external drive and second from the internal hare drive.  If the external is attached grub will appear and allow you to choose ubuntu or windows, if it is not attached the windows boot will occur normally, without grub appearing.

It may even be possible to install grub to the external disk in other ways from the running ubuntu, but I am not sure how.

I'm just brainstorming here, but I believe you could do it with the live CD. Let's say that the Ubuntu root partition is number 1 on the portable drive. (That would have to be confirmed). And let's say that after booting up a live CD and mounting the external drive, this appears as sdb to the live cd. Which would be (hd1) in grub-speak and the Ubuntu root partition would be (hd1,0).

What I would do is to open a terminal in the live session and:

```
$ sudo grub
> root (hd1,0)
> setup (hd1)
> quit
$ exit
```

(Where $ = bash prompt. > = grub prompt.)

That would install stage 1 to the mbr of the external drive, **not** the mbr of the internal drive.

"But wait," I hear everyone chorus. "When booting up from the external drive, that becomes sda/hd(0)" Yes, I know, but I've done something similar before, and it worked. The very worst thing that could happen is that nothing would happen. All the above has done is to write stages 1 and 1.5 to the external drive, to sectors that are not otherwise in use at the moment.

**losthawken**, that's only an illustration. If you want to try it, you'll need to check which partition the Ubuntu root partition is.

---

### Post by losthawken on 2009-04-24
> **coffeecat said:**
> I'm just brainstorming here, but I believe you could do it with the live CD. Let's say that the Ubuntu root partition is number 1 on the portable drive. (That would have to be confirmed). And let's say that after booting up a live CD and mounting the external drive, this appears as sdb to the live cd. Which would be (hd1) in grub-speak and the Ubuntu root partition would be (hd1,0).

What I would do is to open a terminal in the live session and:

```
$ sudo grub
> root (hd1,0)
> setup (hd1)
> quit
$ exit
```(Where $ = bash prompt. > = grub prompt.)

That would install stage 1 to the mbr of the external drive, **not** the mbr of the internal drive.

"But wait," I hear everyone chorus. "When booting up from the external drive, that becomes sda/hd(0)" Yes, I know, but I've done something similar before, and it worked. The very worst thing that could happen is that nothing would happen. All the above has done is to write stages 1 and 1.5 to the external drive, to sectors that are not otherwise in use at the moment.

**losthawken**, that's only an illustration. If you want to try it, you'll need to check which partition the Ubuntu root partition is.

Good idea's, but this is on the edge of my linux skills.  I'm not afraid of a re-install, this is a learning exercise, I've got nothing to lose.  Questions:

Wubi - Is the windows boot manager for wubi a replacement of the original mbr or does it use the existing?  ie will I be screwing with the mbr again?  
-Also, is Wubi fully functional (aside from hibernation)?  can I modify and install all I want on it?

**coffeecat**, Your idea sounds good too, but I'm a little slow on the "how to" part.  Can you maybe help w/ a step by step?  maybe over PM?

---

### Post by coffeecat on 2009-04-24
Wubi is a different matter. What you've got is a native Ubuntu install on the external drive. With Wubi you install Ubuntu 'inside' Windows - Ubuntu lives in the C:\ubuntu folder. Wubi edits Windows' own boot manager to give you a choice of OS. See here:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you want to try my suggestion, plug in the external drive, but boot from a live CD. Once you're in the live environment, open a terminal and post the output of:

```
sudo fdisk -l
```There's quite a lot of output, so if you can get an internet connection in the live environment, you might want to copy and paste that lot into your post. In fact, we're only interested in defining which partition number your Ubuntu root partition is on (and the partition number if you have a separate boot partition), and also whether the live CD is identifying your external drive as sdb or sdc or whatever. From what you've told us, it should be sdb, but I want to be sure.

With this information I can tell you how to invoke grub from the live CD terminal and exactly what grub commands to use. It's actually fairly straightforward, but quite bewildering if you don't know your way round grub.

I learnt the hard way after I accidentally restored the Windows mbr to a hard drive that had a monoboot of Ubuntu Breezy Badger on it. :oops: And if you're wondering how on earth I could accidently restore the Windows mbr, the words 'good supper' and 'a little too much red wine' might give you a clue. :wink:

---

### Post by losthawken on 2009-04-24
Here goes:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97719771

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f3782db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       35921   288535401    b  W95 FAT32
/dev/sdb2           35922       38913    24033240    5  Extended
/dev/sdb5           35922       38783    22988983+  83  Linux
/dev/sdb6           38784       38913     1044193+  82  Linux swap / Solaris

```sda1 is the HD as far as I can tell.  the 320 GB drive is the one partitioned to include ubuntu.  SDB1 was left as an open partition so that I could still use the major part of the drive with windows, and play with ubuntu on the other ~20 GB.

---

### Post by coffeecat on 2009-04-24
Excellent - we've got all the information we need. But first a disclaimer. :wink: I'm 99.9% sure that this will not damage anything and I'm 98% sure this will work, but do this at your own risk. However, if I was in your situation I would do this. And this from a man who managed to accidently restore the Windows mbr to a machine with no Windows on it thus making Ubuntu Breezy unbootable. :lol:

OK. Boot up with the CD, but with the external drive plugged in. Open a terminal, and:

```
sudo grub
```The prompt will change to: grub>

Now:

```
root (hd1,4)
```This tells grub that the root partition #5 on the second drive. Yes, that's right. Grub counts from 0. You may not get any output at this stage.

Now:

```
setup (hd1)
```You should get some output this time, hopefully ending with a success message.

Now quit grub:

```
quit
```Now exit the terminal

```
exit
```Now restart, remove the CD and see what happens. Good luck.

---

### Post by losthawken on 2009-04-24
No dice :(

I followed the directions and got a succeeded message message in grub.  I tried to copy the output in case something went wrong, but didn't do it right.  I exited, quit, restarted and .... Windows...

I've been thinking; on the installer program on the very last window there is a button for "Advanced".  You can see it on the next to last image [here]("https://help.ubuntu.com/community/GraphicalInstall").

I seem to remember an option for Boot location under this advanced menu (which I didn't change on the original install).  Could this help us?  I started to go through the install process again to take a look at it, but it was going to make me re-partition again before I got to that stage, and I backed-out.

Also, I bumped into[ this]("https://help.ubuntu.com/community/Installation/FromUSBStick") while researching.  Is this what I should have done in the beginning?

---

### Post by losthawken on 2009-04-24
> **losthawken said:**
>   Also, I bumped into[ this]("https://help.ubuntu.com/community/Installation/FromUSBStick") while researching.  Is this what I should have done in the beginning?

In reply to myself... what about the "Make your USB stick bootable with SYSLINUX" under the Manual Approach section.  Could this be used to make the disk bootable, and put ldlinux.sys into the root of the existing install?

---

### Post by coffeecat on 2009-04-24
You may be right, that SysLinux is the answer. I'm sorry the earlier didn't work. My 2% doubt was because sdb becomes sda, so to speak, and that's clearly why it didn't work.

I'm afraid the 'Advanced' tab in the installer won't help here. That's for installing grub stage 1 to anywhere but the mbr of a drive - useful if you use 'chainloader' in a multiboot to go from one grub menu of one distro to another.

I need to have a think. I'll read that SysLinux link when I'm a little fresher, and try to get back to you.

---

### Post by rplantz on 2009-04-24
> **losthawken said:**
> No dice :(

I've been thinking; on the installer program on the very last window there is a button for "Advanced".  You can see it on the next to last image [here]("https://help.ubuntu.com/community/GraphicalInstall").

I seem to remember an option for Boot location under this advanced menu (which I didn't change on the original install).  Could this help us?  I started to go through the install process again to take a look at it, but it was going to make me re-partition again before I got to that stage, and I backed-out.



I ran into similar problems installing Ubuntu on a Vista machine that did not come with an installation disk. It has a "hidden" partition for reinitializing Vista, but it became unavailable when grub took over the MBR.

Although I don't recall the details, you are right that the key to solving my problem was in the "Advanced" area. It allowed me to install grub in the Ubuntu partition. Then I used EasyBCD (I think only applies to Vista) to add Ubuntu to the Vista boot program.

If you search the forums with my user name, rplantz, you should find some stuff that I wrote about it.

---

### Post by coffeecat on 2009-04-24
> **rplantz said:**
> Although I don't recall the details, you are right that the key to solving my problem was in the "Advanced" area. It allowed me to install grub in the Ubuntu partition. Then I used EasyBCD (I think only applies to Vista) to add Ubuntu to the Vista boot program.

Well, there's a thought. It is possible to edit the Windows XP bootloader to boot up Linux from another partition, so long as you install grub stage 1 to the Linux partition rather than to the mbr. It's too late to use the advanced tab in the installer now, but all you have to do is use the same grub commands I gave you earlier, but substitute 'setup (hd1,4)' for setup (hd1)'. Which is more or less what the advanced tab can do.

But you have to edit the XP bootloader configuration file, and I've never done that.

---

### Post by losthawken on 2009-04-28
that makes sense, but if I didn't edit the xp boot loader, wouldn't it just load the first bootable disk as indicated in the BIOS?  As long as that is set to look to the USB first then it should load Ubuntu I would think...

That would be ok by me, I don't need to select the system to load if I can control it by pluggin or unplugging the USB.

---

### Post by markeb on 2010-05-23
I need to give you a HUGE THANK YOU for helping me past this same exact problem I had this weekend. Lilo worked and my XP internal HDD is not booting properly.
 
You really saved me a lot of time and frustration Monday morning.
 
Mark
 
> **ajgreeny said:**
> RESTORE WINDOWS MBR FROM UBUNTU LIVE CD
 
You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Then you should be able to boot directly into Windows again if all goes well. Let me know how it goes or if you run into problems.

---

