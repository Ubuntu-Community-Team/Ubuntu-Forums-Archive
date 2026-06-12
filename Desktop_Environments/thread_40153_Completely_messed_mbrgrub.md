---
title: "Completely messed mbr/grub"
date: 2005-06-07
forum: Desktop Environments
---

### Post by vaskark on 2005-06-07
I did something that I haven't a clue how to fix. I have a dual boot system with XP and Ubuntu Hoary. I tried using Partition Magic to make a new FAT32 partition that could be shared by both systems (for my music files). Anyhoo, errors occured. I rebooted and grub presented me with Error 17 (I think). So now I can't get into XP or Ubuntu -- i'm using the hoary live cd right now. I tried booting with my WinXP cd but I couldn't get to a console to do 'fixmbr', but I may have missed it since I've never had to do this before.

So I need serious help in restoring my mbr and repairing grub so that I can once again boot into my XP and Ubuntu partitions. I'm a little worried at this point. If someone patient can help me it would be sooo appreciated, or at least hold my hand to get me started.

Thanks.

---

### Post by bored2k on 2005-06-07
[QUOTE=vaskark]I did something that I haven't a clue how to fix. I have a dual boot system with XP and Ubuntu Hoary. I tried using Partition Magic to make a new FAT32 partition that could be shared by both systems (for my music files). Anyhoo, errors occured. I rebooted and grub presented me with Error 17 (I think). So now I can't get into XP or Ubuntu -- i'm using the hoary live cd right now. I tried booting with my WinXP cd but I couldn't get to a console to do 'fixmbr', but I may have missed it since I've never had to do this before.

So I need serious help in restoring my mbr and repairing grub so that I can once again boot into my XP and Ubuntu partitions. I'm a little worried at this point. If someone patient can help me it would be sooo appreciated, or at least hold my hand to get me started.

Thanks.[/QUOTE]
 When you load your windows disc, during the beggining of the blue screen, in the lower part of the screen it will say something like 'Press F7 for the recovery console' or something like that.

Also try [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) .

