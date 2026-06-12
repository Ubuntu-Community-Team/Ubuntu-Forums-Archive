---
title: "Do I need to make a new partition to install F8?"
date: 2007-11-13
forum: Fedora/RedHat and derivatives
---

### Post by toecutter on 2007-11-13
This might be (quite) a noob question, but I'm downloading the new Fedora to give it a try on the live CD (I want to try out different distro's), and I'm wondering if I'll need to make a new partition for this or any other different distro's I want to try? 

I'm assuming that a new install like this won't talk to anything I've got loaded in Ubuntu 7.04 like k9copy and Azureus, is this correct?

Again, sorry if this is really basic stuff or belongs in a different forum :)

---

### Post by RebounD11 on 2007-11-13
I'm amazed noone answered, I'll try to and I hope that someone will correct me if I am mistaking.

If U want to try the LiveCD you don't need any partitions (you don't need a hard drive for that matter :D), if U want to install it along side Ubuntu (or any other OS) U need to have some free space on your disk from which to create the necessary partitions for a Fedora install, without messing with the data on the Ubuntu partitions. I don't think you have to do anything special, as both Ubuntu and Fedora can use the same swap partition and you can add mount points for the Ubuntu partitions during the installation if you want to, and if you have grub installed already I think you can configure that during the installation.

I never tried dual-booting 2 Linux OS, but this seems the logical way to do it. When I installed Ubuntu on a computer that had Fedora, it set mount points for the Fedora partitions by itself and I only had to create teh partitions Ubuntu needed to install (only / partition in that case), the thing is I erased those partitions because I wanted to replace Fedora with Ubuntu back then.

---

### Post by igknighted on 2007-11-13
> **RebounD11 said:**
> I'm amazed noone answered, I'll try to and I hope that someone will correct me if I am mistaking.

If U want to try the LiveCD you don't need any partitions (you don't need a hard drive for that matter :D), if U want to install it along side Ubuntu (or any other OS) U need to have some free space on your disk from which to create the necessary partitions for a Fedora install, without messing with the data on the Ubuntu partitions. I don't think you have to do anything special, as both Ubuntu and Fedora can use the same swap partition and you can add mount points for the Ubuntu partitions during the installation if you want to, and if you have grub installed already I think you can configure that during the installation.

I never tried dual-booting 2 Linux OS, but this seems the logical way to do it. When I installed Ubuntu on a computer that had Fedora, it set mount points for the Fedora partitions by itself and I only had to create teh partitions Ubuntu needed to install (only / partition in that case), the thing is I erased those partitions because I wanted to replace Fedora with Ubuntu back then.

In a word, yes.  You need separate partitions, otherwise it will overwrite the Ubuntu install you already have.  Also, it will not be able to use applications installed on the other install.  However, you will be able to see the files on the other partition, so you wont have to keep multiple copies of documents or reboot to access other files or anything like that.

Also, when you install the second OS, it will ask you if you want to install a bootloader.  Now, you already have one (grub), so you could select 'no' and manually configure Ubuntu's grub loader with the details of Fedora's install.  This will be a huge PITA though, because Fedora upgrades the kernel all the time, and every time you upgrade you would need to modify your menu.lst manually to compensate (Fedora 8 is now 5 days old and already there has been a kernel upgrade).  You could also install the Fedora bootloader (also grub) to the MBR (this is the default), which would over-write ubuntu's.  Fedora's is prettier, and it might recognize the Ubuntu partition and set up the bootloader entry for you... or it might not.  If it doesn't, you would need to add Ubuntu to fedora's menu.lst manually.  Also, while ubuntu does kernel upgrade far less frequently, they do happen.  And if/when they do, you would need to edit the menu.lst manually again in fedora to point to the new Ubuntu kernel.

There is a third way.  You can tell Fedora to install the grub bootloader to the partition, instead of the MBR (master boot record).  In this case, fedora and Ubuntu would each manage their own booting.  Since Ubuntu's grub would be on the MBR, you would first get to ubuntu's grub upon boot.  Now in Ubuntu's menu.lst file you would need to add a chainloader entry (the same entry you would use to point to a windows install, actually, in a dual boot situation), which acts as a handoff of sorts.  Should you select the fedora/chainloader entry, it would continue on to boot into fedora's grub menu, from which the proper kernel would be set up automatically.  This method will be the easiest in the long term, and while it sounds complicated, its actually not too bad.  If you decide to go this route, post some more details about your hard disk partition setup and we can help you get it all up and running.

Oh, one more thing.  Fedora and Ubuntu can share the same swap and /home partitions (if you do a separate /home that is), so theres no need to create duplicates of those.

