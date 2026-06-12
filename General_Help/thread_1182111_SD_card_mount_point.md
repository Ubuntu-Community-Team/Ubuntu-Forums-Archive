---
title: "SD card mount point"
date: 2009-06-08
forum: General Help
---

### Post by ugm6hr on 2009-06-08
EDIT: Given how long this post is, I have summarised in post 2 below

On 9.04NBR on my Mini 9, I use an SD card (8GB SDHC) which is generally always in the memory card slot.

I had originally (when using the 8.04) reformatted to a single 8GB ext2 partition, and labelled it **sdhome**.  This meant that it always mounted at /media/sdhome on bootup.  I then created symlinks from my home directory to directories within the SD card, which made browsing the card as if it was part of my home directory much easier.  This all worked fine...

After a fresh install of 9.04, I copied back the original /home directory to preserve my emails and settings etc.

The only difference was that it now did not automount on bootup, and needed me to select either the media symbol sdhome, or one of the symlinks to the SD card within nautilus to mount it; after a single click, it worked as expected within any other application too.  Not as slick as with 8.04, but reasonable...

I never bothered editing fstab, cos I figured it was unnecessary, and I didn't want to cause problems if I ever booted up without the SD card inserted.

Yesterday, the SD card decided it was corrupted.  I'm afraid I (foolishly) didn't take full note of the error messages, but it was something related to a bad superblock.

I have since just reformatted the SD to ext3 (thinking perhaps ext2 is too unreliable), and named it **sdhome** again.  It appears to work just as before (although I have removed the symlinks), but now nautilus creates 2 separate media icons for **sdhome** (within the left-hand pane), one of which will work as expected (and changes from a HD symbol to an SD card when mounted), and the other which complains about "/dev/mmcblk0 already being mounted or /media/sdhome being busy".  Obviously, both of these errors are true...

My question is: what has changed in this situation to persuade nautilus to give the SD card 2 entries in the left hand pane?

Some further details:
1. Both entries disappear if I unmount and remove the SD card, and both reappear if I plug it in fresh.
2. I do not recall having made any fstab changes (and have checked - it is not listed).
3. I do not recall having made any udev changes.
4. If I relabel the SD card as **sd**, plugging it in still results in 2 entries, but 1 remains as sdhome; hence I suspect it is related to some persistence (or a change I have previously made).

I apologise if this sounds like I have no idea what is going on, but I have genuinely never encountered this before.

---

### Post by ugm6hr on 2009-06-09
To summarise:

My SD card (Sandisk 8BG SDHC, single ext3 partition) appears as 2 separate entries in the nautilus side pane, both as *sdhome.*

One works as expected, and the other errors.

The original error reappears if I try to mount the "wrong" sdhome before the new correct one:

> mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0, missing codepage or helper program, or other error


And dmesg:
```
[  195.589733] EXT2-fs error (device mmcblk0): ext2_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[  195.589759] EXT2-fs: group descriptors corrupted!
```

Full details above.

---

### Post by anjilslaire on 2009-06-09
I believe the left-hand entries in nautilus are 'bookmarks', I've had extra entries on my 9.04 UNR as well that I've had to remove, whwn creating samba links to my desktop machine.

Check Bookmarks in nautilus and see if you can delete/alter them to get rid of the unneeded sdhome.

Otherwise, I'm not sure what's going on.

---

### Post by ugm6hr on 2009-06-09
Thanks anjislaire.

But both sdhome entries appear *above the bookmarks line* (i.e. the are auto-detected as a drive / device).  I have only 2 bookmarks now - neither refers to sdhome.

---

### Post by anjilslaire on 2009-06-09
ah, gotcha. I assume you've checked fstab to make sure there's no errant entries? Run sudo mount -a & all the usuals?

That *is* strange...


EDIT: I see you have, oops. Have you tried right-clicking the broken entry in nautilus and selecting "Eject"? Perhaps that will remove it.

---

### Post by ugm6hr on 2009-06-09
My /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=329f6102-cd49-421b-a2c1-e4ed1f4d4a4c /               ext3    relatime,errors=remount-ro 0       1
```

As I said, I can't see anything unusual here.  Hence, I figure mount -a will not achieve anything.... but never tried.

Can't right-click and eject, since it only offers the "Mount" option (and Open options), which fails as explained above.

I agree.... Very strange.  I wonder whether it is actually a problem with the SD card itself.  I may try completely blanking the card with 0's, and reformating if no one else has any ideas.  Extremely bizarre how the SD card actually appears to work fine using the other sdhome link.

---

### Post by ugm6hr on 2009-07-19
Just used shred to wipe the MBR (sudo shred -vfz -n 1 /dev/mmcblk0
 then Ctrl+C after the first 5MB), then reformatted ext3.

Seems to be working as normal.

Very strange behaviour: still don't know what happened.

---

