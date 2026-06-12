---
title: "Installed dual-boot, now WinXP won't boot"
date: 2006-08-30
forum: Desktop Environments
---

### Post by markcholden on 2006-08-30
Hi all,

After using Windows all my life, I decided to give Ubuntu a try. Downloaded the ISO, burned, partitioned, installed with the default options, and everything seemed to be working fine. Then after a few boots of Windows XP I noticed that it was performing very, very sluggishly, and finally today I tried to boot into Windows and it failed. It went straight to a black screen - no Windows logo or anything. Ubuntu works fine, but Windows won't boot! Help!

Thanks!

---

### Post by Emerzen on 2006-08-30
Try this: boot your computer into Windows.  As soon as you select Windows from the GRUB boot screen, start tapping the F8 key.  This should bring you to a new menu that asks if you want to boot into recovery mode, choose yes w/ networking.  Lemme know if that works.

---

### Post by markcholden on 2006-08-30
It worked! Thank you! I'm posting this from WinXP in safe mode. Now how do I fix it so I can boot normally? Thanks!

---

### Post by markcholden on 2006-08-30
*bump*

---

### Post by ianthepetrock on 2006-08-30
You could go into your drive manager and remove the ubuntu partitions from the Harddrive in windows, then reinstall ubuntu if you wanted. You might have to also fixmbr.

---

### Post by markcholden on 2006-08-31
Ok, this is weird...I tried booting into safe mode a few times and had the same problem as I had before with booting into normal mode.  It wouldn't boot. Then I went to boot Windows again and it booted normally. I'm in Windows XP right now, normal mode not safe mode, and aside from my theme having vanished, everything seems to be working fine. I'm really, really confused by Windows' behavior...does anybody know what's going on?

---

### Post by Emerzen on 2006-08-31
sorry for the delay but I'm at work.  When Ubuntu is installed, it does nothing to your Windows partition (unless you chose to resize it).  Grub simply chainloads the normal windows bootloader, ntldr.  So, if you can boot XP by any method, there's something wrong w/ your XP side if it fails after that.  That's why I asked about safe mode booting.

Could you give me a little more info about your PC?  What type of PC?  CPU?  How many and what type of harddisks?  How many partitions and where is Ubuntu and XP?  Did you perform any tweaks to XP after it was installed...particularly, did you change the pagefile size or where it resides?

---

### Post by markcholden on 2006-08-31
My computer is a Dell Inspiron 9300, 1.6 GHz Intel, 1 gig RAM, one internal HDD of ~95 gigs.

HDD Partitions:
Three that came with the computer -- a ~50 megabyte FAT16 partition, a ~90 gig NTFS partition for WinXP, and a ~5 gig recovery partition.
Two added -- resized the NTFS and added a Linux Ext3 and swap, combined space usage ~7 gigs.

I did the partitioning in Windows with PartitionMagic. Dunno if that affects anything.

I defragged the hard drive before installing Ubuntu.

I did not touch the settings for the page file. It's system managed.

Hope this helps.

---

### Post by Emerzen on 2006-08-31
Few thoughts:

1.  You have 5 partitions on the disk, which means you must have logical volumes as you can only have 4 primary partitions on a disk.  What this means is: logical volumes in my experience are great but have a tendency to get messed up in XP if you do a lot of resizing or changing of the partitions.  What you can do...the 5 gig recovery partition-> it contains a norton ghost image of your original system as shipped from Dell (I have had multiple dells).  However, once you overwrite your MBR (which you did when you installed GRUB) that partition is forever inacessible.  Dell uses a special bootloader (you hit CTRL+F11 when the computer boots and you see a blue bar on the top of the screen with the words Dell on it to access that partition) which is now gone.  I lost mine after reinstalling XP once.  I contacted Dell and there's no way to get it back w/o shipping your drive back to Dell.  My solution -> fire up Qparted and delete that partition.  Then add those 5 gigs to either XP or Ext 3 partition bringing total number to 4, which you can have XP manage as primary partitions.  This may help.  For more info on that partition go to Dell and look up "PC Restore."

2.  Other simple steps.  Fire up XP and defrag it's partition at least 2x.  Then, right click "My Computer" and select properties.  Click the Advanced tab and performance options.  Change the paging file from system managed to a set size, 2048-4096 is more than you'll need w/ a 1gig of RAM.  

3.  If the problem persists you can try a System Restore under Programs->Accessories->System Tools.

4.  It just occurred to me but it could be malware?  Do you do any filesharing or otherwise have security vulnerabilities?  Run some online bug checkers or if you d/l UBCD4Win and run a virus check from this bootable CD (follow instructions on site for creating it).

**5.  You can boot your computer from your Windows CD and choose to go into the recovery console.  (It will ask for Admin password, just hit enter unless you specifically set one).  Once at C prompt you can enter a "fixboot" command.  This will reinstall your boot files.  I don't remember but it may also reinstall your MBR, which means you'll have to reinstall GRUB after.  Browse MS site and search for "fixboot" to get more details, and follow [this thread]("http://www.ubuntuforums.org/showthread.php?t=224351") to reinstall GRUB.**

6.  If all else fails you can reinstall XP if it's feasible.  If you've never done this it may sound intimidating, but Dell makes it very easy.  The process is -> go to Dell's site and under drivers & d/l enter your Service Tag -> it will then list all the drivers for your computer which you can d/l and burn to a disk or flashdrive -> reinstall XP -> reinstall your drivers.  I can give you more details if you should want to try this.  I do this ever 3 months on my XP side as it's the only way to truly clean out the cobwebs.

