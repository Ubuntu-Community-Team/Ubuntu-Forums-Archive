---
title: "Dumping remote directories with symlinks by FTP"
date: 2006-06-30
forum: Desktop Environments
---

### Post by outofsync on 2006-06-30
Hi,

I want to copy a directory sub-tree from one UNIX machine into my Ubuntu box. That UNIX machine can only be accessed by FTP in this moment.

Before you ask: No, I can't do a tar on the source machine (the disk is full), and no, I cannot configure shared disks nor other kind of network stuff in the source machine at this moment. The only available type of access is FTP.

The difficulty I see is that some of the files to be downloaded are links to other files (but they point inside the sub-tree that is to be downloaded, so they don't point to other directories that aren't of interest).

Let's suppose the directory in the source machine is /users/me/mydata/, and let's suppose that I want to dump it in a directory called /home/me/work/datadump/

If the source file /users/me/mydata/image.jpg is a symlink to /users/me/mydata/images/image.jpg, I want such symlink to also be created in the downloaded copy, but it should be modified so that it points to /home/me/work/datadump/images/image.jpg

Can I just use Nautilus for FTP-ing this stuff, or maybe I can find some problems?

Do you suggest using other tool instead of Nautilus for this purpose?

thanks!

---

