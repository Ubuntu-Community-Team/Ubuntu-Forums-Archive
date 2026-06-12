---
title: "save files from corrupted Windows system"
date: 2009-05-27
forum: General Help
---

### Post by morty35 on 2009-05-27
I need to help a friend restore some files they had on Windows XP.  Their computer has crashed and I tried fixing the Windows system with the Windows cd but some of the registries got trashed so I don't think the operating system is repairable.  

I am using a Ubuntu live cd to load the linux kernel and try to access their files from inside a boot of linux.  Where can I find the Windows files.  With a cd boot, how would I login as a root user so I can get to the Windows files.

Any help would be appreciated.

Also, is there any software that would make this possible if it is not possible the way I am trying to do it.

---

### Post by logos34 on 2009-05-27
If you can't simply mount the windows partition by clicking on it, and copy the files over, try photorec:

>system>admin>software sources>enable Universe repo

sudo apt-get install testdisk

sudo photorec

Documentation [here]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by morty35 on 2009-05-27
It turned out to be easier than I thought.  I just had to mount the Windows partition.  Thanks for the reply.

---