BTW I hate these method (my fav is to use a tool disc like Hiren's boot cd v6 or ultimatebootcd.com, but I guess they should work.

---

### Post by emperor on 2005-06-07
If you inserted a new partion between winxp and Ubuntu, then the partion numbers have changed and thus grub would fail. I use partion magic myself and screw-up grub all the time, but it can be fixed, and is now easy for me to do, but will be a little difficult for a newbe. However you will learn a lot in the process.. 

The first question is, what did you do!

Start partion magic and report back what the partion arrangement is on the disk.

In your spare time, download the Ubuntu Live CD, you will need it later to 'rescue" your installation.

---

### Post by vaskark on 2005-06-08
[QUOTE=emperor]If you inserted a new partion between winxp and Ubuntu, then the partion numbers have changed and thus grub would fail. I use partion magic myself and screw-up grub all the time, but it can be fixed, and is now easy for me to do, but will be a little difficult for a newbe. However you will learn a lot in the process.. 

The first question is, what did you do!

Start partion magic and report back what the partion arrangement is on the disk.

In your spare time, download the Ubuntu Live CD, you will need it later to 'rescue" your installation.[/QUOTE]

See, I can't boot into WinXP from my cd. I found the console mode, but it wouldn't accept my administrator password. I did, however, find a grub floppy boot disk from a few months ago and used to boot into XP (it wouldn't let me boot into ubuntu). So right now I'm in Windows again. Is there anything I can do from a command prompt from here?

In terms of Partition Magic, see this [shot]("http://home.cogeco.ca/%7Ejstrickett/pm.jpg"). The G drive is the newly created FAT32 partiton; the D is another hard drive. But the data seems weird to me: the linux partitition is being reported as full, which it most certainly should not be. Is this because I booted from that floppy?

I already have a Live CD. Hopefully you can help me.

---

### Post by emperor on 2005-06-08
1. Boot with the live CD. 

Note: you may have to use sudo if you can not login as root. I generally use the Fedora #1 cd and start it with "linux rescue"!

2. Then create a directory in /mnt called ubuntu.
    cd /mnt
    mkdir unbuntu

3. Then try to mount the ubuntu partion. It should be partion #6 or hda6.

   mount -t ext3 /dev/hda6 /mnt/ubuntu

4. check that the the drive mounted and the data looks like your drive. 

cd /mnt/ubuntu
ls -l

5. while in /mnt do:
 
cd /mnt
 chroot ubuntu

6. your ubuntu partion should be the root partion now.

7. grub-install /dev/hda      (no subscript number after "hda" or no more windows!)

8. Now you need to edit /boot/grub/menu.lst and correct the drive partion index.

for example, if your Ubuntu is on partion 6, then

title           Ubuntu, kernel 2.6.10-5-k7
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/hda6 ro quiet splash 
initrd          /boot/initrd.img-2.6.10-5-k7
savedefault
boot

Note: I would change this one too, which is at the upper part of menu.lst:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

9. shutdown and restart. Grub should come up now if the partion info is entered correctly.

Be carefull and Good luck!

Note: I have ext3 drives in partion magic that say there is no free space before, mainly with Fedora ext3 partions. The partion is OK and will show up correctly in linux. However you will not be able to re-size it or expanded it with partion magic.

---

### Post by vaskark on 2005-06-08
Everything went ok until step 7 in your instructions.

 > root@ubuntu:/# grub-install /dev/hda
The file /boot/grub/stage1 not read correctly.

I'm rebooting now. Wish me luck! ;)

update:

After following all your instructions I rebooted and encountered the same grub error:

GRUB Loading stage1.5
GRUB Loading please wait ...
Error 17

So i'm anxious to hear your thoughts on what happened at Step 7. And thanks for all your help, btw!!!

---

### Post by emperor on 2005-06-08
[QUOTE=vaskark]Everything went ok until step 7 in your instructions.

I'm rebooting now. Wish me luck! ;)

update:

After following all your instructions I rebooted and encountered the same grub error:

GRUB Loading stage1.5
GRUB Loading please wait ...
Error 17

So i'm anxious to hear your thoughts on what happened at Step 7. And thanks for all your help, btw!!![/QUOTE]

I get the same grub-install error but grub still installed OK. 

Apparently there is something else wrong, error 17 needs to be investigated further.

Grub should be looking for the second stage loader in /boot/grub on partion 6. Ubuntu was on partion 6 wasn't it? Did you verify my calculations?

Also, I should have mentioned to check "/etc/fstab" on the ubuntu partion and correct the partion assignments for ubuntu. If it uses labels, there's nothing to change.

.

---

### Post by vaskark on 2005-06-08
[QUOTE=emperor]I get the same grub-install error but grub still installed OK. 

Apparently there is something else wrong, error 17 needs to be investigated further.

Grub should be looking for the second stage loader in /boot/grub on partion 6. Ubuntu was on partion 6 wasn't it? Did you verify my calculations?

Also, I should have mentioned to check "/etc/fstab" on the ubuntu partion and correct the partion assignments for ubuntu. If it uses labels, there's nothing to change.

.[/QUOTE]
In my /boot/grub on partition 6 (which *is* my ubuntu system -- i went into my home directory and saw all my files) there are files named stage1 and stage2. Is stage2 the second stage loader you are referring to?

I did have to make a change in my /etc/fstab file, to change my '/' mount point to /dev/hda6 (before I made that extra partition that caused this mess it was hda5).

Rebooting ...

Update:

Still Error 17. But I noticed something. When grub is loading from the hd it states "Loading stage1.5". There wasn't a stage1.5 file in /boot/grub. Also, when I use that ubuntu grub boot floppy it says "Loading stage2", which lets me get into windows. This boot floppy does allow me access to a grub prompt so maybe I can work from there. But I'm not sure how.

Anyhoo, that's where I'm at right now.

---

### Post by vaskark on 2005-06-08
I was finally able to use my WinXP install cd to get to console mode and use 'fixmbr', which did work. I went through your posted instructions again and keep getting the same error at the same point:

# grub-install /dev/hda
 The file /boot/grub/stage1 not read correctly.

So i'm not sure what to do now. Do you think reinstalling hoary will work? Would I lose all my files if I did?

---

### Post by stoneguy on 2005-06-08
Diagram you posted is a bit odd...

First off, you don't have a swap partition. You'll probably need one.

2nd, the D partition primary after the extended partition isn't the usual way of doing things.

I haven't installed Ubuntu since Warty, but I think I remember a "install to unused space" option. If that's correct, try the following.

Since you have Partition Magic, do the following (assuming your D partition doesn't have hidden files):

[INDENT]1. copy the contents of the D partition into a directory on C.

2. take down the D partition

3. take down each logical partition in the extended partition

4. take down the extended partition itself

5. create an extended partition for the remaining disk

6. create a swap partition (2-3x) your RAM

7. create a FAT logical partition for your D drive

8. copy back stuff original contents

9. create another FAT logical partition for sharing (why not use D drive though?)

10. Install Ubuntu to unallocated space (which is leftover in your extended partition ) [/INDENT]

That will give you a hard drive with Ubuntu on the last logical partition, swap on the 1st logical partition, and 1 or 2 FAT partitions lettered D and E under WinXP. Adjust /etc/fstab to mount the one you really want.

---

### Post by vaskark on 2005-06-08
The D: partition is a second hard drive, and has nothing to do with my current problem.

Partition Magic keeps giving me Error #510 when I try to do anything to the Linux partition. Things are sufficiently effed at this point. I won't even let me delete it!! Oh well. Glad I backed up all my music and stuff.

Thanks for all the suggestions, guys. A great community :)!

---

### Post by bored2k on 2005-06-08
[QUOTE=vaskark]The D: partition is a second hard drive, and has nothing to do with my current problem.

Partition Magic keeps giving me Error #510 when I try to do anything to the Linux partition. Things are sufficiently effed at this point. I won't even let me delete it!! Oh well. Glad I backed up all my music and stuff.

Thanks for all the suggestions, guys. A great community :)![/QUOTE]
 Ok onto more advanced tips.

[http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

---

### Post by stoneguy on 2005-06-09
[QUOTE=vaskark]The D: partition is a second hard drive, and has nothing to do with my current problem.[/QUOTE]
Not according to the diagram you posted. PM would show it on Disk 2. Here it's on Disk 1.

At what step number (1-10) of my previous message are you getting the error?

I've seen instances where PM will squawk, but Acronis Partition Manager will work.  If you can locate a copy, give it a try too.

UBCD of course will let you do anything to anything. But I'm not sure how helpful it would be unless you recalculated what the partition table would look like for your HD with only the NTFS partition plus unused space and entered that directly in. I don't have a clue how to do that, or where to find the info.

---

### Post by emperor on 2005-06-09
[QUOTE=vaskark]
Update:

Still Error 17. But I noticed something. When grub is loading from the hd it states "Loading stage1.5". There wasn't a stage1.5 file in /boot/grub. Also, when I use that ubuntu grub boot floppy it says "Loading stage2", which lets me get into windows. This boot floppy does allow me access to a grub prompt so maybe I can work from there. But I'm not sure how.

Anyhoo, that's where I'm at right now.[/QUOTE]

Boot floppy's are great! At least your up again!

I had to go out of town on business yesterday and did not have my laptop with me, so no way to communicate until now. There is a way to restore grub using the boot floppy you made, I have done it before but my notes are at home. I'll take a look this evening and post again.

---

### Post by emperor on 2005-06-09
[QUOTE=vaskark]I was finally able to use my WinXP install cd to get to console mode and use 'fixmbr', which did work. I went through your posted instructions again and keep getting the same error at the same point:

# grub-install /dev/hda
 The file /boot/grub/stage1 not read correctly.

So i'm not sure what to do now. Do you think reinstalling hoary will work? Would I lose all my files if I did?[/QUOTE]

Maybe the file system is damaged and needs to be repaired. You can use the linux command "fsck" to check or repair it. You do NOT mount the drive, just run fsck on an umounted drive! Check the usage of fsck with --help to verify the suggested format below. I'm not at a linux machine right now!

1. Boot with the Ubuntu live CD.

2. Then run "fsck -F ext3 /dev/hda6

[http://www.adminschoice.com/docs/fsck.htm](http://www.adminschoice.com/docs/fsck.htm)

If errors and found you should be prompted for permission to fix it. 

If errors are found and fixed, try to install grub again per eariler instructions.

---

### Post by emperor on 2005-06-09
IT does appear that the D: drive is on the same hard drive, hard drive #1. A primary partion created in an extended partion is quite wierd! You may be able to fix it by saving the data on drive D somewhere and then deleting the D: Fat partion using  Pariton Magic. Then run fsck as I mentioned earlier and try to repair the Ubuntu partion. I have seen the unused size of an ext3 partion set o zero when this is untrue in reality; at least with Fedora Core 2 and Core3 created partions. So, the fact that the size says 0 does not rule out being able to fix it, at least in my experience.

---

### Post by stoneguy on 2005-06-09
[QUOTE=emperor]A primary partion created in an extended partion is quite wierd!.[/QUOTE]
Nope, that's downright impossible AFAIK - look closer at his picture. The 2nd primary partition is **after** the logical, not **in** it. There's nothing in the specifications for disk partitions about the order they occur in. There's a limit of 4 partitions because that's all the space there is in the boot sector for the 4 16-byte entries describing them. Any one of those entries can be an extended partition. I've had secondary data drives with NO primary partitions so pulling them in and out didn't change letter assignments.

If vaskark is both brave and desperate, he can do the following.  

Use a linux rescue CD to back up the hard-drive boot sector to a floppy using
[INDENT]dd if=/dev/hda of=/dev/fd0 bs=512 count=1[/INDENT]
Then, use a disk sector editor to set bytes 01BE thru 01ED to zeros for sector 0 of /dev/hda. Doing this will blow off partitions 4, 3, and 2 (yes, the entries are in reverse order). Before you do anything, check whether bytes 01FE and 01FF are AA55 to be sure it's the right sector.

Reboot, and all there should be is a single primary partition of your C drive. If the reboot doesn't work, use fixmbr or whatever from the XP rescue console (I'm fuzzy on this part having only done stuff like this from Win9x) and try again.

Now use PM to put a logical partition on the all the disk space that's left, lay out the additional FAT32 chunks (leaving unused space), and install Ubuntu (letting it use that unused space however it sees fit).

If this makes things worse instead of better, use that linux rescue CD to restore the hard-drive boot sector from the  floppy via
[INDENT]dd if=/dev/fd0 of=/dev/hda bs=512 count=1[/INDENT]
Remember that in life and linux there are no guarantees  :)

---

### Post by Nu-Buntu on 2005-06-09
Looking at your Partition Magic screen shot, it appears that your ext3 partition is totally full. Also, I don't see a Linux swap partition. Don't know if either of these is the problem, but thought I would point it out just in case it was.

---

### Post by vaskark on 2005-06-09
[QUOTE=emperor]Boot floppy's are great! At least your up again!

I had to go out of town on business yesterday and did not have my laptop with me, so no way to communicate until now. There is a way to restore grub using the boot floppy you made, I have done it before but my notes are at home. I'll take a look this evening and post again.[/QUOTE]
I made the boot floppy a while ago according to these instructions:

[http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy]("http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy")

But this was a while ago. It allowed me to get into WinXP, so at least that's something :).

Update:

Holy s***! Drive D: IS a partition, not a second hard drive. It's got a ghost backup to restore my system. I should start taking my medication again ... maybe :?

---

### Post by stoneguy on 2005-06-09
[QUOTE=vaskark]Drive D: IS a partition, not a second hard drive. It's got a ghost backup to restore my system. I should start taking my medication again ... maybe :?[/QUOTE]
No, just get your glasses changed :)

