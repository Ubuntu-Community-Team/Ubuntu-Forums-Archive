---
title: "A little guidance with USB external HDD"
date: 2008-12-20
forum: General Help
---

### Post by Bartender on 2008-12-20
I know, there are lots of posts on this, but I'm not getting it.

I put together an external HDD, using an Antec MX-1 and a Samsung 400 GB SpinPoint.  The MX-1 supports e-SATA but I'm using the USB port for now.
Using a GParted/Clonezilla LiveCD, was able to format the Samsung to one primary ext3 partition.
With Ubuntu 8.04 up, I plug in the external and turn it on.  Get an icon on the desktop.  The drive shows one folder, "lost and found".

But I can't do anything with it.

It's recognized as /dev/sdb, the partition is /dev/sdb1.  If I go into "Properties" it has a UUID, etc. but on the "Permissions" tab it says "unable to determine permissions".

My goal is to use the MX-1 a few times a month for backups.  I'd like an icon when it's plugged in.  I know I need to make an entry into fstab. But don't know what it should be.

---

### Post by taurus on 2008-12-20
If you know the mount point of that drive, you can change the ownership of it from root to your login name so you can write to it.

Assuming it's mounted to /media/backup and your login name is beer, you could do something like

```
sudo chown -R beer:beer /media/backup
ls -la /media
```

---

### Post by Bartender on 2008-12-20
Right now it's mounting at /media/disk

I don't know if there are good reasons to move it?

So if I follow your lead, I would type in 

```
sudo chown -R bpbar:bpbar /media/disk
ls -la /media
```

And that's it?  
No entries into fstab, or manual mounting, etc.?

I'm still intimidated by terminal - not because I can't type something in, but because I don't know where the changes go and don't know how to fix/revert to previous if it doesn't work...

---

### Post by Bartender on 2008-12-20
I'm on dial-up :(
Want to add a quick screenshot.  This from right-clicking on the drive icon at desktop, going in to Properties, Volume

taurus, I want to get a picture in my head of how you see this - what you're saying is;
 
Don't mess with fstab, which controls devices mounted at boot 
Don't mess with mount point
Don't screw around with UUID, or any of that stuff

Just leave everything as it was originally detected and move ownership of that device to me??

---

### Post by taurus on 2008-12-20
You can leave your /dev/sdb1 where it is, /media/disk (default mount point for automount), or you can mount it somewhere else if you wish.  Assuming you want to remove it to /media/backup, you could do something like these from a terminal.

```
sudo umount /dev/sdb1
sudo mkdir /media/backup
sudo mount -t ext3 /dev/sdb1 /media/backup
sudo chown -R bpbar:bpbar /media/backup
ls -la /media
```
And when you want to remove that drive, unmount it first with

```
sudo umount /media/backup
-or
sudo umount /dev/sdb1
df -h
```

---

### Post by Bartender on 2008-12-20
OK, thanks, taurus -
I'm gonna try it.

EDIT:
It worked!
I moved some DVD rips to the external.  Got a funny error message the very first time, but after that it worked fine.
I tried clicking on the desktop icon and unmounting the volume.  Got an error message that indicated since I'd manually mounted the volume it wasn't in HAL and couldn't unmount.

So the way you had me set it up I need to manually unmount each time like you described in post #5?  I prefer the GUI but if I *have* to use the CLI I *guess* I can live with that :)

What happens when I plug the thing in?  

I'll umount, turn off the external, and turn it back on.  See what happens

EDIT AGAIN:
taurus, many thanks -

I umounted, turned off the external, waited a few seconds, turned it back on.  Icon appears on the desktop and it appears that I have full access to the device.

---

### Post by Silent Warrior on 2008-12-20
Although not, I suppose the same thing - the drives I want to mount at boot are internal, no backup of any sort - but suppose I uncomment the last two lines I hacked into fstab and boot, what would happen?

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=36773081-fb28-4620-a7a7-a43ae71fbcd3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=7d29acd8-8410-4775-9952-a101b2fff67b /home           ext3    relatime        0       2
# /dev/sda5
UUID=2421e8e1-6de1-40f2-ad1d-f42253ef8a75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#/dev/sdb1	/media/sdb1	ntfs user,noauto,exec

#/dev/sda1	/media/sda1	ntfs user,noauto,exec
```

I have a lot of stuff on the other two drives - my Windows life - including some music I'd like to listen to. If this isn't kosher, how do I manage this stupendous feat?

---

### Post by Bartender on 2008-12-20
silent -
Any lines that are commented out with the # will be ignored.  sda1 is already in the upper half of your fstab, with a UUID and everything.  I'm not very good with fstab but don't see why you'd want a second entry for sda1 at the bottom.
Take a good look at aysiu's guide 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
and notice that the first guide ends with a link 
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
that explains manually editing fstab

---

### Post by Silent Warrior on 2008-12-20
Bartender: Funny thing, really. Ubuntu is installed (root, home and swap) on an IDE-drive (should be hda or summat??), and the other two drives are SATA. When I mount the drives through Nautilus - which works, but I'd rather not have to do that and rescan my collection in Amarok every time - and check the drive-properties, they are listed as sda-c, with the Ubuntu-drive actually being sdc (which is probably why GRUB doesn't always approve of starting my computer)... sda-b being my two NTFS-drives, that is. (What can I say? X-Plane + Global scenery wouldn't fit along with the mothers of all bloat-ware: Neverwinter Nights 1 + expansions, Neverwinter Nights 2, and MSFSX.)

Presently checking Psychocat's guide. Looks like grade-A stuff, that.

Well, what do you know? That did it for the NTFS-drives. Stellar! Now there's just the little matter of the accidental extra partition I had to make on the Ubuntu-drive when my home-space dwindled faster than the root-partition... (hda4/sdc4, whatever...) Should I just copy a working ext3-entry in fstab and modify it to point at this partition?

---

### Post by Bartender on 2009-06-11
OK, guys and gals, looking for some input here...

I haven't done anything with the external for a bit.  Yesterday I plugged it in and got a desktop icon, plus a window showing folders on the external.

Just for the heck of it, when I wanted to turn it off, I right-clicked on the icon, and "Unmount Volume" was listed as an option.  The external unmounted without a hitch.

I didn't have to use the terminal as described in earlier posts.

The OS is still 8.04.  There was a kernel update recently.  Perhaps the latest kernel update makes mounting/unmounting external HDD's more convenient?

---

