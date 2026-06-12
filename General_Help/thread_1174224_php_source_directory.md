---
title: "php source directory?"
date: 2009-05-30
forum: General Help
---

### Post by boon4376 on 2009-05-30
Im trying to install magickwand, And it wants me to extract it to my PHP source directory, and i have no idea where that is in ubuntu.

I've installed ubuntu server w/ lamp, then installed ubuntu desktop GUI.

Please tell me where to locate the PHP source directory thanks! :D

---

### Post by boon4376 on 2009-05-30
30min bump

anyone?

On my other machine, I had to extract it to
/usr/include/php5/ext/

But on this install, none of the php5 labled folders have ext sub directories.
and the /usr/include directory doesnt even have a php5 folder *confused

---

### Post by ActiveFrost on 2009-05-30
**/etc/php** or **/etc/php5** ;)

---

### Post by Mike'sHardLinux on 2009-05-30
Have you installed or downloaded the PHP source? I didn't think source code was installed by default, though it's been a while since I used Ubuntu server....

As for /etc/php or /etc/php5, ActiveFrost, aren't those just the "config" directories? Source refers to the source code. When you install magickwand, I think you have to rebuild PHP.

---

