---
title: "Multiple boot and NTFS problems -- Vista, Ubuntu/GRUB, CHKDSK"
date: 2009-01-10
forum: General Help
---

### Post by wesleyx on 2009-01-10
I have a dual-boot (Vista/Ubuntu) system, with 2 system hard drives.  Each drive has both Vista and Ubuntu, in multiple partitions, and my intent is that the second hard drive should be a bootable mirror of the first, for both Vista and Ubuntu.  This seemed like a very good idea at the time -- in the event of a drive problem on HD-0, I simply would boot from HD-1, for both Vista and Ubuntu.  I could then replace HD-0 and clone back to it, but in the meantime, keep working or playing or whatever!

It doesn't seem like it was such a good idea now, because (1) it seems that Vista always boots from HD-1, no matter whether I order it to boot from HD-0 or HD-1 and (2), much worse, I am having persistent and recurrent MFT BITMAP corruption on the Vista data partitions on both drives.

Details:

My system is an HP m9040n with a Q6600 Core2 Quad CPU, 3 GB RAM, and 2 320 GB hard drives, running 32-bit Vista Home Premium.  I used BootIt-NG and Acronis Disk Directory to do the partition work, Clonezilla for making a complete clone from HD-0 to HD-1, and to make clone images to a 500 GB USB drive for image backups.  Also used Acronis True Image for some partition backups.  Used SyncToy to keep slave Vista partitions in sync with master Vista partitions.  Intended to do similar synchronization for Ubuntu using rsync, but haven't gotten that far.  Also used JungleDisk for Internet backup of user files.  (I'm big on backup.  When you comprehend all the problems I've been having, you can see why!)  BTW, the reason I didn't consider a soft RAID-1 solution is that I know of no such software that would work for both the ntfs and ext3 partitions.

The first attachment, Partitions.jpg, is an Acronis Disk Director screen shot showing all the partitions on both drives.  The Ext3 partitions are for Ubuntu, obviously.  I kept the original Vista install on HD-0, repartitioned using BootIT NG, and went to some trouble to put most subfolders of Users\* onto the Vista Data (E) drive.  I installed Ubuntu and set up the Ubuntu users, etc. in the Ext3 partitions.  Then I used Clonezilla to clone the entire thing to HD-1.  I booted from HD-1, in both Vista and Ubuntu, and all seemed fine.  (Many steps and stumbles left out, of course.)  For multiple boot control, I used GRUB.

The second attachment, menu.lst, contains the non-boilerplate parts of my GRUB menu.lst file, showing GRUB boot commands for all configurations.  As you can see, it has entries for booting from each of the primary partitions on both HD-0 and HD-1.

Things seemed to be going fairly well, but then I moved and the system was dormant for about 3 months.  After I got it back up a couple of weeks ago, I started noticing problems.
______________

Problem 1:  Why can't I get Vista to boot from HD-0?  Or is it booting from HD-0 and assigning the system disk letter to be G ?  Is this a Vista problem or a GRUB problem?

Multiple boot into Ubuntu seems to work fine, with the single anomaly that, when booted from HD-1, df tells me that /dev/sda4 is mounted on / when I am convinced (because of Used/Available figures) that it is actually /dev/sdb4, as it should be -- see attachment dfLies.txt.  (sda is HD-0 and sdb is HD-1)

However, no matter whether I use the GRUB entry for HD-0 Vista or the GRUB entry for HD-1 Vista, the results, as displayed by Acronis, are the same -- C: is assigned to the first partition on HD-1 and E: to the second partition.  I believe that C: is always my Vista system disk, and I haven't tried to play any games with changing letter assignments to partitions.  (If I am wrong on this, please correct me, because then maybe the Vista dual boot is working!)  BTW, uncommenting the map commands on the HD-1 Vista entries has no apparent effect.
________________

Problem 2:  MFT BITMAP attribute corruption.

Starting a week ago, when I tried to use SyncToy beta to synchronize some folders between C: and E:, E: has had persistent and recurring  MFT BITMAP errors.  I have run CHKDSK many times, and most often it says it fixed the problems -- a second run finds the same MFT BITMAP corruption problem.

Using Acronis Disk Director/True Image, I backed up the entire partition to an external drive, reformatted the partition and restored.  At this point, the corruption problems had disappeared, but they came back after I did another SyncToy run or two.  I am running SyncToy beta, downloaded last August.  I am a suspicious that SyncToy might be causing the problems, but I don't really think so.

Another possibility is that Vista somehow is confusing the Vista Data-1 partition on HD-1 with the Vista Data partition on HD-0, so writing inconsistent information to the BITMAP attributes, sometimes on HD-0 and sometimes on HD-1.  Originally, the partition labels were identical between HD-0 and HD-1 -- I assumemd that any reasonable system could keep them straight, since the most fundamental address, the hardware address, was different.  I changed the partition labels on Jan. 4, and things have not improved -- but maybe the damage was already done by then?  Seems farfetched, but I am grasping at straws here!

From what I understand from an earlier post/reply, CHKDSK can't correct BITMAP problems.  (If not, why does it say that it did correct them!?!  Arrrggghhh!!!)  Is there any utility that can?

Any chance a virus or worm might be causing the BITMAP problem?  I am running Norton 360, and am faithful about keeping it up to date.

Is there a way I can command Vista to not mount the extra partitions at boot time?  At least that might allow me to analyze the problem better.

Anyone have any idea what might be really going on?  I'm willing to do the backup/reformat/restore exercise again, but if the errors just come back an hour later, what's the point?

For anyone who wants to be truly bored, the last attachment, Problems090103.txt, details the saga.
___________________

Thanks for any help or pointers you might give me.

Bruce

---

### Post by caljohnsmith on 2009-01-10
It sounds like the basic problem with what you are trying to do is that you have both HDDs plugged in at the same time when you try to boot one of them. If one drive is an exact clone of the other, then for instance with Ubuntu that will cause the exact problems that you are having; the partitions on both drives will have the same UUIDs, so when you boot Ubuntu, Ubuntu may mount the partition on the wrong drive. Vista would give you similar problems I would think, and it sounds like that may be what you are experiencing. So unless you want to go through the trouble of changing the partition UUIDs (and at least a few Ubuntu system files to go with that), and also maybe using tricks like "hiding" partitions so Vista doesn't have problems, I think the easiest solution to your dilemma might be to only have one HDD plugged in when you boot it. I don't know if that would work in your case though, but it sure seems like you could be in for a lot more headaches if you really want to boot one of the drives while the other one is plugged in. Maybe there's an easy way around those issues that I'm overlooking, but those are just my initial thoughts about your situation. Good luck though and please keep us posted about what you end up doing. :)

---

### Post by wesleyx on 2009-01-10
What you say about UUID's makes sense if the OS's, indeed, work that way, ignoring hardware disk addresses (personally, that sounds like an insanely bad design!!).  Unfortunately, both the drives are internal, so I can't just routinely unplug one or turn it off.  I think I'm going to have to start over at some point, and take a few days to rework the entire design, throwing out my fundamental idea that making a clone for an online backup would be a good thing!!  Have to study up on UUID's.

Thanks for the info and suggestions.

---

