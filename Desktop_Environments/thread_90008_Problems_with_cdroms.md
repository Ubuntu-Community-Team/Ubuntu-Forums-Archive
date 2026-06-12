---
title: "Problems with cdroms"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Pixel on 2005-11-14
Ever since I've installed I've been having this problem.

If I log into gnome, and put a CD in, it shows the cd fine and put the link on the desktop for it, and if I go to the administration -> disks it shows them mounted on /dev/hdc and /dev/hdd.

Now the problem is when I want to access these drives from anything other than my desktop.

My fstab shows /dev/hdc is mounting on /mnt/cdrom and /dev/hdd is mounting on /mnt/cdrom1, but if I try to mount any of these drives it says this:

<code>
kyager@terra:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
</code>

and even when gnome will show the icon on the desktop AND play music or whatever is on the CD perfectly fine, if I try to ls that directory it shows nothing.

This is really starting to confuse me...

Any idea whats wrong?

---

