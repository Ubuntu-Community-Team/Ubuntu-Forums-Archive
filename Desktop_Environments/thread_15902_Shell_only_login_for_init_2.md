---
title: "Shell only login for init 2"
date: 2005-02-17
forum: Desktop Environments
---

### Post by vortex-5 on 2005-02-17
I'm trying to mod ubuntu a little bit.

I'm the kind of user that doesn't always use the GUI in linux, I liked how Ubuntu was able to detect all my devices with little to no work on my part. However I'm a bit dissapointed that /sbin/init 2,3,4,5 are exactly the same.

I'm used to most distro's like Knoppix / Debian (Woody) / Suse and Redhat having /sbin/init 2 as a full featured but shell only logon (no Xwindows)

Anyone know what scripts I have to change to get it to do that?

---

### Post by cyberchills on 2005-02-17
No way.......... What's up with that?  I guess you could change the /etc/inittab's default to ? no I guess not that either.  Ok well then I guess you'll probally need to edit your /etc/init.d/rc script.  Or just change the uneeded services names to start with a lowercase s in there /etc/rc*.d  directories.

Please document and POST if you end up having to do this.


RESPECT

---

### Post by vortex-5 on 2005-02-17
Changing the inittab's default won't do anything unless of course you change the default to run level 1 (since user administrative maintinence mode)

everything from run level 2-5 is X windows login....

I've tried disabling the XFree86-common script in the /etc/rc2.d section that also failed. I'm wondering if GDM is getting loaded elsewhere.

---

### Post by Wim Sturkenboom on 2005-02-18
I've just **removed** S99gdm from /etc/rc2.d and it does not start X anymore in runlevel2. So that should work for you as well.
My default is now 3 as I like Ubuntu to boot into the GUI.

---

### Post by cyberchills on 2005-02-18
Sweet.

---

### Post by rufius on 2005-02-18
[QUOTE=Wim Sturkenboom]I've just **removed** S99gdm from /etc/rc2.d and it does not start X anymore in runlevel2. So that should work for you as well.
My default is now 3 as I like Ubuntu to boot into the GUI.[/QUOTE]
 Probably a better method for doing that than just removing the file from rc2.d is to use update-rc.d. Try 'man update-rc.d'

---

