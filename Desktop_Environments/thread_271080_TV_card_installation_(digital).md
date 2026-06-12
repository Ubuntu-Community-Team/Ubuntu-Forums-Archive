---
title: "TV card installation (digital)"
date: 2006-10-04
forum: Desktop Environments
---

### Post by lozenge on 2006-10-04
What is a good driver/application set to use for my TV card?

All I know is that it is pretty generic. Is there anything that'll work out of the box?

---

### Post by anaconda on 2006-10-04
I use kaffeine. It is in the repos, easy to use and works well.

For my "hauppauge wintv nova-t usb2" I found installing instructions from:
[www.linuxtv.org](www.linuxtv.org)

basically all I had to do to install my digiTv was to copy the right firmware to the /lib/firmware -folder.

(I also checked that all needed drivers were already in the kernel. With my wintv nova-t usb2. these

 - mt352.ko
 - nxt6000.ko
 - dvb-usb.ko
 - dvb-usb-digitv.ko 
)

and they were there already, so I didn't have to do anything..

---

