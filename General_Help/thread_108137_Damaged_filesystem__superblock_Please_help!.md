---
title: "Damaged filesystem / superblock? Please help!"
date: 2005-12-25
forum: General Help
---

### Post by psyguy92 on 2005-12-25
Firstly, Merry Christmas to all forum members :)

I have some files I can't delete and bootup reported a filesystem error.  My main drive booted fine.  The files are on my external storage drive (usb, ext3, /dev/sdb).  The drive's icon appeared on the desktop when I booted. This error started after windows crashed while writing to the storage drive.  Here's what I see:

```
$ ls -al Stu*
ls: Stuff: Input/output error
```

I can see this file (and several others) in file manager, and in the terminal, but can't do anything with them - no delete, open, move, etc.  I have good copies of these files, so I'm not concerned about loosing these files, but I am concerned about the rest of the data on the drive (currently fine).  I've never ran fsck before, but I was guessing now was the time.  I unmounted the drive, and did this:

```
$ sudo e2fsck -v /dev/sdb
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

That looks bad.  Should I be worried? What should I do? Can I delete these corrupt files? Is the drive going to be OK?  Is the rest of the data safe?

Thanks for any help!

---

### Post by sciurus on 2005-12-26
What were you using to write to ext3 from Windows?

---

### Post by psyguy92 on 2005-12-26
[QUOTE=sciurus]What were you using to write to ext3 from Windows?[/QUOTE]

Ext2IFS v. 1.10a

I'm assuming a delayed write was the cause.  I'd like to delete the bad files, but am more concerned about drive and general data integrity on the external (ext3) drive.  Any ideas?

---

### Post by sciurus on 2005-12-26
If you know the details of how the filesystem was set up, you can use mke2fs -n with those settings to show you were the backup superblocks should be. Then you could start e2fsck -b addressOfSuperblock /device. I would use the -c flag to check for bad blocks.

---

### Post by psyguy92 on 2005-12-27
[QUOTE=sciurus]If you know the details of how the filesystem was set up, you can use mke2fs -n with those settings to show you were the backup superblocks should be. Then you could start e2fsck -b addressOfSuperblock /device. I would use the -c flag to check for bad blocks.[/QUOTE]

I used the 'Disks' program to format the disk ext3.  I don't know what you mean by 'how the filesystem was setup'.  I don't really know anything about superblocks. I'll google it. I'm a 100% newbie in this area :(

---

### Post by psyguy92 on 2005-12-27
Google resulted some info.  I'm wondering if this is accurate / safe to try?

Here's what I found:

The usual ( and only ) positions are: 8193, 32768, 98304, 163840, 229376 and 294912. ( 8193 in many cases only on older systems, 32768 is the most current position for the first backup )

You can check this out and have a lot more info about a particular partition you have on your HD by:

CODE
$ dumpe2fs /dev/hda5

You will see that the primary superblock is located at position 0, and the first backup on position 32768.

suppose you get a ¨Damaged Superblock¨ error message at filesystem check ( after a power failure ) and you get a root-prompt in a recovery console, then you give the command:

CODE
# e2fsck -b 32768 /dev/hda5

It will then check the filesystem with the information stored in that backup superblock and if the check was successful it will restore the backup to position 0.
Now imagine the backup at position 32768 was damaged too . . . then you just try again with the backup stored at position 98304, and 163840, and 229376 etc. etc. until you find an undamaged backup  ( there are five backups so if at least one of those five is okay it´s bingo ! )

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
This is a flash drive... correct? Flash drives are not very big, so just back it up to your hard drive and reformat it. That's the simplest way to fix the problem. (And I would suggest not writing to ext filesystems from windows.)

---

### Post by psyguy92 on 2005-12-27
> **&#1055 said:**
> This is a flash drive... correct? Flash drives are not very big, so just back it up to your hard drive and reformat it. That's the simplest way to fix the problem. (And I would suggest not writing to ext filesystems from windows.)

No, this is a 120 GB IDE drive in a USB case. 

That's 25 regular DVDs or so.  Or a gazillion CDs.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
Ah, that would be different.

You could try the backup superblocks and see how that works but you may lose data. I looked at the webpage for that software you're using and can't tell if it even  supports them or not.

I've personally found the safest way to access a windows hard drive from linux (and, especially, vice-versa) is via a network connection :)
 
Anyway, given that this is a mechanical drive I wouldn't jump to the conclusion that windows corrupted it. It's possible but it's also very possible the drive dropped some clusters and may lose more. Hard drives are cheap, I suggest getting another (even if it's just a loaner) and backing it up. Stick it in a desktop machine and run a comprehensive diagnostic on it using the manufacturer's boot cd. If it tests ok reformat it and restore the data.

---

### Post by psyguy92 on 2005-12-27
Thanks for the input.  I think it was windows that corrupted it, simply because the location of the bad files is within the folder that was being copied to the external drive when windows crashed.  Could be wrong though.

If restoring the superblocks seems risky, I'll probably not do that until I can buy another drive to backup.  I really don't understand it well enough to know how risky it is.

You mention accessing the drive as a network resource.  Can you do that with a drive connected to a single computer?  How is it safer to write to that drive if it is a network resource?  I assume you're talking about Samba here. *confused*

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-27
> Thanks for the input. I think it was windows that corrupted it, simply because the location of the bad files is within the folder that was being copied to the external drive when windows crashed.

My experience with windows it is it can be very flaky when operating with usb drives. Add this to the fact you are using a binary kernel driver not included with the operating system... now, how is windows going to behave when it sees a media error on that drive? There is simply no way to know - it's just as possible the media error was there all along and when you attempted to write to the bad cluster it caused the NT kernel to crash. 

After losing countless hours to screwing with data loss form hard drives, I am a firm believer in redundancy. I have my most hard to replace stuff on a 40gb drive sitting on my shelf and the main drive on my machine is a three disc RAID5. One hard drive in a machine is not a notion I will even consider any more - three drives (which still can cost as little as a hundred bucks if you shop well) is now what I consider a "base system." I know you didn't ask, but hard drive failures are pretty common  - there's at least three discussions started here a week that inevitably lead to someone having a dying hard drive.

It doesn't have to be an old drive to die, either. So far I am batting a thousand with the drives I've purchased in the last several years: 6 out of 6 drives (Maxtor and Seagate both) have died while under warranty and had to be replaced in the system. 

You cannot access the drive via a network using the same machine unless it supports virtualization, and present virtualization tech isn't deep enough to robustly segregate hardware at that level. What I meant was simply using an old or cheap low end pc running windows.

---

### Post by sciurus on 2005-12-27
I would try the backup superblocks. The worst thing I think can happen is you replace one bad superblock with another bad/invalid superblock.

---

### Post by MetalMusicAddict on 2005-12-28
Maybe try putting the drive physically in the PC if you can. Then test. Sometimes USB does funny things.

---

### Post by psyguy92 on 2005-12-28
Well superblocks are ok now and I was able to run a full e2fsck (it ran a second time on its own). I got a lot of invalid inodes notices and answered yes to dozens of prompts.  I'll not post the output as it's several pages long.  Basically, it's now clean.  Programs that read from the drive no longer act wierd (they were doing strange things when getting to the bad files).  I was able to delete the bad files.  Data loss isn't too bad - it's hard to estimate.  I've only found a few things so far, and nothing critical.  I do have some files in lost+found and have no idea what they are, if they're useful, or how to find out.  Guess I'll worry about that if I find that I'm missing something important.

I feel lucky.  It looked like every single bit was melting one by one.  They didn't.  I guess the lesson here is to get more drives and learn how to set up a RAID in case I'm not so lucky the next time!

Thanks for the input and help!

psyguy92

---

