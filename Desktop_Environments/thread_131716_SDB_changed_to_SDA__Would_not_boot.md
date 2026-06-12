---
title: "SDB changed to SDA?  Would not boot"
date: 2006-02-17
forum: Desktop Environments
---

### Post by garren on 2006-02-17
I am putting this post up for two reasons: I'm hoping for an explanation of what happened, and I'm trying to help others that get this problem.  

I got Breezy working on a partition on an external hard drive, with grub on the hard drive, not on my computer's internal hard drive (the hard drive partition was called "SDB1" when I installed it).  It worked for about a week and then it stopped booting all of a sudden.  I thought my file system was corrupted, judging from the symptoms after searching the forums (fora?  are we in Greece?).  

After several hours of trying to fix the file system, trying to update the kernel, and reloading the grub--all unsuccessfully--,using a terminal in the Live CD I ran "fdisk" using the command "fdisk -l" which lists all the drives it sees, and their paths, etc.  It said the path to the partition I was looking for was SDA1.  SDA?  Who is that?  SDA is a stranger in these parts because my hard drive has been SDB this whole time.  When did that drive become SDA?  So now I need to go into my /boot/grub/menu.lst to change all of the SDB's to SDA's.  I haven't done it yet, but I assume it will work because I removed the live CD, brought up grub, trying to boot, pressed 'e' to edit the command line, and switched 'SDB1' to 'SDA1' afterwhich it booted, and here I am all logged in right now.  

I have no idea why my hard drive changed.  But it did, and I really had no idea what was going on.  Hope this helps others who run into the same problem.

---

### Post by dcstar on 2006-02-17
[QUOTE=garren]I am putting this post up for two reasons: I'm hoping for an explanation of what happened, and I'm trying to help others that get this problem.  

I got Breezy working on a partition on an external hard drive, with grub on the hard drive, not on my computer's internal hard drive (the hard drive partition was called "SDB1" when I installed it).  It worked for about a week and then it stopped booting all of a sudden.  I thought my file system was corrupted, judging from the symptoms after searching the forums (fora?  are we in Greece?).  

After several hours of trying to fix the file system, trying to update the kernel, and reloading the grub--all unsuccessfully--,using a terminal in the Live CD I ran "fdisk" using the command "fdisk -l" which lists all the drives it sees, and their paths, etc.  It said the path to the partition I was looking for was SDA1.  SDA?  Who is that?  SDA is a stranger in these parts because my hard drive has been SDB this whole time.  When did that drive become SDA?  So now I need to go into my /boot/grub/menu.lst to change all of the SDB's to SDA's.  I haven't done it yet, but I assume it will work because I removed the live CD, brought up grub, trying to boot, pressed 'e' to edit the command line, and switched 'SDB1' to 'SDA1' afterwhich it booted, and here I am all logged in right now.  

I have no idea why my hard drive changed.  But it did, and I really had no idea what was going on.  Hope this helps others who run into the same problem.[/QUOTE]
Firstly, I'm surprised it booted, I was under the impression Ubuntu "hard coded" the drive designation into the boot loader - but if it worked, good.

Secondly, has your internal drive failed?, that is the only thing I can think of that would suddenly change your external drive to be the first detected by Ubuntu.

---

### Post by garren on 2006-02-17
> has your internal drive failed?, that is the only thing I can think of that would suddenly change your external drive to be the first detected by Ubuntu.

Phew, I'm glad to say my internal drive is fine--That is what I am using at this particular moment.  Internal drive is HDA though, never was SDA.  (although perhaps you're saying the 'a' just attaches to the first recognized drive, whether its 'HD' or 'SD', and the 'b' attaches to the second drive, no matter the 'SD' or 'HD', and so on?)  

I think I may have figured out why my drive changed to SDA, but it then it leaves unexplained why Ubuntu stopped working for me.  I had forgotten that I changed /boot/grub/device.map to make my USB drive (0,0) and my internal drive (1,0) since I was under the impression that it was that way from Ubuntu's perspective since Grub was on the USB drive.  

It doesn't solve the question as to why Ubuntu stopped working in the first place because that change was one of the first things I tried to fix Ubuntu *after* it stopped working.  

In that case maybe one of those other things I tried--reinstalling grub, etc--did fix the problem.

---

### Post by dcstar on 2006-02-17
[QUOTE=garren]Phew, I'm glad to say my internal drive is fine--That is what I am using at this particular moment.  Internal drive is HDA though, never was SDA.  (although perhaps you're saying the 'a' just attaches to the first recognized drive, whether its 'HD' or 'SD', and the 'b' attaches to the second drive, no matter the 'SD' or 'HD', and so on?)  

I think I may have figured out why my drive changed to SDA, but it then it leaves unexplained why Ubuntu stopped working for me.  I had forgotten that I changed /boot/grub/device.map to make my USB drive (0,0) and my internal drive (1,0) since I was under the impression that it was that way from Ubuntu's perspective since Grub was on the USB drive.  

It doesn't solve the question as to why Ubuntu stopped working in the first place because that change was one of the first things I tried to fix Ubuntu *after* it stopped working.  

In that case maybe one of those other things I tried--reinstalling grub, etc--did fix the problem.[/QUOTE]
Ok, that all makes sense.

BTW, Ubuntu assigns the first IDE Master device it detects as hda, the Slave on that IDE channel is hdb (if it exists). The second IDE Master device is hdc, and the Slave hdd.

The key word there is "detects", I believe that if you just used the Secondary IDE channel (and there was nothing on the first) then Ubuntu would still start off with hda etc, and if you later put other devices into the Primary channel these Secondary ones would suddenly become hdc etc!

The same process may have happened with your sda/sdb hardware.

---

