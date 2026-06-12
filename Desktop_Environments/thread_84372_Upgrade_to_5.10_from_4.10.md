---
title: "Upgrade to 5.10 from 4.10"
date: 2005-10-30
forum: Desktop Environments
---

### Post by dutler on 2005-10-30
How do I do the upgrade from 4.10? I just replace the info in my apt source.list  with 5.10 sources right?

---

### Post by aysiu on 2005-10-30
Yes--a find/replace on the word *warty* for *breezy* should work fine (except for backports). Then ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by dcstar on 2005-10-31
[QUOTE=dutler]How do I do the upgrade from 4.10? I just replace the info in my apt source.list  with 5.10 sources right?[/QUOTE]

Have a read of the various Upgrade FAQs around, they can help you avoid potential problems and make the whole process as smooth as possible.

I downloaded and made a 5.10 install CD when I upgraded from 5.04 on the weekend, as I prefer to have that than just have the files downloaded on-line.

---

### Post by dutler on 2005-10-31
Thank you for your help! I did run in to some problems though...
> 
udev requires a kernel >= 2.6.8, upgrade aborted.
dpkg: error processing /var/cache/apt/archives/udev_0.050-3ubuntu7_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace wireless-tools 26+27pre22-1ubuntu1 (using .../wireless-tools_27-1ubuntu1_i386.deb) ...
Unpacking replacement wireless-tools ...
Errors were encountered while processing:
 /var/cache/apt/archives/udev_0.050-3ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Does the dist-upgrade not upgrade the kernel? 
What if the 4.10 kernel is user mode linux? 
I also do not need things like "wireless-tools" was this already install or was it going with the dist-upgrade? can I dist-upgrade server or somthing like that?

peace / dutler

---

### Post by dutler on 2005-10-31
solved. was able to replace the kernel with a 2.6 varity, then followed the direction to upgrade to breezy.

thanks again!

---

