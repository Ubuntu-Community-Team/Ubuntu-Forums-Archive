---
title: "Help needed URGENTLY"
date: 2009-02-22
forum: General Help
---

### Post by Dj-Tempo on 2009-02-22
Hi all im a total newbie to Ubuntu & I've just recently installed Ubuntu 7.04  using the live CD i was given a while back...

My main issue is I only installed this to try and reinstall windows XP using my USB stick (U3 1GB stick) after my pervious xp install died on me :(

Everything was going fine earlier & my usb stick was letting me paste the files from my friends CD so i could install... I since found out i missed a few files (after rebooting and XP failing to load) but now everytime i go into the USB device it says I am the owner and I am allowed to read & write but it doesn't let me delete anything instead it just says permission denied :S

I really need to know (in simple terms) how to get rid of this data on my stick and put the correct data back onto my stick so i can reinstall XP again

I also dont have access to the CD drive anymore its since packed up on me but i do however have the files for XP install...

(Also just to note the USB stick ISNT corrupt it still shows correct data and all the right file sizes)

---

### Post by Ericyzfr1 on 2009-02-22
All this sounds confusing...You are trying to install XP with a USB stick...copying files from another PC?  It does not sound like a good way to install XP...I may be wrong...or I clearly did not understand the situation...

---

### Post by Dj-Tempo on 2009-02-22
> **Ericyzfr1 said:**
> All this sounds confusing...You are trying to install XP with a USB stick...copying files from another PC?  It does not sound like a good way to install XP...I may be wrong...or I clearly did not understand the situation...

Lol sorry... My friend let me borrow his windows XP disk, from which i put into my machine in order to load the files (from the CD) onto my USB Stick, & yes i know i should have just installed from the CD but he was in a rush and wanted his cd back :( Anyway now as I have the files on my USB stick they are in the wrong order and I am missing a couple of files which are still on my desktop to where i originally ripped them too but not on my USB drive... Now the drive isnt letting me write / copy / delete anything from it and i dont understand why or how to fix it... I hope this clarified the situation :)

---

### Post by sandyd on 2009-02-22
> **Dj-Tempo said:**
> Lol sorry... My friend let me borrow his windows XP disk, from which i put into my machine in order to load the files (from the CD) onto my USB Stick, & yes i know i should have just installed from the CD but he was in a rush and wanted his cd back :( Anyway now as I have the files on my USB stick they are in the wrong order and I am missing a couple of files which are still on my desktop to where i originally ripped them too but not on my USB drive... Now the drive isnt letting me write / copy / delete anything from it and i dont understand why or how to fix it... I hope this clarified the situation :)
i smelll something wrong already.

to boot from a cd, usb, or other removable media, your device **must** have a boot sector. copying files from the winxp cd doesn't copy the boot sector.
if you have a floppy drive, and floppies, thats ok, you can download the setup from microsoft

search setup boot disks in google.

---

### Post by Dj-Tempo on 2009-02-22
> **carlee said:**
> i smelll something wrong already.

to boot from a cd, usb, or other removable media, your device **must** have a boot sector. copying files from the winxp cd doesn't copy the boot sector.
if you have a floppy drive, and floppies, thats ok, you can download the setup from microsoft

search setup boot disks in google.

The drive does have boot sectors as i used USB Multiboot Tool as seen on this youtube [video]("http://www.youtube.com/watch?v=2Vt_8p0VllY") since then i used cfdisk to try and format the USB stick, it seems to have formatted but now it just says... "Unable to mount media. There is probably no media in the drive" I dont know if im closer to solving the problem or just digging myself a deeper grave, all i really wanna do is wipe the drive then re-put the files back onto it...

---

### Post by prinny42 on 2009-02-22
Ah, cfdisk doesn't format the drive itself; it just edits partitions.  Formatting shouldn't be too hard, but first, would you rather fat32 or ntfs (or something else)?

Also, since you used cfdisk, I presume you already know the /dev/(whatever) name of the drive?

---

### Post by Mercury_Alpha on 2009-02-22
Installing Windows from a USB stick can be done, but [it's a pretty complicated process]("http://www.vandomburg.net/installing-windows-xp-from-usb/"). If the USB stick "environment" is not set up very specifically, with help from a pre-existing, accessible Windows desktop, it's going to be pretty rough.

---

### Post by bgates on 2009-02-22
Also, not to be confrontational or anything, but isn't this Windows support?  What, if anything, is broken in Ubuntu?  Windows is a commercial software with support options.  Assuming this is licensed.  If you are trying to install your friend's OEM Windows CD to your computer, it probably won't work and isn't licensed.

---

### Post by Dj-Tempo on 2009-02-22
> **prinny42 said:**
> Ah, cfdisk doesn't format the drive itself; it just edits partitions.  Formatting shouldn't be too hard, but first, would you rather fat32 or ntfs (or something else)?

Also, since you used cfdisk, I presume you already know the /dev/(whatever) name of the drive?

Yeh it turned out to be /dev/sdb and im only looking for a fat32 format, I deleted the partition which was already in there and now I just want to return it too normal (as the stick was when i bought it) i hope you can shed some light on this as its getting to the point of dier frustration at the moment... Thanks

Also for the notice of "bgates" the CD is a retail version       & I posted it here as I'm currently using ubuntu 7.04 fiesty dawn (or w,e, its called) and don't understand any of the commands let alone how to reformat my USB that ubuntu seamingly broke...

---

### Post by prinny42 on 2009-02-22
Alright, after you deleted the partition did you put a new partition on there (so there's at least one)?  If not, do so.

Know now that I haven't actually done this before (I've only ever formatted to ext3), but I'm pretty sure this is right.  First make sure that your drive is unmounted.  Formatting it should just take one command:
```
sudo mkdosfs -vF 32 /dev/sdb
```

When it next mounts, try putting something on it to see if you get a permissions error.  If you do, I'm not sure if this is the best way to do it, but this is how I work around it.  Just change the owner of the file it mounts to from root to you.  You can do this with this command:
```
sudo chown (Your Username) (Folder Drive Is Mounted To)
```

---

### Post by Mercury_Alpha on 2009-02-22
Ubuntu didn't break your USB stick. You have to set access permissions on any external drive that you attach. That's why it's saying "permission denied." This is a security layer built into Linux, to protect the system against unauthorized access or manipulation.

Also, making a copy of someone *else's* Windows CD to install on your computer is piracy. I'm not judging -- I'm saying that assisting you is assisting piracy, and that gets this forum into trouble.

---

### Post by Dj-Tempo on 2009-02-22
> **prinny42 said:**
> Alright, after you deleted the partition did you put a new partition on there (so there's at least one)?  If not, do so.

Know now that I haven't actually done this before (I've only ever formatted to ext3), but I'm pretty sure this is right.  First make sure that your drive is unmounted.  Formatting it should just take one command:
```
sudo mkdosfs -vF 32 /dev/sdb
```

When it next mounts, try putting something on it to see if you get a permissions error.  If you do, I'm not sure if this is the best way to do it, but this is how I work around it.  Just change the owner of the file it mounts to from root to you.  You can do this with this command:
```
sudo chown (Your Username) (Folder Drive Is Mounted To)
```

Thanks for the tip Prinny however after entering that code I was faced wit this error...

```
tempo@tempo-desktop:~$ sudo mkdosfs -vF 32 /dev/sdb
Password: *MYPASS*
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: Will not try to make filesystem on full-disk device '/dev/sdb' (use -I if wanted)
tempo@tempo-desktop:~$
```

I then typed fdisk to see what the issue was and was faced with this...

```
tempo@tempo-desktop:~$ fdisk -l

Disk /dev/sdb: 1004 MB, 1004060160 bytes
31 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 1922 * 512 = 984064 bytes

   Device Boot      Start         End      Blocks   Id  System
tempo@tempo-desktop:~$ sudo mkdosfs -vI 32 /dev/sdb
mkdosfs 2.11 (12 Mar 2005)
32: No such file or directory
tempo@tempo-desktop:~$ sudo mkdosfs -vfI 32 /dev/sdb
mkdosfs 2.11 (12 Mar 2005)
Bad number of FATs : I
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]
tempo@tempo-desktop:~$
```

None of the above makes sense to me I hope it sheds some light with one of you better experienced "linuxers" lol :)

Also for attention of the "piracy" message, If i legally own a product key for the same disk my friend let me use (due to the fact my own disk was scratched beyond readability) this is not classed as an act of piracy.

---

### Post by cariboo on 2009-02-22
Why not borrow the CD from your friend and create an iso of the cd, it take a lot less time and agravation. Make sure he cd isn't mounted then open a terminal and type:

```
sudo if=/dev/scd0 of=windows_xp.iso 
```

Then if you can find a copy of Intrepid you can use System-->Administraion-->USB Startup Disk Creator to transfer your iso to your usb device.

Jim

---

### Post by bgates on 2009-02-22
> **Dj-Tempo said:**
> Also for attention of the "piracy" message, If i legally own a product key for the same disk my friend let me use (due to the fact my own disk was scratched beyond readability) this is not classed as an act of piracy.


That is only true if both you and your friend have purchased full retail versions.  If his CD was OEM, you are not licensed to install it, and it probably won't work for technical reasons also.

---

### Post by Dj-Tempo on 2009-02-22
They was both bought at thesame time, Infact im the one that bought him the disk when i bought myself one (came across a deal when xp was first released, buy one get one half price) so yes they are both legal versions of XP Home Retail edition, however the problem at hand is the usb stick refusing to open , format and generally work not wether or not i legally own an xp license which also coresponds to my friend's cd... However I do understandwhere your coming from & thank you. I just hope I can get round this main issue of the stick...

---

### Post by prinny42 on 2009-02-23
Okay, it looks like something is wrong with the partitioning of your USB stick, so let's take it from the top.  I've managed to get my hands on a spare USB stick, so I just did this and it works.

Make sure that it's still /dev/sdb and
```
sudo cfdisk /dev/sdb
```

Once you're in cfdisk, hit [d] to delete the existing partition (if it complains about empty partitions and won't let you delete, just go down one and then hit [d]).  Then, hit [n] to create a new partition (go with primary when it offers, and it should offer you a reasonable default size), and hit [t] to change its type.  Type 0C (that's zero, capital C) to go with W95 FAT32 LBA.  Now hit [W] (and it has to be a capital W) and tell it yes to write the partition.  Once that's done, hit [q] to exit.

Now all that's left is to format it.  Make sure the stick is still unmounted.  The command I gave you earlier should work, but make sure to include the partition number (the number at the end of /dev/sdb).
```
sudo mkdosfs -vF 32 /dev/sdb1
```

If the stick doesn't automount after that, unplug it and plug it back in.  It should mount.  You might get a permissions error when trying to write to it, but if so, I've already described how to fix that.

And you should be done.  By the way, take note that Linux is case-sensitive (in one of your attempts with mkdosfs you changed -F to -f, but that might have just been a typo).  Also, the -F specifies the FAT size, so the 32 needs to come right after it.

Let us know how it goes.

---

### Post by Dj-Tempo on 2009-02-23
> **prinny42 said:**
> Okay, it looks like something is wrong with the partitioning of your USB stick, so let's take it from the top.  I've managed to get my hands on a spare USB stick, so I just did this and it works.

Make sure that it's still /dev/sdb and
```
sudo cfdisk /dev/sdb
```

Once you're in cfdisk, hit [d] to delete the existing partition (if it complains about empty partitions and won't let you delete, just go down one and then hit [d]).  Then, hit [n] to create a new partition (go with primary when it offers, and it should offer you a reasonable default size), and hit [t] to change its type.  Type 0C (that's zero, capital C) to go with W95 FAT32 LBA.  Now hit [W] (and it has to be a capital W) and tell it yes to write the partition.  Once that's done, hit [q] to exit.

Now all that's left is to format it.  Make sure the stick is still unmounted.  The command I gave you earlier should work, but make sure to include the partition number (the number at the end of /dev/sdb).
```
sudo mkdosfs -vF 32 /dev/sdb1
```

If the stick doesn't automount after that, unplug it and plug it back in.  It should mount.  You might get a permissions error when trying to write to it, but if so, I've already described how to fix that.

And you should be done.  By the way, take note that Linux is case-sensitive (in one of your attempts with mkdosfs you changed -F to -f, but that might have just been a typo).  Also, the -F specifies the FAT size, so the 32 needs to come right after it.

Let us know how it goes.

OMG your a genious, lol

All worked perfectly, auto mounted, and didnt ask for permissions amazing really as after taking it to a hardware shop (The USB Key) they tried to format in windows and it said "This disk cannot be formatted" and basically that its been corrupted, how wrong they where, :D

Anyway thanks for your help dude youv'e made an old DJ very happy (Oh and sorry if this sounds like im takin liberties but I downloaded a few Virtual Machines earlier one being VMWare workstation and the other VirtualBox and they both say stuff like "libc isnt dependable / satisfiable :S) 

Many thanks again to all of you :D

---

