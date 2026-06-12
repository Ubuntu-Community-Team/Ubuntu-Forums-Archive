---
title: "Nautilus error stack smashing"
date: 2009-06-17
forum: General Help
---

### Post by rawr_a_Zombie on 2009-06-17
I recieved the following message when trying to mount a drive. also i cannot pull up and folders, they come up for a brief second and then vanish. I'm on 9.04, and am very new to linux.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:4313): WARNING **: Unable to add monitor: Not supported
*** stack smashing detected ***: nautilus terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb73e7da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb73e7d60]
/usr/lib/libbrasero-media.so.0[0xb57cbbe4]
/usr/lib/libbrasero-media.so.0[0xb57c30b9]
[0x46204e41]

---

### Post by ulvo on 2009-06-20
The same problem occured to me.

>  nautilus
*** stack smashing detected ***: nautilus terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f25c7ea82c7]
/lib/libc.so.6(__fortify_fail+0x0)[0x7f25c7ea8290]
/usr/lib/libbrasero-media.so.0[0x7f25bb79ecd7]
/usr/lib/libbrasero-media.so.0[0x7f25bb79fbe3]
/usr/lib/libglib-2.0.so.0[0x7f25c9380ae4]
/lib/libpthread.so.0[0x7f25c81223ba]
/lib/libc.so.6(clone+0x6d)[0x7f25c7e8efcd]
======= Memory map: ========


I did not find any hints for this anywhere.

---

