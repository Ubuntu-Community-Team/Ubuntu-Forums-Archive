---
title: "How to wipe xp off hd"
date: 2008-12-12
forum: General Help
---

### Post by hatewindows on 2008-12-12
Hello all--I have Xp and ubuntu 8.10 on a dual boot Hard drive--I'm done with XP--DONE!  My question is--is there a simple way to Delete XP totally from the dual boot and allocate the free space that XP was using to Ubuntu-so the entire drive is UBUNTU? Thanks for any answers.. Happy Holidays..... MARK

---

### Post by 73ckn797 on 2008-12-12
You can boot a Ubuntu live CD and use System/Administration/Partition Editor and delete the partition that Windows is on. You then can resize the Ubuntu partition. It will take a while depending upon the size of the hard disk.

---

### Post by soro2005 on 2008-12-12
If you erase the WinXP partition and allocate the free space to your Ubuntu partition, it'll screw with your grub. You'll have to reinstall grub, or at least fix the references.

Alternatively, you could just seize the opportunity to change your partitioning schema and use what's now WinXP for, say, /home. Or even as a partition dedicated to nothing else but your documents.

---

### Post by EvilRobotDrew on 2008-12-12
speaking from experience, a separate /home partition is AWESOME! It allows you to upgrade, downgrade, check out other distros, all with much less worry about destroying important data or settings. As an example, i recently installed Fedora 10 on a new partition, because i have a separate /home partition, then when i first booted into Fedora, my theme, Icons, background, everything was (almost) exactly like in Ubuntu.

---

### Post by louieb on 2008-12-12
> **soro2005 said:**
> ...as a partition dedicated to nothing else but your documents.
+1  Separate the data from the OS.

---

### Post by 73ckn797 on 2008-12-13
> **louieb said:**
> +1  Separate the data from the OS.


Ignore this reply. Found the answer.

---

### Post by PanopticChaos on 2008-12-14
I would also concur with blanking the existing XP partition, formatting it ext3, and using it as a separate documents or data partition rather than resizing the linux partition over it - I've seen enough partition resizes go poorly (though it's less an issue in modern times).  

Additionally, having your data on a separate partition helps you later on down the road if you ever bork up your Ubuntu install - if /home is on a different partition than / you can just reinstall and most of your settings will still be there

---

### Post by Kain000 on 2008-12-14
I was wondering the same thing as I am ready to get rid of my XP partition.   How would I errase my xp and make it space for /home?

---

### Post by 73ckn797 on 2008-12-14
> **Kain000 said:**
> I was wondering the same thing as I am ready to get rid of my XP partition.   How would I errase my xp and make it space for /home?


You might look here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by logos34 on 2008-12-14
> **Kain000 said:**
> I was wondering the same thing as I am ready to get rid of my XP partition.   How would I errase my xp and make it space for /home?

I would recommend moving/copying /home with the **cp -a** command (see link my signature) rather than cpio as in the psychocats link.  It's a lot simpler and it gets EVERYTHING.  I stopped suggesting the psychocats method since it seems to cause permissions problems when rebooting ([.dmrc etc]("http://ubuntuforums.org/showthread.php?t=371052&highlight=.dmrc+psychocats"))

---

### Post by hawkhock on 2008-12-20
> **PanopticChaos said:**
> I would also concur with blanking the existing XP partition, formatting it ext3, and using it as a separate documents or data partition rather than resizing the linux partition over it - I've seen enough partition resizes go poorly (though it's less an issue in modern times).  

Additionally, having your data on a separate partition helps you later on down the road if you ever bork up your Ubuntu install - if /home is on a different partition than / you can just reinstall and most of your settings will still be there

Am also ready to terminate XP.  Newbie -- Currently using Ubuntu dual boot.  I've done lots of thread reading but know I don't understand all of it.

The simplest method would be to use the 8.10 Live CD for a full install.  I may resort to that but am also trying to learn how to use Linux.  So am looking at two different scenarios to accomplish the same goal: terminate XP, Ubuntu with three (?) partitions:  /ext3, /home, /swap.  Do I also need an unallocated or free space partition?

Scenario #1:  Full install from Live CD
[LIST]
[*]Back up /home from dual boot
[*]Do I need to delete all items from Add/Remove programs in Windows before the full install?
[*]Full install from Live CD -- Does this completely erase the C drive and reinstall from scratch?  Or is anything recognized from the dual boot install?
[*]Clean install (I hope), DSL is working, updates completed.  Restart.
[*]Boot from Live CD.  Access Partition Editor. Open GParted. Add new partition?
[*]Select /ext3 as the partition type?  Do I need to size the new partition?
[*]Close GParted.  Remove Live CD.  Restart in normal mode.
[*]Move /home to the new partition using copy method from this thread
[/LIST]

Scenario #2:  Change from dual boot to full install using GParted.
After installing Ubuntu 8.10 as dual boot, disk partitions are:
/devsda1	0%
/devsda2	46% (Windows)
/ext3		53% (Ubuntu)
/free space	0%

[LIST]
[*]Do I need to delete all items from Add/Remove programs in Windows before "blanking" the Windows partition?
[*]Boot Ubuntu Live CD
[*]Open Partition Editor.  Open GParted
[*]"Blank" Windows partition -- does this 'erase' or 'delete' the partition?
[*]Does the last action leave the partitions for /devsda1 and /devsda2?
[*]Do 1 & 2 get combined or does one of them get removed?
[*]Which one (1 or 2) gets formatted as /ext3?
[*]Assuming partitions are finished, close GParted, remove Live CD.  Restart.
[*]Use copy command to move /home to the /ext3.
[/LIST]

I haven't accessed the Partition Editor on the Live CD to see how it works.  Will do that while waiting for a response.

Sr Citizen in UT

---

### Post by cb34 on 2008-12-20
didn't read the whole thread.. sorry if i'm repeating things.. but i just nuked my win partition off my dual boot drive.. so what i basically did was...

backup the $home dir.
then, making sure nothing is running in the background, run gparted, delete winxp partition, then will say unallocated space.. then just create a new partition in that space, formated as ext3 for ubuntu... 

or

insteaad of creating a new partition with that unallocated spce.. you could resize so your ubuntu install will take over the unallocated space.

just make sure you have patience, could take a very long time to resize if it moves the data around on the disk, and dont do anything else on the computer while its working to make sure nothing screws up.

done a partition resize/combining a bunch of times, no problems. just takes a long time sometimes.. hours.

you dont need to touch the windows install if you wanna just nuke the whole partition. no need to boot windowz, or go into is add/remove.. just nuke the whole partition.

also i dont know if it matters, but before you do the win nuke, make sure at the grub boot menu(assuming you're using grub) you have ubuntu set as the default OS that boots.

peaz.

---

### Post by EvilRobotDrew on 2008-12-23
if anyone wants to move /home to the new partition, this thread may help, especially caljohnsmith's post

[http://ubuntuforums.org/showthread.php?t=986798](http://ubuntuforums.org/showthread.php?t=986798)

---

