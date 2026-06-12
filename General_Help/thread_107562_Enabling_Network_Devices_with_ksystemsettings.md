---
title: "Enabling Network Devices with ksystemsettings"
date: 2005-12-23
forum: General Help
---

### Post by nihilism wow on 2005-12-23
I run ksystemsettings with kdesu, so I can enable some ehternet/wireless devices on my desktop running Kubuntu 5.10. I can click enable interface while having the different interfaces selected, and a green checkmark appears next to the device for half a second before being disabled again. It's incredibly infuriating, yet I'm not quite sure what to do. Any help would be appreciated!

---

### Post by gohlip on 2005-12-23
I am new to this too. This may not be the proper way to do it, but it works for me. Download the gnome desktop. (you can still keep KDE as default, which I did). Then go to Systems>Networking. Enabling networking will work. Note that you still have to do this each time you
start up the computer. Did not have this problem with Hoary.
Also, unlike Hoary, Breezy needs you to start pppoeconf if you connect direct. 

Hope the rest don't throw rocks at me for saying this, but a neophyte like me finds Hoary much better. Breezy is too buggy and like its not ready for guys like us. I tried to get a number of friends on Hoary, but I am now pretty silent on Breezy. Hope Dapper will be much better. Newer versions are supposed to be?

---

### Post by gohlip on 2006-01-18
Just read a post in the Kubuntu mailing list today
Try   " sudo apt-get install ifplugd "
It worked.

---

