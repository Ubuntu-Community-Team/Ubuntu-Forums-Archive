---
title: "cannot install nvidia driver after linux-rt"
date: 2009-05-11
forum: General Help
---

### Post by sharkcohen on 2009-05-11
After installing and booting on the linux-rt kernel in 9.04, I am unable to reinstall the 180.51 nvidia driver.  The kernel headers are installed, and I am pointing the install script to them with --kernel-source-path.  The install script spits out the following error:

```
ERROR: The kernel header file
       '/usr/src/linux-rt-headers-2.6.28-3/include/linux/version.h' does not
       exist.  The most likely reason for this is that the kernel source files
       in '/usr/src/linux-rt-headers-2.6.28-3/' have not been configured.
```

It certainly is not there:

```

sharkcohen@sharkdesk:~$ ls -la /usr/src/linux-rt-headers-2.6.28-3/include/linux/version.h
ls: cannot access /usr/src/linux-rt-headers-2.6.28-3/include/linux/version.h: No such file or directory

```

Please advise, thanks.

```

sharkcohen@sharkdesk:~$ ls /usr/src
linux-headers-2.6.28-11          linux-rt-headers-2.6.28-3
linux-headers-2.6.28-11-generic

```

---

