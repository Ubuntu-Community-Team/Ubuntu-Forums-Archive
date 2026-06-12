---
title: "Enable Trash on secondary ext4 filesystem (HDD)"
date: 2011-11-14
forum: Desktop Environments
---

### Post by joxl on 2011-11-14
I'm wondering if it's possible to enable the Trash (is this a nautilus feature?) on a secondary (internal) hard drive.

Here's my scenario; I recently did a clean install (11.10) on a new SSD.  Due to the size restriction of the device (120GB) I've sym-linked a few folders in my user directory to another (spinning disk) hard drive. for example:
```
$ ls -l ~/Music
lrwxrwxrwx 1 me me 34 2011-11-10 19:11 /home/me/Music -> /media/HD1/archive/Music

```The problem is if I delete items that don't reside on the root device (my SSD), nautilus tells me that they cannot be moved to the trash and will be deleted immediately.  I do realize that even if they ***could*** go to the trash, they would not be located in the default [FONT=Courier New]'~/.local/share/Trash'[/FONT] location, that's fine of course.  I would expect them to go to a folder somewhere on their originating disk (e.g. [FONT=Courier New]'/media/HD1/.Trash'[/FONT] or something like that).

I tried creating the directory that always magically appears on USB FAT and NTFS devices ".Trash-1000" and making it world-writable, as in:
```
$ sudo mkdir -m1777 /media/HD1/.Trash-1000
```To no avail, nautilus refused to use it as a trash directory.

Googling the issue turns up lots of results on tweaking the fstab to make this work on NTFS mounts, but my disk is formatted ext4, and those mount tweaks won't work.  I did try tweaking my fstab, however.  I used options similar to the defaults: [FONT=Courier New]'rw,suid,dev,exec,auto,**nouser**,user_xattr'[/FONT] and also the same, only user enabled: [FONT=Courier New]'rw,suid,dev,exec,auto,**user**,user_xattr'[/FONT] which didn't make a difference.  So now I've reverted it back to what I had before all that... here's the meaningful snip of my [FONT=Courier New]/etc/fstab[/FONT]:
```
$ cat /etc/fstab
<snip>
# / was on /dev/sda1 during installation
UUID=1f45...   /              ext4    errors=remount-ro,user_xattr  0       1
# HD1 -- 1TB HDD (currently /dev/sdb1)
UUID=ce4b...   /media/HD1     ext4    errors=remount-ro,user_xattr  0       2
```SIDENOTE: I have the [FONT=Courier New]'user_xattr'[/FONT] option set because that's how it was configured by the 11.10 installer... to my knowledge, I am not actually using any extended attributes.

Any help, tips or tricks would be greatly appreciated, thanks.

---

