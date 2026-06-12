---
title: "Latency"
date: 2009-05-03
forum: General Help
---

### Post by Messyhair42 on 2009-05-03
I've been getting latency in my operation since upgrading to Jaunty. videos take a long time to load and stall for no reason and when i try to copy or move files the transfer takes ten times as long as it used to. I'm using an Intel E8400 3.0 X2 Core 2 Duo processor, 2 GB DDR2 RAM, 512 MB nVida graphics card, and a 1 TB seagate HD, formatted using ext3 filesystem

---

### Post by fdrake on 2009-05-03
> **Messyhair42 said:**
> I've been getting latency in my operation since upgrading to Jaunty. videos take a long time to load and stall for no reason and when i try to copy or move files the transfer takes ten times as long as it used to. I'm using an Intel E8400 3.0 X2 Core 2 Duo processor, 2 GB DDR2 RAM, 512 MB nVida graphics card, and a 1 TB seagate HD, formatted using ext3 filesystem

try to find and install some new drivers more appropriated for your system.

---

### Post by Messyhair42 on 2009-05-05
i had trouble booting into Jaunty, took a couple of tries and a side trip through a wierd screen but it worked, then i discovered that my files on my HD were unreadable. I filed a bug (#372231) with launchpad. luckily i have Intrepid on another HD still so i'm using that for the moment. i tried to access the documents on the other HD (the one with jaunty on it) and they're still unaccessable. so either it is a bug with jaunty, or my big HD is corrupt (i was getting buffer I/O errors when i shut down Jaunty). i have /, /usr, /var, /temp, and /home on separate partitions, hopefully if there's a problem it only affects /home. i'm not sure if this stems from the same problem that was giving me latency or not but it's a problem anyway.

---

