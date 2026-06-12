---
title: "Install qtparted"
date: 2005-04-30
forum: Desktop Environments
---

### Post by otterit on 2005-04-30
I'm trying to install qtparted after downloading the .deb from the qtparted home page.  I'm receiving the following error:

#dpkg -i qtparted_0.4.3_i386.deb
(Reading database ... 58795 files and directories currently installed.)
Unpacking qtparted (from qtparted_0.4.3_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing qtparted_0.4.3_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/sbin/qtparted')
Errors were encountered while processing:
 qtparted_0.4.3_i386.deb

Any idea?

Thanks!

---

### Post by jeremy on 2005-05-10
try sudo apt-get install qtparted

---

