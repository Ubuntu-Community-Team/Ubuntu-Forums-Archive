---
title: "Odd problems for new user."
date: 2009-02-26
forum: General Help
---

### Post by noseforsharpies on 2009-02-26
I installed Ubuntu 8.10 over Vista, completely. When it boots up, there's an odd message about the boot timer not connected . . . or something. Also, my computer shut off ( heat issue ) and when it restarted, Ubuntu went into the automatic file-check. Which failed. And I'm not sure how to do the manual file-check . . . So what should I consider looking into? Not looking for specific answers, necessarily, but just some things I should look into. Do I have a corrupt OS? Also, after it boots, there's some weird green / pink static-stuff that goes across the top-screen, then the cursor is a little x, THEN it finally kicks in. 

I kept rebooting, and finally it just started without trying to do the file-check. Another thing . . . There was something about an I/O error that I noticed when it tried to do the file-check.

Thanks!

---

### Post by justleen on 2009-02-27
if your unsure bout the state of your disk, your best off to boot the live cd, and run a filesystem check.
```
 fsck.ext3 /dev/sda1 
```
where sda1 is your disk.

The reason you should this from the live cd is that the filesystem you want to check should be unmounted. And you cannot easily umount the root drive..

---

