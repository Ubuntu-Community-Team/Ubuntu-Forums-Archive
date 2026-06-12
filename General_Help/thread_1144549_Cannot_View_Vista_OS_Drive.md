---
title: "Cannot View Vista OS Drive"
date: 2009-04-30
forum: General Help
---

### Post by sgtlange on 2009-04-30
Hello all, i recently installed all of the ntfs components to read/write ntfs but i cannot view my main vista drive containing all of my data. 

Here are a few things to know. There is no seperate partition for ubuntu i believe it is installed directly under the windows drive 'c' here is my fdisk command from terminal:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbcf0706b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8544    68628448+   7  HPFS/NTFS
/dev/sda2            8544        9527     7889920    7  HPFS/NTFS
/dev/sda3            9527        9730     1627136    7  HPFS/NTFS
josh@ubuntu:~$ 

My hp machine has the main partition for vista and now ubuntu, an "HP Recovery" and "OS Tools" that came from the factory.

I beleive sda1 is the one i am after but i have tried mounting it to the media folder labled windows. when accessing windows the folder is empty.

I can however, access the os tools, and hp recovery and view the ntfs files.

HELP! :)

---

### Post by bswilson on 2009-04-30
Could you give us some information about your install?  Did you use the Wubi installer to get Ubuntu on your machine?  Or are you dual-booting?  If the latter, what does your grub configuration look like?

---

### Post by sgtlange on 2009-04-30
i installed by disk, i am running 8.10. Yes i am dual booting vista and ubuntu. i am not sure what you mean by grubb configuration. Hope this helps, if you need more information let me know and if its some digging let me know how to get it and i'll post my results. 

Thanks!

---

### Post by sgtlange on 2009-05-02
Bump, Any help?

---

### Post by zvacet on 2009-05-02
> There is no seperate partition for ubuntu i believe it is installed directly under the windows drive 'c'

If this is correct then you installed by Wubi installer.I hope if you confirm this that would be helpful to somebody else who know more about this.

---

### Post by sgtlange on 2009-05-03
It must have been the Wubi installer but i guess i'm not really sure. I went to ubuntu.com downloaded the iso burned it to a disc and installed it via booting the disc. Thanks

---

### Post by bswilson on 2009-05-13
**sgtlange**, can you post the contents of the file **/boot/grub/menu.lst** here, so we can help you troubleshoot?

---

