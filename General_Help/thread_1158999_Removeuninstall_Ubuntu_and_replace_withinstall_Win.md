---
title: "Remove/uninstall Ubuntu and replace with/install Windows XP"
date: 2009-05-14
forum: General Help
---

### Post by swhite on 2009-05-14
All I want to achieve is to COMPLETELY replace Ubuntu with Windows XP (that is, preform a clean installation of XP). I have no files to lose or anything like that I just want my hard drive no longer have Ubuntu on it.
 

 OK, when I put in the XP disk and restart the computer (its a laptop btw) the disk automatically starts up and 'does it's thing' to start to install Windows, BUT it eventually comes up with this screen:
 

 _“... Windows XP Professional Setup_
 The following list shows the existing partitions and unpartitioned space in this computer.
 [and below in a box it says]:
 Unknown Disk
 	(There is no disk in this drive)...”
 

 So I can't "just install Windows over Ubuntu"
 Suggestions?
How do i format the hard drive?

 Can I somehow do it through Ubuntu (like can be done EASILY with Windows)?
 Can I somehow get rid of Ubuntu using the Ubuntu installation disk? (could be a stupid suggestion IDK)


PLEASE HELP

---

### Post by lisati on 2009-05-14
One possibility: use an Ubuntu LiveCD to run gparted and delete or reformat the partition to something that Windows can recognize.

---

### Post by swhite on 2009-05-14
What's "gparted"?
Is it already on the LiveCD?
When i put the LiveCD in its comes up with "Install Ubuntu" and other stuff that doesn't point toward reformatting or "gparted"...

---

### Post by lisati on 2009-05-14
> **swhite said:**
> What's "gparted"?
Is it already on the LiveCD?
When i put the LiveCD in its comes up with "Install Ubuntu" and other stuff that doesn't point toward reformatting or "gparted"...

gparted is a partition manager. On the Ubuntu "Live CD", select the "Try Ubuntu" option. You should be able to find something about "gparted" or "partition manager" on the System->Administration menu.

---

### Post by Iusedtowearatie on 2009-05-14
Try this:
[http://www.dban.org/](http://www.dban.org/)

It completely wipes the disk. Starting from there, the Windows install should be able to handle the rest...

---

### Post by swhite on 2009-05-14
Ok thanks for the tip. 
i'll give it a shot 
If u don't hear back, you'll know that it worked

---

### Post by hobo14 on 2009-05-14
Yes, it's a pity windows is unable to recognise any file systems but fat and ntfs.

From livecd:

choose: Try ubuntu without installing/changing anything

when it's loaded:
menu > system > adim > partition editor

Then you can do what you like to the partitions.

---

### Post by 3startuna on 2009-05-14
> **swhite said:**
> All I want to achieve is to COMPLETELY replace Ubuntu with Windows XP (that is, preform a clean installation of XP). I have no files to lose or anything like that I just want my hard drive no longer have Ubuntu on it.
 

 OK, when I put in the XP disk and restart the computer (its a laptop btw) the disk automatically starts up and 'does it's thing' to start to install Windows, BUT it eventually comes up with this screen:
 

 _&#8220;... Windows XP Professional Setup_
 The following list shows the existing partitions and unpartitioned space in this computer.
 [and below in a box it says]:
 Unknown Disk
 	(There is no disk in this drive)...&#8221;
 

 So I can't "just install Windows over Ubuntu"
 Suggestions?
How do i format the hard drive?

 Can I somehow do it through Ubuntu (like can be done EASILY with Windows)?
 Can I somehow get rid of Ubuntu using the Ubuntu installation disk? (could be a stupid suggestion IDK)


PLEASE HELP

Windows isnt recognising the filesystem linux runs on.

Try this pop in the Linux CD run live CD reformat the partition as NTFS using system > administration > Partition manager

Then restart the computer pop in the XP CD and boot from that, the NTFS partition should now show up. And install

Windows is kind of a silly OS and its easy to hide things from it.

I had a hidden partition on my computer that Windows couldnt even access, but I was able to get into with Grub and linux.

Also if you dont mind me asking why are you going back?

---

### Post by swhite on 2009-05-17
Well i've used the partition manager to format the harddrive to nfts using the LiveCD like ppl said and still no luck in getting windows to recognise the harddrive when trying to install XP (the same message comes up). So i've reinstalled Ubuntu just to have a working laptop but i still want XP back, so i'm planning on getting an external HD case to put the laptop HD in and use to plug it into my desktop to try and format it there instead, see if it works...

Ubuntu is just too hard to learn about and get used to, and for me it's too much of a hassle and a pain in the **** when i wanna connect to networks and print through network printers. Also i really do not care about 'tweaking' or customising, i hate the terminal and code and all that ****, and i very rarely have problems with viruses and spyware or watever. So the way i see it, XP is much better to meet my simple hassle free needs.

---

### Post by lisati on 2009-05-17
I'm sorry to hear that you found Ubuntu frustrating. Many of us here at the forums find Windows just as frustrating, as illustrated by your difficulties getting XP back on your system.....

If you want to give Ubuntu another shot, you're welcome to ask questions about specific difficulties.....

---

### Post by ugm6hr on 2009-05-17
Did you try dban?

It will completely zero the drive as if it never had anything on it at all; if Windows doesn't recognise it at that stage, then that is a problem with Windows.  I am already suspicious of this, since if you truly reformatted the whole drive to NTFS, there would be no problem.

Nevertheless, dban is worth trying.

Out of interest, where did you get the XP CD?  Is it one that came with the computer (i.e. OEM) or a store-bought copy?

Good luck.

---

### Post by 3startuna on 2009-05-17
Thats a good point Something might be wrong with the copy of XP he has.

Is it a pirated OS or a store bought CD?

Thats another reason why i switched to linux XP was too much of a PITA whe you needed to do a reinstall and dont have a CD

---

### Post by swhite on 2009-05-18
> **3startuna said:**
> Thats a good point Something might be wrong with the copy of XP he has.

Is it a pirated OS or a store bought CD?

Yer it is a pirate copy actually but it has never done this on any other computer i've installed it to...

---

### Post by 3startuna on 2009-05-18
> **swhite said:**
> Yer it is a pirate copy actually but it has never done this on any other computer i've installed it to...

dude NEVER use a Pirate OS thats why your having problems

---

### Post by helofromseattle on 2009-05-18
If you want a fresh windows xp install you have to...

1 - boot into the Ubuntu live CD then, go to System -> Administration -> Partition Editor

2 - unmount all your partitions (if mounted), delete you linux swap partition and resize the main linux partition to take up all unallocated space

3 - right click on your main linux partition click Format to -> ntfs

4 - click apply and wait for it to finish the tasks

5 - now reboot your machine and put in the Windows XP install disc, run the install normally, you should be good to go

hope this helps:p

---

### Post by ugm6hr on 2009-05-18
Closed.

Advice re: installing a pirated OS is not permitted.

---

