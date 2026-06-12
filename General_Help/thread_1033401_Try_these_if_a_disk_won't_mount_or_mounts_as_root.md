---
title: "Try these if a disk won't mount or mounts as root"
date: 2009-01-07
forum: General Help
---

### Post by maestrobwh1 on 2009-01-07
I had this happen a few times and I frequently see posts on such matters so I figured I would offer some help with my 3 years of Ubuntu experience.  

>>Part A
One of the worst issues is when after an upgrade, your root partition mounts as read only. I guess the worst is that it won't mount and that is another topic you need to search help for.

There are a variety of issues that can cause the read-only mount, but mine that happened twice, I answered "n" to replace the file /etc/init.d/mountkernfs.sh and I later found out that I should have replaced this with the package maintainer's version. I could still get in to X in recovery mode, so I did that, found the /etc/init.d/mountkernfs.sh and renamed it

> 
sudo mv /etc/init.d/mountkernfs.sh /etc/init.d/mountkernfs.sh-old

and there was another file /etc/init.d/mountkernfs.sh-upgrade or something to that effect (can't remember, but it has the word upgrade attached to it), and I copied it as mountkernfs.sh, 

> sudo cp /etc/init.d/mountkernfs.sh-"whatever it is called" /etc/init.d/mountkernfs.sh


I purged virtualbox for good measure, rebooted and it worked.  I reinstalled virtualbox.

>>Part B
**Other minor mounting issues not with root partition:**

I first made sure I was a member of the group "storage"  I used 

kdesudo kuser

but if you have gnome, you will have to use the command 

gksudo "whatever the user program is called" or it might be in the menu and will ask you for the root password when launched.

This worked once because somehow, I was was bumped out of the "storage" group so I just added myself again.

>>Part C
AS A NOTE
Unlabeled volumes mount as "disk" and I find this bad in the long run and you should fix that and give every partition and disk you own a unique label, that way you can avoid a lot of confusion about what is where and what it mounts as in Ubuntu.  If not, disks will mount as disk, disk1, etc and that is confusing.

Some oddball things you can try for **removable** disks that can only be mounted as root:
1. find out what name the disk is assigned in /media/ when you mount it as root then unmount it.  

i.e. disk mounts as MYDISK and *_if MYDISK persists in /media/_*, do
> sudo chmod 777 -R /media/MYDISK
Plug the disk back in and see if you have access.  
No?
Unmount the disk again, do exactly the same thing, and chmod it with the command, then DELETE THE FOLDER IT MOUNTS TO in /media/

I don't suggest running a chmod  as root with a disk mounted.  It will take forever and it may cause a whole lot of permission issues.  

No? Mount it again:

2. Give the disk a different name

> sudo e2label /dev/sdX NEWLABEL for ext3 and ext2

sudo mlabel -i /dev/sdX ::NEWLABEL (for vfat 16 and 32, and you'll have to make sure mtools is installed)

sudo ntfslabel /dev/sdX NEWLABEL (and make sure you have ntfstools installed)

Plug the disk back in.  
No?  I can't help you anymore:-(  Something is amuck and I have no idea what it is.

**If there is an issue with NTFS being unmounted improperly once, it frequently refuses to mount in Linux.  You can use the force option, but you are on your own if you do that and I am not listing it here as something to do, and try not to write to the partition if you do this.  If ntfsprogs is installed, the command "ntfsfix" can help as well with that in Linux.  Might be better to plug it into a windows box and run a disk check.**

>>Part D
Another time, when I upgraded, I just had all sorts of issues :

The only way I fixed it was to rebuild my fstab

> sudo cp /etc/fstab /etc/fstab.old

> sudo blkid -c /dev/null

in another terminal

> sudo nano /etc/fstab  (you can use a graphical editor as well, but I have finally gotten use to the quicker nano editor)

then in the side by side terminals:

In fstab, I very carefully checked every fstab line UUID entry against every item output by blkid (make sure they match and to what mount point you want).  I found I had to change a few things.  I fixed it and rebooted and I had access.

If this isn't the case and that all seems okay, and it wasn't when I had an issue once:

I googled for the very basic need for fstab options for each partition type, added in those and then 0 0 for the last columns (except the root partition)

i.e.
> 
UUID=CA50687D506871DD 	/media/DATA	ntfs-3g	defaults,auto,noatime	0	0

I rebooted and I had access.

Best of luck.  Frustrating.

---

