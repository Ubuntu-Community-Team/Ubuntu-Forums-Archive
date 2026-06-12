---
title: "owner/permissions of auto mounted removable media"
date: 2006-01-09
forum: General Help
---

### Post by Kirk Wolf on 2006-01-09
I've setup a Breezy system for my parents which works great but has a problem when using USB thumb drives.

The system is setup so that Mom and Dad have their own logins, and use different screen groups to switch back and forth.

The problem with removable media is that when my Dad inserts a thumb drive, it is auto-mounted with my Mom as the owner and permissions of 700, so that he can't read it.

Both of these userids have the same administrator rights, so I'm assuming that it is mounting as one id because it is somehow chosen first.

Both userids share the same group id, so is it possible to cause removable media to be mounted 770 or 775 so that both can use it?

Thanks, 
Kirk

---

### Post by BathroomNinja on 2006-01-09
I may be way off here, but if the file system on the thumbdrive is FAT or FAT32 (should have come that way by default), then it shouldnt save user rights.  However, it sounds like your thumbdrive may be in ext2 or 3.  The only thing I can think of off the top of my head is:

backup the data from the thumbdrive
Use Gparted to format the thumbdrive using FAT32 or FAT.
Unplug, replug, then try again to see if all users can read the files.

Let me know if that works.  If it doesn't work; I'll use my thumbdrive at home to attempt to recreate the problem.

---

### Post by aysiu on 2006-01-09
[QUOTE=Kirk Wolf]
Both of these userids have the same administrator rights, so I'm assuming that it is mounting as one id because it is somehow chosen first.[/QUOTE] So this option is enabled for your dad? (see attached screenshot)

---

### Post by Kirk Wolf on 2006-01-09
Yes;  both userids have that permission.  The problem is that the auto mount mechanism seems to always choose "mom"s userid as the owner.  This would be OK, if there were a way to have it mount the thumbdrive with 770 instead of 700.


Also, the thumb drive is definitely FAT or FAT32... one of their friends brought it over from their Windoze machine.   They really don't want to reformat it.... only read it actually.

Thanks, 
Kirk

---

### Post by BathroomNinja on 2006-01-09
When I get home in about 5 hours, I will attempt to recreate this issue with my thumbdrive.  I currently only use it for me, so I will see what happens when I login with a different user.

---

### Post by BathroomNinja on 2006-01-11
I was unable to duplicate the problem :(

---

