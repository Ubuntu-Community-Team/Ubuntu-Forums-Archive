---
title: "How to use bittorrent in ubuntu"
date: 2007-06-03
forum: Desktop Environments
---

### Post by yinglcs2 on 2007-06-03
Hi,

I download a 'torrent' file using firefox and it opens torrent with bittorrent. And bittorrent downloads the files.
However, after I log out and log in again, how can I restart bittorrent?

When I open bittorrent , it asks me for the 'bittorrent meta files'. But when I go to my desktop , i don't see the torrent file that i download using firefox. 
And when I do a 'find . -name *.torrent' at my home directory, nothing is found.

Thank you for any help.

---

### Post by userundefine on 2007-06-03
Sounds like you downloaded the file to /tmp and it was likely wiped out when you logged out.  Redownload the .torrent file itself to Desktop, then open manually and point it to the files so it can resume.

---

### Post by Kidge on 2007-06-03
get bittornado through synaptic

---

### Post by Cza on 2007-06-09
i have this same issue, but instead of bittornado working it does the same thing. asks for the torrent file to open. what do i do here?

---

