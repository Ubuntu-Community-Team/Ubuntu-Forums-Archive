---
title: "dpkg fails with permission denied to create status file backup even as root"
date: 2016-03-15
forum: Debian
---

### Post by stber321 on 2016-03-15
Hi. I have a Debian image in a chroot running on my phone. When i try and run apt-get I get an error telling me to run dpkg --configure -a . When I run this I wind up with an error ```
dpkg: error : error creating new backup file '/var/lib/dpkg/status-old': Permission Denied 
``` This occurs even when root???

---

