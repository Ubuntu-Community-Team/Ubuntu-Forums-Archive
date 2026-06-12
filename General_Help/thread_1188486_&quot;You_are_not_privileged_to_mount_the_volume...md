---
title: "&quot;You are not privileged to mount the volume....&quot;"
date: 2009-06-15
forum: General Help
---

### Post by adrian4design on 2009-06-15
Can someone help,

I edited my Fstab file to automount two internal harddrives but now it seems one mounts fine but the other doesn't mount at all and produces this error on any attempt to;

"You are not privileged to mount the volume".

What output is needed to determine the state of the disk I am a real beginner to Ubuntu?

I should mention this is my first dual booting system and windows can see and access the disk fine.

Below is the last few lines of my Fstab, the last two I added:

UUID=ea8f2bd2-db0f-4f39-9951-dd8af28fabaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/My\040Documents ntfs-3g defaults,nls=utf8,umask222 0 0
/dev/sdc1       /media/Archive ntfs-3g defaults,nls=utf8,umask222 0 0

---

### Post by michy99 on 2009-06-15
It is possible that the drive did not unmount cleanly the last time you were in windows.

---

### Post by adrian4design on 2009-06-15
Nope, I have thought of that and have only today been in and out of windows with no trouble!

I think it is something I have put into my Fstab maybe?

---

### Post by merlinus on 2009-06-15
/dev/sdb1       /media/My\040Documents ntfs-3g defaults,nls=utf8,umask222 0 0

You might try changing the \ to an _ 
My_040Documents

linux does not use backslashes.

---

### Post by itix on 2009-06-15
Have you tried using UUIDs instead of just /dev/whatever?

You can find the UUIDs by [COLOR="Navy"]ls /dev/disk/by-uuid[/COLOR] (or by simply browsing that folder in nautilus which is the file browser which probably is easier since you can get more info from nautilus).

Check for the disk which is already in fstab in UUID mode and add the other two. That way, it will find those two even you remove and reinsert your disks.

EDIT: never mind... listen to the guy above. You cant use "\40" as a blank space. Use '/media/My Documents' if you want to mount it to /media/My Documents...

---

### Post by Polaris96 on 2009-06-15
just a hunch:  check the owners and permissions on fstab.  might've gotten scrambled when you saved.

try commenting out the new lines by placing a # in front of them and then reboot.  If it still doesn't work, you probably have saved fstab with other than root priviledges.  That shouldn't be possible, but I have seen it happen, before.

---

### Post by adrian4design on 2009-06-15
Polaris96,

Your "commenting out" cleared my fault so I now have access to my drive however now neither drive is automounting, what do I need to change in fstab now, see below:

UUID=ea8f2bd2-db0f-4f39-9951-dd8af28fabaa none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1       /media/My\040Documents ntfs-3g defaults,nls=utf8,umask222 0 0
#/dev/sdc1       /media/Archive ntfs-3g defaults,nls=utf8,umask222 0 0

---

### Post by Polaris96 on 2009-06-16
ok, you do have the correct priviledges assigned to fstab. 

The next thing that jumps out at me is that you're trying to mount scd.  why?  normally an automounter takes care of that when you pop in a cd.  

You wouldn't be allowed to mount a removable drive if there was no media in the drive.  Did you have a CD in the drive when you rebooted?

Try uncommenting everything except scd and then reboot.

---

### Post by michy99 on 2009-06-16
> **Polaris96 said:**
> ok, you do have the correct priviledges assigned to fstab. 

The next thing that jumps out at me is that you're trying to mount scd.  why?  normally an automounter takes care of that when you pop in a cd.  

You wouldn't be allowed to mount a removable drive if there was no media in the drive.  Did you have a CD in the drive when you rebooted?

Try uncommenting everything except scd and then see what happens.

That's the usual fstab line for scd. The noauto option keeps it from mounting automatically.

---

### Post by Polaris96 on 2009-06-16
thanks, michy!  that one got past me :)  I still think it's worthwhile to try the test I mentioned.  maybe even try one at a time until we figure out what's breaking the rules.

---

### Post by adrian4design on 2009-06-20
Sorry for my absence,

I have been looking at your suggestions, I had the archive hard disk auto mounting when the other disk locked up, the reason I want auto-mounting is I use these disks on a wireless network with windows machines and if they aren't mounted I can't access them from my laptop.

How do I view the fstab privileges?

---

