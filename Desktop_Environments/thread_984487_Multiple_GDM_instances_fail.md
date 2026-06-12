---
title: "Multiple GDM instances fail"
date: 2008-11-16
forum: Desktop Environments
---

### Post by shhgs on 2008-11-16
Hi all:

I want to start multiple gdm sessions on my laptop. One on local machine, one login to a remote system through XDMCP. However I can start the two gdm screen, but whenever I try to login, it failed. Keyboard and mouse stuck, and networking stopped. The only way to wake it up is to press the power button, hard.

I am using 810 amd64 version. And my laptop is a Acer Extensa 5420-5571, which is using ATI video card. I noticed there's a slip about this issue. [http://ubuntuforums.org/showthread.php?t=161168](http://ubuntuforums.org/showthread.php?t=161168), but it is about drake. I want to know is this bug fixed, or still hang there.

The config change listed below.

```
diff -uBb -r1.3 gdm.conf-custom
--- gdm.conf-custom	2008/11/16 21:28:34	1.3
+++ gdm.conf-custom	2008/11/16 21:33:17
@@ -65,4 +65,3 @@
 
 [servers]
 
-1=Chooser

```

Thanks all.
Jon

---

