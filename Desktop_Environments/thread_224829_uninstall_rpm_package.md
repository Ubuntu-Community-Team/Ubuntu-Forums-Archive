---
title: "uninstall rpm package"
date: 2006-07-28
forum: Desktop Environments
---

### Post by csteven9 on 2006-07-28
I installed an rpm package (wildfire server) on Ubuntu. Now RPM will not uninstall it. It tells me to use alien. I tried to repackage it with alien and reinstall. It didn't take. How can I remove the package or alternately, make it work? I didn't use all the commands when installed.

---

### Post by Paerez on 2006-07-28
please post the error message rpm gives you.

---

### Post by csteven9 on 2006-07-31
Sorry, I fixed it. Needed Java virtual machine. The error message said to use alien to create deb package. A little to late for the uninstall.

---

### Post by ricesteam on 2006-08-05
Hi,

I'm learning linux, and I have a similar problem. I am wondering what you did with alien to unstall your rpm package?

In other words, I did a 'sudo alien -i ###.rpm' to install my package; how do I uninstall that same package?

Thanks

---

### Post by Paerez on 2006-08-05
You can go into the Synaptic Package Manager, and search for it. Ubuntu remembers the alien packages you install, so it will be in the list.

---

