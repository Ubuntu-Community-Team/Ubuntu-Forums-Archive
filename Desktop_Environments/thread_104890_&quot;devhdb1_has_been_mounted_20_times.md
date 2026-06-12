---
title: "&quot;/dev/hdb1 has been mounted 20 times"
date: 2005-12-17
forum: Desktop Environments
---

### Post by missmoondog on 2005-12-17
searched and found this thread pertaining to older ubuntu version, [http://www.ubuntuforums.org/showthread.php?t=20674](http://www.ubuntuforums.org/showthread.php?t=20674)
quoting original poster here:
"Hi folks,
I receive the following error this morning when i boot the box "/dev/hdb1 has been mounted 30 times without being checked, checked forced" . It then goes on to check the partition similar to windows' chkdsk. The message was shown during the very early initialization process. This has happened twice. I am not sure what causes the error to be generated. the hdb1 is the partition where i install ubuntu and it does not share any other os in it and my box is regularly turned on during the day and only is shutdown at night. any thoughts || suggestions?

-yoha"


i get same message, but it says after 20 times on mine. has only ever happened on this particular computer (twice) i'm on now. i have 4 others setup the exact same way, that have never done this check. my main computer is restarted more often than this one and one other computer is restarted at least as often also and has never done that. is there a way to disable it that i might have done on accident? if so, how do i re-enable it?

thank you

edit:
found part of my own answer.
[http://ubuntuforums.org/showthread.php?t=77771](http://ubuntuforums.org/showthread.php?t=77771)

---

### Post by kosmic on 2005-12-17
don't worry is normal, is just ext3 verifying your partitions, if you don't wan't to see ext3 doing that you can move to reiserfs that also have journaling filesystem

---

### Post by psyguy92 on 2005-12-17
would changing the pass from 1 to 0 in /etc/fstab eliminate this checking? or it that only for direct fsck commands?

I've wondered about this too.  I'd guess occasional checking is fine, but depending on the frequency of rebooting, it would be nice to be able to change the frequency of forced checks.

---

### Post by kosmic on 2005-12-17
ok :
> 
A feature of e2fsck is that it will regularly force a check of a 
        filesystem even if the filesystem is marked clean. Typically, this
        happens on every twentieth mount or every 180 days, whichever comes
        first.

        This still happens with ext3, and is quite possibly not what you want
        to happen - one of the reasons you chose ext3 was to avoid the downtime
        which is caused by a long fsck.

        So it is a good idea to turn this feature off for ext3. 
        Use the command

                   tune2fs -i 0 /dev/hdxx

        To disable the checking.



---

### Post by schdefan on 2005-12-17
you can change the frequency of forced checks with tune2fs
or to supress a force check from fsck.sh script which is loaded from /etc/rcS.d
put a 0 in /etc/fstab at the end of the line of the partitions.

The root filesystem should have a 1
other partitions can have 0 for no check and 2 for check

For example
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /mnt/hda6     ext3    defaults,users,rw 0       0
/dev/hda7       /mnt/hda7     ext3    defaults,users,rw 0       2

schdefan

---

### Post by anil_robo on 2005-12-18
[quote=kosmic]don't worry is normal, is just ext3 verifying your partitions, if you don't wan't to see ext3 doing that you can move to reiserfs that also have journaling filesystem[/quote]

Does it mean that there is an issue with ext3 filesystem? I have the same file system and receive the disk check message sometimes.

If I choose Reiser File system, would a disk check be not required?

Is Reiser FS better than ext3? If yes, in what respects?

---

### Post by missmoondog on 2005-12-18
appreciate all the excellent replies, but i'm still curious as to why i haven't seen it do the check on the 2 other machines that are used more often than the one in question? all machines are setup exactly the same.

---

### Post by kosmic on 2005-12-18
[quote=anil_robo]Does it mean that there is an issue with ext3 filesystem? I have the same file system and receive the disk check message sometimes.
 
If I choose Reiser File system, would a disk check be not required?
 
Is Reiser FS better than ext3? If yes, in what respects?[/quote]
 
From what i know both are very good File System types, the diferences beetween them is that ReiserFS only journals the meta-data, while Ext3 can journal meta-data or meta-data + the actual file content data.
 
Please have a look at this document -> [http://www.linuxgazette.com/issue68/dellomodarme.html]("http://www.linuxgazette.com/issue68/dellomodarme.html") from LinuxGazette
 
Also
 
**Advantages of EXT3**
By contrast, ext3 does not require a file system check, even after an unclean system shutdown, except for certain rare hardware failure cases (e.g. hard drive failures). This is because the data is written to disk in such a way that the file system is always consistent. The time to recover an ext3 file system after an unclean system shutdown does not depend on the size of the file system or the number of files; rather, it depends on the size of the "journal" used to maintain consistency. The default journal size takes about a second to recover (depending on the speed of the hardware).
 
So I don't know way ext3 forces the file check of the system after 120 days or x reboots, it is not needed is normal circunstances. so you can deactivate this procedure with the tune2fs comand.

---

### Post by anil_robo on 2005-12-19
[quote=kosmic]Please have a look at this document -> [http://www.linuxgazette.com/issue68/dellomodarme.html]("http://www.linuxgazette.com/issue68/dellomodarme.html") from LinuxGazette [/quote]

Quote from a paragraph in the above article:
>   There are at present time at least two robust and reliable journalling  filesystems for Linux (i.e. XFS and reiserFS) which can be utilized  without fear.
  ext3 is still an alpha release and can undergo several failures.

---

### Post by zugvogel on 2006-10-22
In terms of useabilty, this is a serious problem. For the system to perform a check like that, without the ability to cancel the check or postpone it to a later date, is just stupid. The other day I was in a hurry and had to get some important information from my laptop before leaving the office. When I turned it on however, Ubuntu decided to do a system check. I tried Ctrl-C but upon restarting my laptop, the system started doing its check again. In the end I had to leave without the information which was quite inconvenient, to say the least...

I see from this thread that there is an ability to turn the check off. I want to know; is this safe? And for the "average" computer user who does not know about these forums, future releases of Ubuntu must include a way to postpone such a check. I hate the thought of starting my laptop to give a presentation, only to find that I and my audience have to wait 5 minutes for a "system check" to finish...

---

### Post by kvonb on 2006-10-23
You know, mine does this as well, it always seems to be at the most inconvenient time, when you just need to do something quick!!

I generally ignore it and just complain until it's finished, but last week I got a system BIOS message saying something about SMART status bad.

I'm wondering if the reason for the forced check is that SMART has reported an error on the disk, which in turn forces the filesystem check?

It makes sense to me, SMART has marked another sector as bad, which means that some data is either bad or has been relocated on the disk, ergo ext3 would want to know about it and update it's journals accordingly.

Thoughts?

Regards,

Kev :)

---

### Post by danielferber on 2006-11-03
I agree. The disc check is completely inconvenient and useless, since it never detected and error. I work most of the time out of office and carry my laptop with me. Since Linux is not very smart for saving battery in standby, I have to turn the laptop completely off several times a day.

This means that I have to waste time waiting for forced disc checks several times per week, very inconvenient, specially when I need to make demos for clients or check some information when someone calls me by phone.
 
It is really an usability issue, and it was already an usability issue ten years ago with the first Redhats. Ubuntu has succeeded in many efforts in making life easier, but on some important and trivial usability issues people from Ubutu still seem to be asleep and do people from other Distros.

---

