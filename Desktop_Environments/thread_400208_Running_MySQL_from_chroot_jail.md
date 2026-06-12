---
title: "Running MySQL from chroot jail"
date: 2007-04-03
forum: Desktop Environments
---

### Post by dwaiting on 2007-04-03
Hi

I am trying to create a modified version of the Ubuntu 6.10 desktop cd.

I have followed the guide posted here:
[https://help.ubuntu.com/community/LiveCDCustomization/6%2e06](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06)

My problem comes when trying to run the MySQL server from within the chroot jail. MySQL fails to start, and therefore cannot be configured properly by apt-get.

I have browsed around and seen various solutions to similar problems but none seem to help me. Is it simply a matter of changing the /etc/init.d/mysql script or is the solution a little more complicated?

Thanks

- Dave

---

