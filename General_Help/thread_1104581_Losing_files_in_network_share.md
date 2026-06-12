---
title: "Losing files in network share"
date: 2009-03-23
forum: General Help
---

### Post by deboard on 2009-03-23
I have a PC running Ubuntu that serves files using NFS and Samba (NFS for my linux machines, and Samba for the windows machines). This is mostly things like pictures, music, etc.  I use mirrordir to back this all up nightly to another drive.  

Anyways, I noticed today that a lot of my pictures directories are empty.  Once I dug into it, I also noticed that mirrordir noticed the files were gone, so I don't think that the problem lies with mirrordir.  This happened once before on a much smaller set of files, but I chalked it up to user error.  

The odd thing is that only the files in the 2nd level of directories are missing, across the board.  So if I have:

/pictures/jan/
/pictures/feb/
/pictures/mar/
         
then all pictures in jan, feb, and mar are gone.  But if I have

/pictures/jan/jan10/

then all pictures in jan are gone, but pictures in jan10 are still there.  

I'm stumped, if it was just one directory I would think it was user error (which would be me, since I'm the only user really), but there are probably 30+ directories where the pictures are gone like this. I can see myself accidentally deleting one directory's worth doing something stupid, but not going into each directory, leaving the directory structure intact and only deleting the first level of files.  

I'm using ext3 on the disk, Ubuntu 8.10, up to date NFS and Samba.  The disk has performed solidly up until now, but I guess it could be going, I don't see any signs of that though.  

Anyone heard of anything like this? I'd certainly like to avoid this in the future.

---

### Post by deboard on 2009-03-24
I wanted to add that I have 4 main shares, and the two that lost files are the ones that are accessed through samba the most.  In fact, it's likely the other two haven't been accessed through samba in the past month at all, and they appear to be completely intact.  

Is there a possible NFS/Samba interaction that I am not aware of?  Is it ok to share the same directory with both NFS and Samba?

---

