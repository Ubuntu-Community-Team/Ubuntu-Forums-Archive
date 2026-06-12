---
title: "Ubuntu server 11.04 Terrible network speed"
date: 2011-09-24
forum: Desktop Environments
---

### Post by cactuarknight on 2011-09-24
Hi, i'm getting terrible network speeds from an ubuntu server 11.04 box.
not sure about most of the hardware but i know it has a gigabit network card, 1GB ram, and 2 hdds, one sata(for storage, on an expansion card), the other IDE(swap, os installation)

Heres the issue, i can download files from my windows 7 machine at 40MB/s, but if i try and download (i want to use it as a backup/tftp server) the files back i get speeds ranging from 400 to 800 kb/s.
(FTP has the same issue)
to test if this was a samba sharing issue, i installed a LAMP server and was able to share the files back at about 10MB/s, but this isn't really an option with my limited knowledge of active filesharing.

i was able to abtain the speeds noted above by downloading the files using a firefox plugin to increase the downloads threads from 1 to 10.

Is there anything i can do to make this increase work with samba as well as with an apache2 server?

Thanks
i use webmin 1.560 to administer the box if that helps

---

