---
title: "USB Drive Now Read only"
date: 2008-12-23
forum: General Help
---

### Post by rwigle on 2008-12-23
After working most of the day, my USB drive (KNGSTON) started acting up. I was unable to write to it, or delete files. Some files appear to have been corrupted. I have seen a few similar threads, and none ends well.

Following have not worked:

i) chmod on files or folders, no matter what (says file system read only)
ii) chown (same error, but many many times over)
iii) tried to remount, but this generated the same error repeatedly.

iv) Places => KINGSTON (use visual interface to change permissions etc) won't let me. File system is identified as read only.

I tried unmounting and remounting as read-write. Same problem.

Following is the output of sudo blkid

```

/dev/sda1: UUID="c5b5a0b6-21a5-4f0d-9888-d764052e06c2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="97fa01ad-3394-48b9-b0a1-ddfea653e2ed" 
/dev/sdb1: LABEL="KINGSTON" UUID="9D37-FBCA" TYPE="vfat" 

```

Hardy Heron.

Tried: 

```

sudo dosfsck -a /dev/sdb1

```

 (fixes a few errors, but still system is identified as read-only)

Help....

---

### Post by Hangwire on 2008-12-23
Bump, have the same problem with my MP3 Player.
Didnt find a solution really.

---

### Post by spirou on 2008-12-24
Same problem here with an external card reader.
Solution: Start gparted and reformat the card.
But I don't want to do this everytime I want to change some files.

---

### Post by rwigle on 2008-12-29
Hmmm, I have been thinking about this, and I wonder if we have discovered a feature (versus a bug).

In my case. what I think happened is that there was a write failure on my USB drive. So some subsystem that I can't name decides to save me from trashing all my data by continuing to work on it. It freezes the drive to get my attention (it does!).

OK, suppose that's right.....

My question is whether to reformat that 8GB Kingston Traveler USB drive or toss it and get a new one. The drive gets a lot of read/write cycles. I am toying with leaving a machine going in my office and using unison.

Comments/suggestions invited..

P.S. Thank heaven, I did a backup that very morning.

---

### Post by rwigle on 2008-12-29
Hmm, followed another post's suggestion and booted Windows XP on another box. Loaded the USB drive and then did safe removal.

Result: USB drive is reading writing OK, but I am still wondering if it is time to trash the USB drive as a precaution. (Any views on that?)

---

### Post by Cornbreadly on 2008-12-29
The same thing is happening to me.  I have family over from the holiday and I am getting ready to send my nieces home with an old laptop (opensuse) to manage their generic mp3 players and music collection.

Only now their MP3 players on both systems (my ubuntu and clean opensuse install) both register as read only.

Im at a lose... cant the system reclaim read/write access on anything connected?  Really, why does a cheap mp3 player foil sudo or su?  I can wipe everything on them and try again but i need these mp3 players to work... A circle of hell is providing tech support to 7-10 year old girls.

---

### Post by Cornbreadly on 2008-12-29
i have some new info:

It is a fat16 file system.  The mp3 player was designed to work with only WMP 10 or 11.  

Would that explain why I was only able to write to it once before everything was locked up?  Did I trip something that disabled the drive?

I reformatted one of the players(back to fat16) to start from scratch... that didn't really work.  Now I have a blank mp3 player that I can't write too.

I followed this [howto]("http://ubuntuforums.org/showthread.php?t=990287&highlight=fat+16+mounts+read") to get everything mounted as read/ write but when I tried it said it was read only.

Please help... I am a bad uncle.

---

### Post by Bramkaandorp on 2009-01-04
I have the same problem with my mp3 player. I recognise the symptoms.

Read-only.
Sudo doesn't help.
It works fine in Windows xp, although I just shut down the system, in stead of safe removal first(this was 2 days after the problem, so it is not the cause). I do not know if safe removal will help, but I will try tomorrow.

However, my mp3 player is a fat32 system.

I have tried pysdm(Python Storage Device Manager) to no avail.

If anyone has a solution, please help.

Thanks.

By the way, it is on both my laptop(eeebuntu), and my desktop(ubuntu intrepid), but(as I said),not on windows xp. So it is a problem on the mp3 player, not the system(or it is on ALL ubuntu systems, maybe all linux systems).

Cheers,

Bram

---

### Post by rwigle on 2009-01-08
This is not really a resolution, but confirms that it is probably caused by a write error on the drive.

[https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only](https://help.ubuntu.com/community/Mount/USB#Device%20become%20suddenly%20read%20only)

---

### Post by ddigler on 2009-03-03
Exact same prob hear w/ both my USB drives (mp3 player and 8GB pen drive). 

To get mp3 player to work (initially) had to reformat FAT32. Worked like a charm for a few days and then out of nowhere its 'read only file system' now. Never had these probs with Windows; find it hard to believe that both my mp3 player and pen drive need to be replaced. 

My pen drive seems to work but permissions are whacked. Was going to wipe it but after realizing that it wasn't a permanent fix for the player am going to wait. 

How are you guys handling these issues?

---

### Post by James- on 2009-03-03
> **rwigle said:**
> Hmm, followed another post's suggestion and booted Windows XP on another box. Loaded the USB drive and then did safe removal.

Result: USB drive is reading writing OK, but I am still wondering if it is time to trash the USB drive as a precaution. (Any views on that?)

yeah I had that happen to a USB key when I unplugged it from windows and plugged it into a linux box... Windows sort of corrupts the drive while mounting it and uncorrupts it when dismount...always best to safely remove sotrage devices

---

### Post by Rallg on 2009-03-03
Happened to me, once recently. I copied out my stuff from the USB, then used Partition Editor to re-work the USB, completely (even giving it a new drive label). Put the files back, all good. However, you could not do that for an mp3 player!

---

### Post by ddigler on 2009-03-04
To followup, reformatted both drives (mp3 and 8gb pen) last night (fat32). Both are functioning properly. I have not been using the safe removal unmount on either windows or ubuntu. Will start using.

Only time will tell. Will report back...

---

### Post by shateredsoul on 2009-03-04
I had t he same issue with my ipod and sandisk e200 (which I thought you could reformat like a normal drive! doh!).  It would be nice if the next release addressed this issue. There should be a way to right click and change permissions as root (i copied my files over on a fresh install of ubuntu and they all were read only... what the ?) M

---

### Post by lemonbar on 2009-03-07
This thread has helped so much!  I've been having this problem as well, posted about it a couple of times, and while trying to fix the "read-only" problem, I fixed it so the device wouldn't mount at all. Renaming the disk (I referred to ["Rename USB Drive - FAT16 and FAT 32]("https://help.ubuntu.com/community/RenameUSBDrive#FAT16%20and%20FAT32")" helped - I had to reset the player before it worked, but now it mounts, and when it did I think I scared my neighbors with my "Wooooo!!!!"  It's still "Read Only" but I feel a bit better about this all working out. Anyway, so glad this exists.:guitar:

---

