---
title: "Help with new TB setup"
date: 2009-04-26
forum: General Help
---

### Post by rreyes1316 on 2009-04-26
I just got a new TB HD and want to ensure I can use it with linux (my main os) and windows over a network. I will mostly store videos, music, and photos. Should I use NTSF or fat32 or perhaps a combo? Just to ensure I have the best file setup.

Thanks

---

### Post by bdoe on 2009-04-26
It depends on how you intend to connect your hard drive to the network. Is is an external NAS? Is it going into a server? Or is it going into the same computer you intend to use primarily?

In the case of network-attached storage (NAS), it really doesn't matter what filesystem you use. In the case of an internal server drive, the filesystem used should be one that's understood by the server. If the server in question is running Windows, then you should probably choose NTFS. If it is running Linux, then you should probably use EXT3.

Also, hard drive size will have a lot to do with your decision. I'm assuming the "TB" designation you're using refers to the hard drive size. In this case, your best bet is to go NTFS. I don't think FAT32 can handle such large drives without hacks, but I might be wrong. At any rate, the filesystem overhead imposed by FAT on such a large volume would be astronomical.

---

### Post by rreyes1316 on 2009-04-26
Well . . .I plan on having the TB drive in the machine. The os will be on my Raptor 150 also running XP in VirtualBox(maybe). The other pc's in the house are linux except for one. I would like all the pc's in the house to be able to access the TB drive. Ideally I want to build a myth box. Does windows read ext3? And what is the difference with this new ext4?

---

### Post by cariboo on 2009-04-26
If you use samba to share the files on you hard drive, it doesn't matter how the partitions formated. I am currently using Freenas on my server ant all the partitions are formatted as ufs, every computer that is on the network can connect and read/wrtie files. Currently 1 XP desktop, 1 XP laptop, 2 Jaunty desktops, 1 AntiX desktop and 1 Intrepid server.

Have a look at this [thread=202605]howto[/thread].

---

