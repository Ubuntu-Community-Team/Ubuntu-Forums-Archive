---
title: "installed Jaunty and cannot customise icons"
date: 2009-10-24
forum: Desktop Environments
---

### Post by guiliker on 2009-10-24
ubuntu: Jaunty latest
gnome: 2.26.1

I had to reload my ubuntu due to an issue with the Windows partition. I decided to use a Jaunty image. I am trying to make my screen as pretty as it was under Intrepid, however I cannot upload any icon themes. I get the following fault:
```
[ 4760.753662] gnome-appearanc[5066]: segfault at 0 ip b77683ef sp bfab9320 error 4 in libpango-1.0.so.0.2400.1[b773d000+40000]
```
What do I do to fix this?

Thanks in advance :)

I have not fixed this, but I have realised a workaround. Ignore the "appearances" GUI and uncompress the chosen icon theme folder. Once uncompressed move to ".icons" folder in the "home" folder. Log out and log back in again, then use the GUI to select chosen icon theme. However, I still get the above error message in the log.

---

