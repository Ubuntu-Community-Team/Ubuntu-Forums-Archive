---
title: "&quot;Live&quot; USB can't install/use RAID or LVM?"
date: 2010-11-27
forum: Desktop Environments
---

### Post by Uberman on 2010-11-27
I've performed a search for this, and back to 2006, I could not find a post that specifically addressed this.

I have built an ITX system (Intel Atom) and will have 4TB (two 2TB Samsung Spinpoints) of storage installed on it.  Since the case is passively cooled, I don't want to get anymore hardware into the cabinet, so I'm attempting to run Ubuntu (10.10) from a USB drive (with persistence) instead of installing a third, OS-only HDD.

I'm finding, however, that I cannot get 'mdadm' or 'lvm2' to install onto the USB drive so that I can set up RAID 0 and/or LVM on the HDDs.  When I try, it looks like the process attempts to access "/vmlinuz" (to make the drivers install at boot time, I'm guessing), which is a broken link on the live image because it's a Casper image.  This leads to unavoidable installation failures, and I'm left without the ability to create/manage a RAID or logical volumes from the "live" USB.

It would seem like this would be a common action with "live" installs.  Am I missing some kind of step to get these features enabled on the "live" USB drive, or is it simply not possible with Ubuntu?  If it is the latter, does anybody know of a distribution that can run from a USB drive *and* provides this functionality?

Thanks for your help and insight.

---

### Post by d_morgan on 2010-12-03
I'm not sure if the setup I'm working on is the same but I can access logical volume from a Ubutnu live USB key.  I have one HDD at /dev/sda formated with ext4 without any lvm.  I have a second HDD at /dev/sdb setup with lvm (1 pv, 1 vg, 2 lv).  After I boot the live image i run
sudo apt-get install lvm2

If I activate the volume group I can then mount the drives in the GUI.

Does it fail for you when you install lvm2?

---

