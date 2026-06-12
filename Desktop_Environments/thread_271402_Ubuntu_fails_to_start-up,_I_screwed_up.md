---
title: "Ubuntu fails to start-up, I screwed up"
date: 2006-10-04
forum: Desktop Environments
---

### Post by LostJot on 2006-10-04
[[img=http://img217.imageshack.us/img217/1519/img0352ui8.th.jpg]](http://img217.imageshack.us/my.php?image=img0352ui8.jpg)

This is it loading up in recovery mode, it won't continue beyond this point. If I disconnect the USB devices, it won't go beyond the "kjournald" line.

How I screwed up:

I was at the command line, trying to figure out how to get my nvidia driver properly configured. I had hit init 3 at the command line, but ended up hitting 6 instead. Some lines of text came up, ending with something to do with the BIOS. In hindsight, I should have taken a photo of this, but I didn't. I rebooted and both Windows and Ubuntu loaded up. 

But Ubuntu had lost /media/hda1 and /media/EXTERNAL, they had gone from the desktop and their contents were empty when accessed through nautilus. I considered this to be a minor problem, I was happy that at least I could get into Ubuntu to clear up my mess at some point.

Went back into Windows to do some other (unrelated) stuff. External drive functioning fine (I think I had lost the mount in Ubuntu, somehow). 

Started up Ubuntu again to see how on Earth I was going to configure my system to use nvidia. But it wouldn't load. Standard load wouldn't go beyond "decompressing the kernel....OK". Recovery mode load stops at the point shown above. 

Is this fixable?

---

### Post by LostJot on 2006-10-05
I think I will reinstall. Is this as simple as putting the CD, going to the live desktop and asking it to install as I did the first time around?

---

### Post by taurus on 2006-10-05
> **LostJot said:**
> I think I will reinstall. Is this as simple as putting the CD, going to the live desktop and asking it to install as I did the first time around?
Yes.  Exactly the same.  However, may want to format your Linux partitions over again so you would have a clean system...

---

