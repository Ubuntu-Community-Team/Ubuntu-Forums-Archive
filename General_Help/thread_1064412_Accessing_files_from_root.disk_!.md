---
title: "Accessing files from root.disk !"
date: 2009-02-08
forum: General Help
---

### Post by MajinSaha on 2009-02-08
I have the following problem.

My laptop's motherboard seems to have corrupted. I had Vista on it with Ubuntu installed inside ( in other words, Wubi ). To save my data I bought Hard Drive Enclosure Kit - a small devise that helps to back up data from the hard drive to any desktop machine via USB cable. I succesfully saved the data from Windows, but Ubuntu is stored in a huge "root.disk" file. I can't read files from it.
Just for additioanl safety, I copied the whole "ubuntu" folder from the hard drive to my desktop computer.
Now what should I do ? Forget about laptop, it's dead now, I'm only able to work with the desktop computer. Should I use any software to extract files from "root.disk" or should I run Live Ubuntu CD and then do some mounting procedure ? Tell me everything you know ! I really need an access to those Ubuntu files, it's not just some crappy movies or music, these are very important professional files of mine ! All I need is just to copy them to one of the Windows folders, then I'll be able to back them up using the Enclosure Kit.
By the way, I have Win XP on the desktop computer, while on the laptop I had Vista. Hope that's not gonna be a trouble.
THANKS TO ALL RESPONDS !

---

### Post by Orlsend on 2009-02-09
**You could do another Wubi install,once you are done replace the root.disk file with the one you backed up. (I am not sure if it completely works, but My dad done it before.) **

**or the wubi guide says:**

"How can I access the Wubi files from Windows?

There are a few Windows applications that can mount ext2-based file systems. See for instance:

    *

      [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
    *

      [http://www.fs-driver.org/](http://www.fs-driver.org/) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\ "

---

