---
title: "Creating image from fully encrypted ubuntu system"
date: 2015-01-24
forum: Desktop Environments
---

### Post by Frank_Brner on 2015-01-24
Hello.

I use the program "image for linux" from terabyte (comercial product) for creating backup images. I use this for years and it works fine.

But:
I have a problem with creating an (full) image with image for linux from a ssd.

When I create an image from a ssd with linux installation and NO  encryption - it all works perfectly, smooth and fast and the image is  small.
The same, when I only encrypt my home folder (\home) in a linux installation.
But when I make a fully encrypted system (for example with ubuntu 14.04.  trusty tahr), the creating of the image takes a long - a very long
time and the image is really huge.

For example:
Making an image from a ssd with 128GB (about 28GB used from it) from a  not encrypted or only home-folder-encrypted system creates
an image with some 12GB size - and this in about 10 - 12 minutes with validating on!
Making an image from the same ssd with the same system - but only now  full encrypted system - creates an image with 120GB size and
takes more than 1 1/2 hours - without any validation...

Is there any hint, you can give me about this? I really want to use a full encrypted system for security purposes.

Thanks very much.

Regards

---

### Post by sudodus on 2015-01-24
Welcome to the Ubuntu Forums :-)

I don't know your particular backup/imaging tool, but I suppose that the encryption makes it impossible to use the optimisation methods, that works in a system without full encryption. It might be better to use a simple imaging method for each byte without any compression. The final size will be similar and you won't spend time trying to compress what is made to look like random data.

The most basic imaging tool is dd, but it is risky. ***Clonezilla*** has safety precautions, and can often optimize the backup, but I think in this case it will resort to dd (but still be much safer than a naked dd command line.

If you plan to switch to Clonezilla, you need an extra drive. Restore from the backup to that drive, and verify that the restored system works as it should! Otherwise you don't know if the backup works.

It is possible that your current backup (the big one) is similar to what you get with Clonezilla.

1. If you think it is too slow, it is worthwhile trying Clonezilla.
 
2. If you think it is good enough, you should verify that the restored system works as it should also in this case, because it is different from your previous case.

-o-

Another option it to create a backup not as an image, but of your important personal files. Such a backup is done while running the system, and the files would be backed up without encryption. It is easy to make such a backup incremental, to add new files and only check that the old files are still the same (and to back them up if changed).

Such a backup is much faster and more convenient (but it is not complete like a cloned image).

---