If D is a partition that shipped with your lappie as a recovery partition, better disregard the instructions in my previous posting. They can be pretty weird beasts in terms of booting and reinstalling.

If you have a CD set to install from, you could proceed.

---

### Post by emperor on 2005-06-09
When I setup my Dell Inspiron 9300, I deleted the primary ghost partion at the end of the drive prior to creating other partions and installing linux

---

### Post by vaskark on 2005-06-09
Ok, here's what I'm thinking: I'm gonna get someone at my local tech shop to do this for me, as I'm in wayyyy over my head. So when I get my machine back I'll reinstall Hoary from scratch. But I have a few questions to ask ...

1) In previous posts in this thread I was shown how to use the live cd to 'get' at my hoary files. I'm wondering if there's a way I could go in, somehow get a list of all packages I installed through synaptic, back it up to a remote server, so that when i do reinstall I can use apt-get to reinstall all the packages I had previous to this situation. Is this possible? It would make restoring my system a heck of a lot quicker. When I think about all the stuff I compiled myself the thought of tracking down all those dependencies ... *curls into fetal position*

2) Before I reinstall Hoary should I use Partition Magic to make an ext3 partition beforehand? That way, when I get to the partition-related install section, I can just assign it there? Also, I suppose I should also make a /swap partition (which I didn't have before). My machine has 512 Mb of RAM ... how big should a swap partition be?

3) During the last time I installed Hoary I don't recall ever being offered the chance to make a grub install floppy. This would be ideal, as I'd rather not have hoary touch my mbr anymore (lol). What would people suggest?

