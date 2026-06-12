---
title: "Can't change permissions to store files on my external hard drive."
date: 2009-01-01
forum: General Help
---

### Post by Kaileida on 2009-01-01
I got an Iomega 500GB External Hard Drive for Christmas. My primary laptop runs Mac OS 10.3.9, so I formatted the drive to work with that and pulled all my pictures, music, etc. Now, I have another laptop that runs Ubuntu, which I use mostly for storage purposes, as a secondary chat client, etc. When I plugged the drive into that computer, it told me that I had read-only privileges, as well as mounting a second "drive" it dubs Boot OSX.

I don't know that Disk Utility (on the Mac) will let me change the permissions- I couldn't find the option to- and I don't have to worry about losing the data, as I've already copied it to the other laptop. Anything I can do to make it behave like I've just gotten it out of the box- or, at the least, let me have read and write permissions?

Thanks in advance!

---

### Post by dcstar on 2009-01-01
> **Kaileida said:**
> I got an Iomega 500GB External Hard Drive for Christmas. My primary laptop runs Mac OS 10.3.9, so I formatted the drive to work with that and pulled all my pictures, music, etc. Now, I have another laptop that runs Ubuntu, which I use mostly for storage purposes, as a secondary chat client, etc. When I plugged the drive into that computer, it told me that I had read-only privileges, as well as mounting a second "drive" it dubs Boot OSX.

I don't know that Disk Utility (on the Mac) will let me change the permissions- I couldn't find the option to- and I don't have to worry about losing the data, as I've already copied it to the other laptop. Anything I can do to make it behave like I've just gotten it out of the box- or, at the least, let me have read and write permissions?

Thanks in advance!

You have to tell us what type of filesystem you formatted the partitions as.

---

### Post by Kaileida on 2009-01-01
It says the volume format is Mac OS Extended (Journaled).

---

### Post by mc4man on 2009-01-01
You may want to wait for some others to chime in.

Anyway over the fall one of my son's friends stayed with us for a while with a new mac. 
To allow them to share some files with a flash drive we formatted one on the mac with mac Os extended (hfs+, no journaling ), not sure which partition scheme we used (options

While it worked the only way in ububtu to write to the disk was as root.
(the mount options were rw, <i don't remember>  uid=0 gid=0

While there probably was a solution what was easier was to clear the drive on the mac (format to free space) and then partition it in ubuntu to hfs.

This way it worked fine in ubuntu and the mac. I believe the package to allow gparted to format hfs was hfsutils

But as I said if you format without journaling it does work, maybe someone knows how to get around the root only write permission. (with hfs+

Edit: and obviously a vfat (fat 32) should work on any Os

---

### Post by Jordubu on 2009-01-24
All right guys,

This is what i did and it works

I have an Iomega external Hard Drive (HD USB) 250 GB
I downloaded &#8220;GPARTED&#8221; then it identified my Iomega HD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Then I rightcliced it and UNMOUNT it That&#8217;s necessary for the formatting
Finally rightcliced again and select format to FAT32 that&#8217;s the needed one format
This FAT32 allow you to write and read it.

And it works with Ubuntu and
Windows and I supose to MAc OS X too
So that is it
Remember to make a BACK UP first with DVDS or another Computer or HD

---

### Post by Jordubu on 2009-01-24
All right guys,

This is what i did and it works

I have an Iomega external Hard Drive (HD USB) 250 GB
I downloaded &#8220;GPARTED&#8221; then it identified my Iomega HD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Then I rightcliced it and UNMOUNT it That&#8217;s necessary for the formatting
Finally rightcliced again and select format to FAT32 that&#8217;s the needed one format
This FAT32 allow you to write and read it.

And it works with Ubuntu and
Windows and I supose to MAc OS X too
So that is it
Remember to make a BACK UP first with DVDS or another Computer or HD

And forget about that permission I just write and read without problems in my HD

---

