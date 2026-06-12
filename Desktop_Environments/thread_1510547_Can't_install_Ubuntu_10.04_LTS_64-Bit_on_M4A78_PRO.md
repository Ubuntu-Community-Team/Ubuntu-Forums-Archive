---
title: "Can't install Ubuntu 10.04 LTS 64-Bit on M4A78 PRO"
date: 2010-06-15
forum: Desktop Environments
---

### Post by Denbert on 2010-06-15
Hi there,

I'm trying to install Ubuntu 10.04 LTS 64-bit desktop version on Asus M4A78 Pro - But i Can't install the OS, as installer says error when trying to create filesystem ext4

Anyone got at clue :confused:

( Debian Lenny 64-bit works fine on the board..)

---

### Post by wkulecz on 2010-06-15
Have you tried using ext3 instead of ext4?

---

### Post by Denbert on 2010-06-16
> **wkulecz said:**
> Have you tried using ext3 instead of ext4?

Yes, did tried ext3 also, no luck at all - think it's the controller driver, as the Ubuntu 10.04 is seeing my disks as RAID1 (having two 320 gb disks attached) I've tried RAID, IDE and AHCI settings in bios - Same error...

Debian Lenny installs without at glitch :confused:

---

### Post by grege on 2010-06-16
Maybe unplug one of the drives until installed? A bit of work to then manually add other and maybe move /home.

Also could try 32bit version.

---

### Post by Denbert on 2010-06-16
> **grege said:**
> Maybe unplug one of the drives until installed? A bit of work to then manually add other and maybe move /home.

Also could try 32bit version.

As I have 8 gb RAM in the machine, 32-bit version is a no-go.

I'll try the one-by-one disk on a rainy day, as I installed the Debian Lenny earlier today, as I was in a need for a working system today.

But the error is very strange and I'll investigate on it later this summer and come with feedback.

---

### Post by grege on 2010-06-16
Ubuntu will install a 32bit PAE kernel giving you the full 8gb, and no mucking about with dodgy flash kludges.

---

### Post by Denbert on 2010-06-16
> **grege said:**
> Ubuntu will install a 32bit PAE kernel giving you the full 8gb, and no mucking about with dodgy flash kludges.

Nice, I'll try it tonight ;-)

Thanks for pointing me in this direction - I'll make a feedback.

---

### Post by dino99 on 2010-06-16
yeah pae kernels give you all the 64 benefits without the isuues :p

better to prepare the partitions before installing ubuntu: boot with partedmagic to do it.

---

### Post by Denbert on 2010-06-16
> **dino99 said:**
> yeah pae kernels give you all the 64 benefits without the isuues :p

better to prepare the partitions before installing ubuntu: boot with partedmagic to do it.

OK - Then I'll setup the the partitions with partedmagic and then mount them during install! - Why not use the ubuntu installer to make the partitions?

I'm getting curious here ;)

---

### Post by grege on 2010-06-16
I only ever use the installer, you can select manual configuration if you want to something sensible like create a separate /home partition.

If you are going to use the entire drive it is a no brainer.

@dino99 - any reason for your advice? Or do you see it as a solution to the original problem?

---

### Post by Denbert on 2010-06-16
> **grege said:**
> 
If you are going to use the entire drive it is a no brainer.


THATS MY KIND OF LANGUAGE, YOU READ ME LIKE AN OPEN BOOK :lolflag:

---

### Post by Denbert on 2010-06-16
> **dino99 said:**
> yeah pae kernels give you all the 64 benefits without the isuues :p

better to prepare the partitions before installing ubuntu: boot with partedmagic to do it.

Just tried the 32-bit version wit two and one disk attached - same error..

It's crazy as Debian Lenny works great, but is VERY anoing to use as desktop machine... - why don't the kernel folks work using the simple rule: "If it works, don't fix it" ](*,)

---

### Post by grege on 2010-06-16
@Denbert

You could try running Debian Squeeze. Only thing is it might actually bring back the problem as Ubuntu is based on Squeeze/Sid/Experimental. With perseverance you can make Squeeze to be pretty much the same as Ubuntu. Main gripe I have always had with Debian is Samba shares, which I need for my media players and NAS. Debian just makes Samba an unnecessary chore.

I would try adding a new kernel to Lenny, keeping the current one of course, and see if it boots and runs. If it works add squeeze and non-free and contrib repositories, plus Debian Multimedia and do an dist-upgrade. No guarantee you won't end up with a stuffed system. Live CDs are a great way to check if things work. If you want to get serious and earn enormous street cred download a sidux live cd. Sidux uses the latest everything and runs KDE 4.4, but is very hands on. You must read the online manual first to understand how it controls network access (very important as on first boot you will not have Internet access) and handles updates. 

I have a M4N78 Pro, the one with Nvidia chips,with an Phenom X4 810 and it works flawlessly with Ubuntu, Debian and Sidux.

[http://sidux.com/index.php?module=PNphpBB2](http://sidux.com/index.php?module=PNphpBB2)

---

### Post by Denbert on 2010-06-16
> **grege said:**
> @Denbert

You could try running Debian Squeeze. Only thing is it might actually bring back the problem as Ubuntu is based on Squeeze/Sid/Experimental. With perseverance you can make Squeeze to be pretty much the same as Ubuntu. Main gripe I have always had with Debian is Samba shares, which I need for my media players and NAS. Debian just makes Samba an unnecessary chore.

I would try adding a new kernel to Lenny, keeping the current one of course, and see if it boots and runs. If it works add squeeze and non-free and contrib repositories, plus Debian Multimedia and do an dist-upgrade. No guarantee you won't end up with a stuffed system. Live CDs are a great way to check if things work. If you want to get serious and earn enormous street cred download a sidux live cd. Sidux uses the latest everything and runs KDE 4.4, but is very hands on. You must read the online manual first to understand how it controls network access (very important as on first boot you will not have Internet access) and handles updates. 

I have a M4N78 Pro, the one with Nvidia chips,with an Phenom X4 810 and it works flawlessly with Ubuntu, Debian and Sidux.

[http://sidux.com/index.php?module=PNphpBB2](http://sidux.com/index.php?module=PNphpBB2)

Hmm, I got it up and running...

I installed Ubuntu 9.10 32-Bit version and upgraded the system to 10.04 LTS...

They must have changed something in the driver from 9.10 to 10.04

---

### Post by grege on 2010-06-17
> **Denbert said:**
> Hmm, I got it up and running...

I installed Ubuntu 9.10 32-Bit version and upgraded the system to 10.04 LTS...

They must have changed something in the driver from 9.10 to 10.04

Well done. Just check you got the PAE kernel and your full 8gbs. I think it is only since 10.04 that the PAEs are installed automagically. They are in Synaptic if not already running.

cheers

---