---

### Post by toecutter on 2007-11-13
OK cool, thanks :)

the third option you explain sounds like the way to go - I plan to use Ubuntu as my main desktop and after reading what you typed a couple of times I understand it a bit. I'd just need to know where to put the info for Fedora, or do I understand it right that the boot info for Fedora would be stored on the partition where Fedora is installed?

currently my partitions are set up something like this:

5gb - XP
30gb - XP games
200g - home 
15gb - Ubuntu
4gb - swap

How much space should I make available for Fedora?

---

### Post by igknighted on 2007-11-13
> **toecutter said:**
> OK cool, thanks :)

the third option you explain sounds like the way to go - I plan to use Ubuntu as my main desktop and after reading what you typed a couple of times I understand it a bit. I'd just need to know where to put the info for Fedora, or do I understand it right that the boot info for Fedora would be stored on the partition where Fedora is installed?

currently my partitions are set up something like this:

5gb - XP
30gb - XP games
200g - home 
15gb - Ubuntu
4gb - swap

How much space should I make available for Fedora?

Given that you already have a /home, I would suggest about 7-10 gb.  Also, do not choose the same username for both distros, you could run into all sorts of problems.

I wish I had a screenshot of the installer at the point where you tell it where to put grub, but I don't.  If anyone else knows where screenshots of the installer are, could you post them?

Anyhow, you are indeed correct in your idea of how it works.  The file you need to edit is Ubuntu's /boot/grub/menu.lst file (need to use sudo to have rights to edit it).  You will add a section that looks like this: ```
title Fedora 8
	rootnoverify (hd#,$)
	chainloader +1
```

# is the number of the hard drive that Fedora is installed on.  Grub starts counting at 0, not 1, so the first hard drive (and only hard drive in a one disk setup) is drive 0.

$ is the partition # on that drive.  Generally it is the number in the block device minus one (because grub starts counting at 0), so if the block device name of the partition is /dev/sda7, on the only disk, the rootnoverify line would end with (hd0,6).

You can look up the block device name with the command 'sudo fdisk -l' (thats a lower-case L, as in list), which will detail all the info about the partitions on your system.

---

### Post by toecutter on 2007-11-14
That's excellent, thanks very much for the detailed info! :) 

Not sure when I can get around to trying it, but I'll post here if I have problems

---

### Post by BLTicklemonster on 2007-12-30
Excellent. I'm using fedora 8 live cd right now. It's - well, it's just like ubuntu for all I can tell, but what the heck, I haven't looked around any yet. mp3s seem to be playing right off the bat, I like that.

Thanks for all the info igknighted.

---

### Post by BLTicklemonster on 2008-01-01
Wow, what a wake up call.

Fedora's installer isn't anywhere near as straight forward and simple as Ubuntu's.

In Ubuntu, I can find where I need to resize a partition and just do it. In Fedora, I was guessing along, and came to pretty much the right place (hda,5 which is hd0,4 was shown as sda,5 which threw me for a minute there) and I chose the size I wanted (12000 mb out of an available 80000), but it kept saying that there wasn't enough room.

Okay, right there, if I can't do that, I back off and leave it alone. God knows if it starts bugging me there, I'll end up totally messing something up.

I like it, playing around from the live CD, it appears really nice, but seeing that the commands are all different, and the programs it uses are all different, I think I'll just stick to Debian based distros.

---

### Post by igknighted on 2008-01-03
> **BLTicklemonster said:**
> Wow, what a wake up call.

Fedora's installer isn't anywhere near as straight forward and simple as Ubuntu's.

In Ubuntu, I can find where I need to resize a partition and just do it. In Fedora, I was guessing along, and came to pretty much the right place (hda,5 which is hd0,4 was shown as sda,5 which threw me for a minute there) and I chose the size I wanted (12000 mb out of an available 80000), but it kept saying that there wasn't enough room.

Okay, right there, if I can't do that, I back off and leave it alone. God knows if it starts bugging me there, I'll end up totally messing something up.

I like it, playing around from the live CD, it appears really nice, but seeing that the commands are all different, and the programs it uses are all different, I think I'll just stick to Debian based distros.

Resizing isn't an option on the installer yet.  I believe it may be on the spec sheet for fedora 9, but I think fedora 10 is more realistic.  Many distros are like this... if you want to keep trying them you should keep a gparted CD around for any partition manipulation.

---

### Post by whitefang5412 on 2008-02-05
No partitions needed for installing fedora unless you don't want to lose your other partition with another OS on it. Then you need to partition. If you want to run the live disk no partitioning is needed. It makes all the decisions off of the live disk.

---

