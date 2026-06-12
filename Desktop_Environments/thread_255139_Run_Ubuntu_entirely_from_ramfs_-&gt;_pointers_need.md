---
title: "Run Ubuntu entirely from ramfs -&gt; pointers needed"
date: 2006-09-11
forum: Desktop Environments
---

### Post by obleak on 2006-09-11
Hi All,

First off - I'm not sure in which forum category this question should be asked in. 
Mods: If this thread belongs somewhere else please move it.

I was wondering if someone could point me in the right direction.

I have a via based SBC running a really stripped down ubuntu (taking up approx 200MB but can get that down to 150MB by removing a few more things) running off an old laptop HD. The MB has a Compact Flash (CF) IDE socket with a 1G sandisk CF installed and formatted as an ext2 filesystem as hdc1. The system has 1GB of ram but only uses 50MB. The system will be battery operated & mobile so eliminating the HD for is important.

The plan is to create an image the HD, put it onto the CF and load the image as a ramfs filesystem thereby avoiding writing to the CF - which is more or less what happens on bootup anyway with initramfs.

I have scoured the net but everything I find is for the 2.4.x kernel (predates initramfs) or is for tiny CF's (<32MB). I can't find anything about creating an image from a HD and loading from a readonly device into ramfs to run - perhaps I am searching for the wrong terms.

As far as I can tell it should be possible to do one of the following things:

1) create a massive initrd.img (it's just a gzipped cpio archive), don't set a root partition in the kernel boot options so the system doesn't pivot to a partition 

2) during the init, create and load the image into ramfs, pivot to the ramfs file system

3) follow the live cd philosphy - don't load the entire image into ram but mount it as a squashfs from the (readonly) CF.

I know there are embeded linux distros specifically designed for doing this, but they all assume low memory or storage space, neither of which really apply (ok a gig isn't huge but it's enough) - and I like ubuntu :)

---

### Post by anaconda on 2006-09-11
Cant help you with ubuntu, BUT

Knoppix has an option to run from ram. I think it installs (copies) the liveCD to hd (or CF if you like), and when booting the whole "CD" is loaded from hd (or CF) to ram, and is run from there. They also have a system to save changes when shutting dowm.

You could make a custom liveCD and run it from CF..

Another (minimalistic)one is DSL-N ~80MB knoppix derivative with 2.6 kernel..

I guess it would be possible to install ubuntu liveCD the same way..

EDIT: Running from ram makes the system reaaalllly amazingly FAST.. good luck..

---