7.  Finally, you can search the MS forums for similar issues, as their are people over there much more knowledgeable than I about Windows.

---

### Post by The Pinny Parlour on 2006-08-31
Sorry to thread hijack but it's kind of similar what I would like to ask.
I have a PC with windows XP, no partitions at all on the HDD.  How can I install ubuntu on it and have like a choice at boot up as to which OS I would like to use.  Preferably I would like to not have to reinstall windows.
I have searched but not found much.
TIA

---

### Post by The Pinny Parlour on 2006-08-31
I worked it out.

Cheers,  :D

---

### Post by markcholden on 2006-08-31
@Pinny -- the Ubuntu installer will do that automatically for you. Just make sure you don't have more than four partitions on the hard drive!](*,) :tongue: 

@Emerzen -- thank you so much for that detailed response!

I have a few questions.

1a. You're right...the Ext3 and swap partitions are logical partitions together on an extended partition. But why would that affect Windows? Windows is still on a primary partition.

1b. Should I try to save anything on the Dell recovery partition? Burn it to DVD, maybe? Is there absolutely no way I can use anything on it now that I've modified the MBR?

1c. The Dell partition is at the end of the drive. The Linux partitions are right before it. In order to use that space I free up by removing the Dell partition, I'll have to completely reformat my Linux partitions too, won't I? In which case I'll lose all the customizations I've made and programs I've downloaded in the last few days. Is there any way I can save all that? Like, say, burn an image of the entire partition, reformat, copy the Linux image to the partition, then use the live CD to install the bootloader?

1d. I was thinking of creating a FAT32 partition for files shared between the OSes. But that would bump the total number of partitions up to 5 again. I was thinking I could delete that FAT16 partition at the very beginning of the drive. Do you know what's in it? Do I need it? (It's labeled "DellTools" or some such.)

2. I'm still defragging and haven't rebooted yet, but just curious, why would defragging and setting the page file size fix the problem?

4. I doubt it's malware. I don't do any file sharing and have always been pretty paranoid about that, scanning the computer regularly, running multiple defense programs, etc.. I'll double-check, though.

5. Yeah....I already thought to try that. Unfortunately, my admin password is lost, and it's not blank. :(

Thanks!

---

### Post by Emerzen on 2006-08-31
1a.  Technically, XP shouldn't have a problem w/ this.  I'm not sure why in my experience it's resulted in problems (if the partitions are there when XP is installed, it's not a problem).  
1b.  When I ran into this, the only solution I found was a complicated hack which required hacking the MBR.  I'm sorry but I don't remember the link where I found this.  I googled something like "dell 'PC Restore' mbr" and found it.  I tried to get Dell to help me fix this, and the only solution they offerred was to have me ship my harddrive to them.  Since then, I've gotten comfortable reinstalling XP, so I didn't really need it.

1c.  No, I don't think so.  If you delete that partition, I'm pretty sure either Qparted, or Partition Magic can then resize the ext3 or NTFS partitions w/o a format.

1d.  The Fat16 partition contains some system utilities from Dell.  Actually useful tools like a hard monitor tools and such.  You can boot to that by hitting F12 while the computer POSTs.  Select the option to boot to the utility parition.  However, if you have the system utlities CD that Dell sometimes ships w/ their PCs, you've got the same tools on that CD (it's a bootable CD).  If you don't have it, you can request it from Dell.  I got rid of my utility partition too.  If you do that, you can use the 5gig for a Fat32 shared partition.  Another option for sharing is to install [this program]("http://www.fs-driver.org/index.html") in XP, which will allow you to read/write from Windows to Ext3.  You can already read NTFS from Ubuntu, so the only thing you can't do is write to NTFS from Ubuntu (there's actually a beta program NTFS-3g that you can install, which is supposed to be pretty stable now).

2.  It's difficult to know where in the XP boot process things are going wrong.  Basically, NTLDR loads the XP kernel and starts system services.  The page file and volume mounting occurs early, so it's somewhat likely that's what the problem is.  However, again, I'm no XP expert so I'd search the MS forums for better advice.

5.  I think you can create a new account w/ administrator priveleges (as long as your usual account has these priveleges).  You can then log on as this person and do the fixboot thing.  It's been awhile but I'm pretty sure any account w/ admin priveleges can log on from the recovery console.  

Hope it's working for you.

---

### Post by Emerzen on 2006-08-31
> **The Pinny Parlour said:**
> I worked it out.

Cheers,  :D

Glad I could help=).  Seriously, that's great.

---

### Post by markcholden on 2006-09-01
Ok, it's working fine now. The defragging and setting of the page file seems to have fixed it. Thanks Emerzen!

---

### Post by bearcat on 2006-09-01
markcholden, it's up to you if you want to do things differently, but for what it's worth, when it comes to file sharing between Windows and Linux, when I have a file I need to access from both operating systems I normally just leave it on the Windows partition. 

It is possible to mount your Windows drive so that you can read from and write to it within Ubuntu, but it isn't possible to do vice versa (which is Windoze's fault, not Ubuntu's). Which means, in a nutshell, that Ubuntu can use files that are on the Windows drive. So you don't really need a special partition for shared files.

---

