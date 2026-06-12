---
title: "Latest kernel has helped but....."
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by cjsstables on 2007-09-02
Hi all.  I'm still working to get Ubuntu Feisty configured as follows:
graphics: gm945 intel
resolution: 1920x1200
compiz-fusion: composite yes with compiz fusion, emerald, avant awm.
driver: i810 or intel
kernel: 2.6.20-16

So far to date:  I have been able to get all running with 1600x1200 using i810 driver everything (ie compositing) works great just no 1920x1200 res.


Previously was unable to get 1920x1200 at all, but with the latest kernel (2.6.20.-16) I can achieve 1920x1200 resolution using intel driver, but glxinfo reports rendering= no.  So....  I can get my 1920x1200 but without compiz-fusion/emerald/avant. 

Can anyone help me out here?  I know compositing will work with 1920x1200 on my box because If I install Debian Lenny, I can 1920x1200 with intel driver and beryl.  However, that is an unstable installation and This box really need to stay with a stable supported distro thus that is why I'm going with Ubuntu.

Any help here would be appreciated.  Let me know if you need more details on my config files.

CJS Stables

---

### Post by PmDematagoda on 2007-09-02
I don't know if this may help you or not but you could try upgrading to the latest kernel being 2.6.22-10, by using the following thread:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by cjsstables on 2007-09-02
well.  I followed that link and installed the kernel from gutsy.  Install went fine however, no changes to previous issues with my configuration.  as mentioned above.  Thanks for your help though.

CJS Stables

---

