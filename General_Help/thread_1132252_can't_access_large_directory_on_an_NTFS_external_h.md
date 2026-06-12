---
title: "can't access large directory on an NTFS external hard drive"
date: 2009-04-21
forum: General Help
---

### Post by das88 on 2009-04-21
I've got ubuntu 8.04 on a dell mini laptop and I'm trying to access my music on a 100GB USB hard drive. When I expand the music folder in Nautilus using list view I can see a list of the sub-folders but if I try to expand one of the sub-folders nautilus freezes. If I try to get to the music folder in icon view, nautilus freezes. When I try to end the nautilus process in the system monitor after these crashes, the process switches over to 'zombie' status and won't go away. I've tried to access the directory from the terminal using 

cd /media/disk-1/music

but the system thinks for quite a while and then tells me the directory doesn't exist, even though that's the path nautilus gives me for the folder. The music directory is probably about 70GB, I'm not sure exactly how large it is because the Disk Use Analyzer hangs when I scan the filesystem with the hard drive attached. Is this happening because the directory is too large? Is there some issue with accessing lots of data in NTFS partitions? I had to force mount it a few times because it was unsafely removed from windows (but I can still access all my data from windows), is that an problem?

Thank you!

---

### Post by ajgreeny on 2009-04-21
Perhaps there is a corrupt file somewhere in this large folder which can't be read in ubuntu so simply throws a wobbly and freezes.  Otherwise I have no idea.  Have you run a chkdisk on the windows partition from within windows?  If not it is probably worth doing so.

PS, I think chkdisk is the program; it's so long since I used windows that I can't remember.

---

### Post by JC Cheloven on 2009-04-21
I had problems like this a couple of times. Every time the reason was the same: some fault in the ntfs file system. Nothing to do with the size of the folders.

The faulty condition was produced either by an improper "unmount" from windows (as a hard shutdown or whatever), or simply by a corrupted file. 

My guess is that while linux can understand ntfs, it is not as good in managing problems with it. After all. this is a windows filesystem.

Personally, I solved the problem formatting to ext3 my music drive. No issues since that. 

If you want your media on ntfs for the sake of compatibility, I'd say that to have a windows boot at hand is advisable, in order to repair eventual faults. If my memory serves me, you will find a tool like "check the disk's filesystem" right-clicking on the drive (at the file browser), and going thru properties -> tools, or something like that.

---

