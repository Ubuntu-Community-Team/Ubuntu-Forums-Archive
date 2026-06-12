---
title: "Merge hda2 + hda4, easy ??"
date: 2005-12-14
forum: Desktop Environments
---

### Post by _jB on 2005-12-14
Hey..
Planning on getting another hd to use as /home (99% full :P).
Right now root and home are on the same disk (hda2 / hda4), so when I've copied /home to the new hd and remounted it, I would like to merge hda2 and hda4 into a single partition.
Can qtparted do this without any problems ?

**my plan** :)
[LIST=1]
[*] copy /home => /new_disc and remount /new_disc as /home
[*] backup / => /new_disc/root_backup.tar (using [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087))
[*] merge hda2 and hda4
[*] restore / from /new_disc/root_backup.tar
[/LIST]

Mayby I'm mistaken, but I seem to recal that I have to unmount drives before qtparted can edit/format/whatever ??
If this is so, the question is, can I unmount / will in use or do I have to boot from a livecd to do this ?

***If anyone has an easier way / hints / a.s.o, please let me know, I've done this before :)***

---

### Post by Gandalf on 2005-12-14
to unmount / you need to do it via livecd, but i'm not sure if u can merge them without breaking ur system :roll:

---

### Post by psusi on 2005-12-14
If you formatted the original partition with LVM, then it should be fairly simple.  If not, it's a bit more complex.  

Will the two drives be exactly the same?  If so then you might want to make them into a raid0 volume.  

Your best bet is to back up your entire system, then use a livecd to repartition, then restore.  

And you don't want to copy files to the new drive first, it has to be empty to add it to an lvm volume group ( or rather, anything on it when you do will be lost ).

---

### Post by _jB on 2005-12-14
> to unmount / you need to do it via livecd, but i'm not sure if u can merge them without breaking ur system
Hence the backup :)

@**psusi**
Nope, no raid. My hda is a 80gig ata133, the new drive will be 350 segate sata.
I've heard misc things about having /home on a seperate partition, but I like it (sofare :)). So it's just a simple, move data > merge (wipe) root and reSetup the root.

Edit fstab to use /home > sdX instead of hda4, will do the trick right ?

---

### Post by daller on 2005-12-14
I'd do it with a livecd, and install gparted!

Good Luck!

---

### Post by _jB on 2005-12-14
[QUOTE=daller]I'd do it with a livecd, and install gparted![/QUOTE]
Oki, think I have a bunch of those somewhere ;)

But otherwise **my plan** is oki ?

---

### Post by daller on 2005-12-14
[QUOTE=_jB]Oki, think I have a bunch of those somewhere ;)

But otherwise **my plan** is oki ?[/QUOTE]

Oh sorry, I misread the thread! - I though you just wanted to merge two partitions... I don't know if gparted is capable of that!

...I would give it a try if I where you! (Just make sure to backup properly)

Hah! your "oki", made me think of you as a Dane! - And I was right! IMO "Location: Copenhagen" would be better! :D

---

### Post by _jB on 2005-12-14
dk_2300 IS copenhagen :)
I'll just try the backup-howto, and see how it works out. A system-reinstall isn't that bad, but I would rather not have to do it ;)

---

### Post by afhp on 2005-12-14
Instead of merging the partitions on hda, you could also simply use the old /home for something else (/var, for instance) -- go to single mode or boot from livecd, move stuff around, edit fstab accordingly and you should be set.

Personally, I prefer having separate partitions for everything (/, /boot, /usr, /var, /home, /usr/local) but to each his/her own.

---

### Post by psusi on 2005-12-14
You don't have a seperate /home partition already do you?  If not, then yes, the easiest thing to do is probably to just move /home to the new drive, then mount the new drive in /home.  

To do that you might want to boot into rescue mode, mount the new drive, say in /mnt, then mv /home/* /mnt.  Then umount /mnt, and add the line to fstab to mount the drive in /home and reboot.

---

### Post by _jB on 2005-12-14
Yes / and /home are seperated.
/ - 12 gb (hda2)
/home - 9 gb (hda4)

---

### Post by _jB on 2005-12-14
[QUOTE=afhp]Instead of merging the partitions on hda, you could also simply use the old /home for something else (/var, for instance) -- go to single mode or boot from livecd, move stuff around, edit fstab accordingly and you should be set.[/QUOTE]

Yes, thats another option.
Right now I have
[list=1]
[*]/ ~ Size 12 GB / Free 7303 MB
[*]/home ~ Size 9853 MB / Free 142 MB
[/list]
For now / isn't in size-trouble yet, but isn't 9gb alot for /var ?

Could I leave hda4 @ 9gb and then mount
/var /hda4/var
/stuff /hda4/stuff
a.s.o instead and  ? And what /?? should/could I move there ?

---

### Post by psusi on 2005-12-14
I wouldn't bother messing with /var.  Out of curiocity, what is the rest of the space on hda used for?  You said it was 80 gigs but / and /home only account for 20 gigs.  

I'd do this:  boot into rescue mode and

mount new disk in /mnt
cp -a /home/* /mnt
umount /mnt
umount /home
edit fstab and change the /home to point to the new drive
reboot

If all goes well, your /home will be on the new drive.  Then you can boot off the livecd, fire up gparted, blow away the old /home partition on the old drive, and resize the / partition to use the space.

---

### Post by _jB on 2005-12-14
Oh, sorry, hda is only 40gb. My 80gb is in my ps2.
The other 15-20gb er win2000 (yes yes i know :P)

> If all goes well, your /home will be on the new drive. Then you can boot off the livecd, fire up gparted, blow away the old /home partition on the old drive, and resize the / partition to use the space.
Oki, I'll try that.

Just haven't heard anyone say "sure, resize with qtparted, you won't lose a bit".
Better just backup to be 100% safe :)

---

### Post by psusi on 2005-12-14
Of course you should allways have backups, but from what I have seen, there is little risk of data loss.  I certainly have more faith in gparted or the command line resize tools than I do in partition magic.  

[QUOTE=_jB]Oh, sorry, hda is only 40gb. My 80gb is in my ps2.
The other 15-20gb er win2000 (yes yes i know :P)


Oki, I'll try that.

Just haven't heard anyone say "sure, resize with qtparted, you won't lose a bit".
Better just backup to be 100% safe :)[/QUOTE]

---

### Post by _jB on 2005-12-23
/home moved, first try, no problems at all. Without reboot:D

**thx** for the help, now back to *my plan* for the root-disk :)

---

