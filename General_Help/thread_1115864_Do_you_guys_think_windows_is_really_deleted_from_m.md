---
title: "Do you guys think windows is really deleted from my computer now?"
date: 2009-04-04
forum: General Help
---

### Post by krine11 on 2009-04-04
Hi, I followed someone instructions from a old post about how to get rid of windows and just use ubuntu. He said to use that hard drive were all of the windows files were and select it to make that hard drive 100% ubuntu. So does that mean windows is officially deleted? If it is Thanks Ubuntu Community you guys rock!

---

### Post by s.fox on 2009-04-04
Hi,

Which guide did you follow?  Can you post a link?

-Ash R

---

### Post by krine11 on 2009-04-04
I  really cant but it showed a small graph with my hard drive space and stuff and than i selected a choice and clicked next where i instaslled and it started working.

---

### Post by ShaunG on 2009-04-04
If you have partition editor installed (gparted) open that up. 

System -> Admin -> Partition Editor.

Otherwise install

```
sudo apt-get install gparted
```

Then run it.

If you can see an entry similar which has filesystem as fat16/fat32/ntfs and the flag for that entry says boot, then Windows is still installed on that parition. (Generally /dev/sda1 )

---

### Post by ulfj on 2009-04-04
If I'm understanding you correctly you used 100% of the drive for ubuntu,then I would say yes it's gone. I did the same thing the other night on a desktop was in a hurry and not paying attention and wiped out XP on that machine,I used XP for only 1 app so no big deal in my case.

---

### Post by ShaunG on 2009-04-04
Forgot about fdisk.

in a terminal type 

```
sudo fdisk -l
```

This will show you all of your partition. IF you can see your windows parition (ntfs/fat file system, with a * under the boot column) then it's still there. Otherwise, gone :)

---

