---
title: "Konqueror has returned..."
date: 2010-10-05
forum: Desktop Environments
---

### Post by gareththered on 2010-10-05
Hi,

Having installed Kubuntu 10.10 RC, I must say that I'm really impressed.  Much better than 10.04 on my laptop.

However, even though the 'blurb' say that Konequeror has been replaced by Rekonq, all I had to do was install digiKam for it to download and install Konqueror!  Now I have two browsers.  Maybe I should install Firefox, Chrome and Opera so that I have the full effect!

Is digiKam really dependent on Konqueror?  Or is this an oversight?

Regards,

Gareth

---

### Post by Dustin2128 on 2010-10-06
not sure, try sudo apt-get remove konqueror, see if it breaks digikam. It smells like an oversight to me... still, nothing wrong with having multiple browsers.

---

### Post by ankspo71 on 2010-10-06
Hi,
It think it is an oversight. I simulated the 'apt-get install' of digikam with '--no-install-recommends' and it is not showing it installing Konqueror. If Konqueror was required, it would have shown in the list of installing packages.

Simulated installation: 
```
sudo apt-get install -s digikam --no-install-recommends
```
Remove the "-s" if you want to install it without recommends.

Hope this helps.

---

### Post by gareththered on 2010-10-06
Thank you both for the reply.

The remove option uninstalled konqueror.  So I followed it with an autoremove to get rid of any other packages that konqueror needed and that removed a further two.

I've reported it as a bug anyway.  Might get fixed in time for the 10.10 release....

---

