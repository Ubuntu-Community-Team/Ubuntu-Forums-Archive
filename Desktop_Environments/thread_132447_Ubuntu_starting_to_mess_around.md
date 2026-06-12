---
title: "Ubuntu starting to mess around"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Kimm on 2006-02-18
My currently Ubuntu install has lasted for a long time, and I want it to last even longer. But today it has been messing with me.

1. All of a sudden I am missing from the sudoers file. This was easuly fixed by loggin in as root and editing it, still annoying however.

2. After rebooting /dev/video0 claims that I dont have the permissions to use it, temporarily fixed by issuing chmod 666 /dev/video0 as root

3. After /dev/video0 permissions where fixed the webcam still doesnt work, I no longer get a stream only a blank screen. I dont know how to fix this, I tried recompiling the driver - no luck.

I wounder it these problems might have something to do with me recompiling the kernel, or glibc. However I did both of these things quite some time ago (glibc a few mounths ago, kernel a few weeks ago), so I cant see this causing the problem anyway.

Anyone?

```

#uname -a
Linux ubuntu 2.6.15-cks1 #1 Sat Feb 4 13:03:27 CET 2006 i686 GNU/Linux

```

---

### Post by Kimm on 2006-02-19
/bump

---

### Post by Kimm on 2006-02-21
no worries, I fixed it. My Userprivelages where completely messed up, only thing the system would let me do way Use the sound card ;)

---