Thanks, guys. I'm gonna take my pc in tomorrow so I won't have it for a while. I'll have to use my older machine til then (P166/WinME ... *shudder*).

Bye!

---

### Post by FLeiXiuS on 2005-06-09
"ERROR 17: Can not mount selected partition--This error is returned if the selected partition exists but the file system type can not be recognized by GRUB."

Thus stating your grub.conf is some where incorrect?  What's your configuration look like?

---

### Post by stoneguy on 2005-06-10
If you want to hack away at this some more, post your grub.conf. Unless your local tech shop is linux-friendly, they're likely to just wipe the disk and reinstall. You won't learn anything that way.

There may be some useful clues at [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml) It could be something as simple as needing the bootnoverify / chainloader statements in para 5.

---

### Post by vaskark on 2005-06-11
OK, I'm back using the live cd and have made my linux file system the root file system again (it's back to hda5 now, btw). I can't seem to find grub.conf, though. I though it would have been in /etc but locate says not. Do I need to re-generate it from scratch somehow?

---

### Post by stoneguy on 2005-06-11
Sorry, not grub.conf (I'm still thinking lilo). It's /boot/grub/menu.lst (at least on my system with a separate /boot partition) that tells grub where everything lives. The last 2 items in the FQN are always "grub/menu.lst"

To be quite honest, I'm not quite sure what the current state of your machine is right this minute. Please provide the following answers (along with the menu.lst file)

When you boot the hard drive, do you go directly into WinXP, or do you go into grub?
If you go into grub, do you get the choices menu? If not, is that where you get the ERROR17?
If you get the choices menu, do any of them work? For ones that don't, what error occurs?
If you get into WinXP, can you run Partition Magic?

What I'm trying to figure out here is which would be your best way forward:
[list=1]
[*]tweaking of menu.lst
[*]reinstalling grub
[*]fixmbr to blow off grub completely and then reinstalling ubuntu so all the setup will be recreated. Save any personalization first so you can recreate it (much handwaving here :-\" )
[/list]

I can make suggestions on #1. Someone else will have to jump in on #2. #3 you should be able to do on your own.

PS This situation is an excellent example of why I advocate using advanced partitioning during install to create a minimum of 4 logical partitions (/, /boot, /home, swap). I consider it a must for anyone seriously using linux. Makes reinstalls so much easier, and gives you a place to stash what you need from /etc (you don't reformat /home when it asks you after the 1st install).

---

### Post by vaskark on 2005-06-11
stoneguy,

I can boot directly into XP (I used the xp install disk to fixmbr). Previously, when grub was still on the mbr, grub gave me Error 17 right away (no choices offered). I can run Partition Magic in XP - here's a [screenshot]("http://home.cogeco.ca/%7Ejstrickett/pm_latest.jpg") of it's current state. I've attached my menu.lst to this post.

Hope that's it. Thanks, stoneguy.

---

### Post by stoneguy on 2005-06-11
Easiest way to proceed from here would be to take down the 10GB ext3 partition. That would create a 14GB unallocated chunk.

Then install ubuntu again, telling it to use unallocated space. It should create 2 partitions, swap and /.

The menu.lst file you attached looks ok at first glance, but I'm wondering if the root (hd0,0) line for XP should've actually been rootnoverify (hd0,0) I don't have an XP system using GRUB to check a working menu.lst. 

I also don't know whether there are any cylinder limits for the location of the boot. There used to be under LILO (one of the reasons GRUB suddenly got popular).

Anyone else out there can check this? Maybe you can catch somebody on IRC.

Good luck! And let us know what finally worked.

---

### Post by vaskark on 2005-06-11
Here's the thing: I *can't* take down the ext3 linux partition at the moment. Partition Magic keeps giving me **Error #510: The version of the file system is not supported**. I googled that and found out that PM may not work with ext3 partitions when the dir_index file system attribute is enabled. As far as I know that isn't enabled by default in Hoary.

](*,)

---

### Post by stoneguy on 2005-06-11
Well, we're not done yet. I was afraid that you'd end up right back where you started from.

If Partition Magic is too fussy, boot from a live cd and use linux's fdisk from a root console to tear down that partition. See [http://www.tldp.org/HOWTO/Partition/partition-5.html](http://www.tldp.org/HOWTO/Partition/partition-5.html) 
Summarizing, you'll go into it with
[INDENT]fdisk /dev/hda[/INDENT] then use the **p** command to list the partitions, then the **d** command to delete the 10GB one, and the **w** command to write and exit. Whatever you do, _don't_ touch partition #1. That's your NTFS partition.

When you reboot into windows and run PM, that 10GB partition should be gone, and the 14GB extended partition should be entirely unused. Now you can reinstall ubuntu.

---

### Post by vaskark on 2005-06-11
I followed your fdisk instructions and it seems to have worked! (see [here]("http://home.cogeco.ca/%7Ejstrickett/pm_correct.jpg")). I can't thank you enough, stoneguy, and emperor, and all the other people who took the time to offer help.

So, when I reinstall Hoary I just tell it to use the unallocated space. Will it make a swap partition for me, or do I have to do that manually? I'll probably wait a few days before I reinstall - give my system (i.e. me!) a chance to unwind from an extremely frustrating time.

Thanks again, guys ;)

---

