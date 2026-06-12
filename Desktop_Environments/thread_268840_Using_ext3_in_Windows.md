---
title: "Using ext3 in Windows"
date: 2006-09-30
forum: Desktop Environments
---

### Post by sexcopter on 2006-09-30
My setup of Ubuntu is and always has been like many others, consisting of an ext3 partition for Ubuntu, an NTFS for Windows and a FAT partition for "My Docs". 
A thought just occurred to me that somewhere in the somewhat distant past I read about a driver for using ext3 in Windows. Did I make that up? Or would it be possible (and presumably preferable) to just have an Ubuntu ext3 partition and Windows NTFS partition to do the same job as my current setup? If so, it'd overcome the sometimes erratic behaviour I get of permissions/ownership of stuff on the FAT partition.

Just a thought.


James

---

### Post by aysiu on 2006-09-30
[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by sexcopter on 2006-09-30
Interesting, and thanks for the instant reply!
What I'd like to know now is, why doesn't everyone do this? Or do they and I just didn't know? :p
Another consideration is if it is *safe*. I trust the filesystem support through Ubuntu, but this is true third-party support for ext in Windows (of all platforms...)
And just one other thing, your link refers to "ext2", and I'm not sure exactly how this relate to ext3.


James.

---

### Post by aysiu on 2006-09-30
I would say a lot more people use it than you think do, but not *everyone* does, for one or more of the following reasons:

1. Some people don't dual-boot Windows. They use Ubuntu exclusively or dual-boot with Mac or some other Linux distro.

2. Some people don't want Windows touching Ubuntu at all. I've never experienced any problems with that driver, but it's not unheard of that something has gone wrong (there's always at least one person out there who's had a bad experience with any given piece of software).

3. FAT32 seems to serve its purpose just fine.

4. Not everyone shares files. Some people dual-boot Windows only for games.

5. Not everyone knows that driver *exists*. Some people think FAT32 is the only option.

---

### Post by sexcopter on 2006-09-30
Ok, that all makes sense. Just to clear up the final point, will this driver be able to mount my ext3 partition? Or does it only support ext2?

---

### Post by aysiu on 2006-09-30
I've used it only with Ext3. Ext3 is essentially Ext2 but with journaling.

---

### Post by sexcopter on 2006-09-30
Cool, thanks a bunch!

James.

---

### Post by darundal on 2006-09-30
Not necessarily saying it will happen to you, per se, but one time I tried a windows driver for ext2/3 and it ended up corrupting the whole drive...

---

### Post by chavo on 2006-09-30
I got bluescreen of death when using that under Windows. It seemed to work fine but I kept getting the BSOD. Just a little warning, it may not happen to you and uninstalling fixed it.

---

### Post by drivel on 2006-09-30
Is the fs-driver stable??

---

### Post by TransitMan on 2006-09-30
I knew this question would arise again someday.
Thanks for the link to the file.

---

