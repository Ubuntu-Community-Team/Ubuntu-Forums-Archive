---
title: "Dual boot help."
date: 2009-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xhahaboix on 2009-10-23
i am currently using Dell Inspirion 1420 with Vista and DMD(Dell Media Direct) installed, but wish to use ubuntu 9.10 on my laptop. Can someone provide me with a full guide on how to remove DMD partition safely and extend the partition to have ubuntu dual booting with Vista without affecting the MBR or bringing the whole system down?All help/opinions offered would be gladly appreciated.Thank You!

Partition Details are as follows:
[[IMG]http://img188.imageshack.us/img188/3546/27791125.th.jpg[/IMG]]("http://img188.imageshack.us/i/27791125.jpg/")


I believe that partition 4(2.5gb,type DD,hidden) is the one that stores all DMD files after finding more details about it through diskpart.exe.

Additional Information:
Current version of Dell Media Direct installed : 3.3.2826

---

### Post by GimmeCoffe on 2009-10-23
> **xhahaboix said:**
> i am currently using Dell Inspirion 1420 with Vista and DMD(Dell Media Direct) installed, but wish to use ubuntu 9.10 on my laptop. Can someone provide me with a full guide on how to remove DMD partition safely and extend the partition to have ubuntu installed and dual boot it with Vista without affecting the MBR or bringing the whole system down?All help/opinions offered would be gladly appreciated.Thank You!

Partition Details are as follows:
[[IMG]http://img188.imageshack.us/img188/3546/27791125.th.jpg[/IMG]]("http://img188.imageshack.us/i/27791125.jpg/")


I believe that partition 4(2.5gb,type DD,hidden) is the one that stores all DMD files after finding more details about it through diskpart.exe.

Additional Information:
Current version of Dell Media Direct installed : 3.3.2826

use wubi!

---

### Post by GimmeCoffe on 2009-10-23
Oops, read question too fast

---

### Post by GimmeCoffe on 2009-10-23
Hmm, it appears that the two other partitions are empty, so the MediaDirect partition must be hidden. 
Go to regedit, and locate the path:
HKEY_CURRENT_USER\Software\Microsoft\Windows\Curre ntVersion\Policies\Explorer. 
Then delete the key "NoDrives".

The hidden partition should appear, then you can safely format it.

---

### Post by xhahaboix on 2009-10-23
> **GimmeCoffe said:**
> Hmm, it appears that the two other partitions are empty, so the MediaDirect partition must be hidden. 
Go to regedit, and locate the path:
HKEY_CURRENT_USER\Software\Microsoft\Windows\Curre ntVersion\Policies\Explorer. 
Then delete the key "NoDrives".

The hidden partition should appear, then you can safely format it.

Unfortunately, i do not have the registry key suggested by you, i only have "clearrecent docsonexit".
Secondly, is it safe to just format the DMD partition, read some articles/posts in other forum that they are unable to boot their system and had to reinstall the system again.

---

### Post by CSdavid on 2010-01-19
Honestly dont worry about the DMD partition.  It was only 2.5GB and memory is cheap.  How much space do you have on your main partitions?

If you have enough to spare like 20Gb for ubuntu you should be fine.   

I use this OS mainly for my computer science work.   depending on what you want to use it for you might need slightly more space.

---

