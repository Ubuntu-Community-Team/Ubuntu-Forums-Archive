---
title: "Inspiron 1300, DM9108 problem"
date: 2008-02-06
forum: Dell  Ubuntu Support
---

### Post by gmcorp on 2008-02-06
I found a post with information about this usb-nic, followed the instructions, but when i try to compile the driver there is an error:

gmcorp@gmcorp:/lib/modules/2.6.24-5-generic/dm9601$ sudo make dm9601   
cc     dm9601.c   -o dm9601
dm9601.c:49:24: error: linux/slab.h: No such file or directory
dm9601.c:50:24: error: linux/init.h: No such file or directory
dm9601.c:51:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/netdevice.h:28,
                 from dm9601.c:52:
/usr/include/linux/if.h:163: error: field 'ifru_addr' has incomplete type
/usr/include/linux/if.h:164: error: field 'ifru_dstaddr' has incomplete type
/usr/include/linux/if.h:165: error: field 'ifru_broadaddr' has incomplete type
/usr/include/linux/if.h:166: error: field 'ifru_netmask' has incomplete type
/usr/include/linux/if.h:167: error: field 'ifru_hwaddr' has incomplete type
dm9601.c:53:31: error: linux/etherdevice.h: No such file or directory
dm9601.c:54:23: error: linux/usb.h: No such file or directory
dm9601.c:55:26: error: linux/module.h: No such file or directory
dm9601.c:56:20: error: dm9601.h: No such file or directory
dm9601.c:63: error: array type has incomplete element type
dm9601.c:71: error: array type has incomplete element type
dm9601.c:76: error: empty scalar initializer
dm9601.c:76: error: (near initialization for 'dm9601_ids')
dm9601.c:80: error: 'DM9601_AUTO' undeclared here (not in a function)
dm9601.c:81: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'reg5'
dm9601.c:84: error: expected declaration specifiers or '...' before string constant
dm9601.c:84: warning: data definition has no type or storage class
dm9601.c:85: error: expected declaration specifiers or '...' before string constant
dm9601.c:85: warning: data definition has no type or storage class

and, so on ...
how can i fix it ? i just want to compile it, and get the .ko file i can handle the other work :)

---

### Post by charlesips on 2008-05-26
> **gmcorp said:**
> I found a post with information about this usb-nic, followed the instructions, but when i try to compile the driver there is an error:

gmcorp@gmcorp:/lib/modules/2.6.24-5-generic/dm9601$ sudo make dm9601   
cc     dm9601.c   -o dm9601
dm9601.c:49:24: error: linux/slab.h: No such file or directory
dm9601.c:50:24: error: linux/init.h: No such file or directory
dm9601.c:51:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/netdevice.h:28,
                 from dm9601.c:52:
/usr/include/linux/if.h:163: error: field 'ifru_addr' has incomplete type
/usr/include/linux/if.h:164: error: field 'ifru_dstaddr' has incomplete type
/usr/include/linux/if.h:165: error: field 'ifru_broadaddr' has incomplete type
/usr/include/linux/if.h:166: error: field 'ifru_netmask' has incomplete type
/usr/include/linux/if.h:167: error: field 'ifru_hwaddr' has incomplete type
dm9601.c:53:31: error: linux/etherdevice.h: No such file or directory
dm9601.c:54:23: error: linux/usb.h: No such file or directory
dm9601.c:55:26: error: linux/module.h: No such file or directory
dm9601.c:56:20: error: dm9601.h: No such file or directory
dm9601.c:63: error: array type has incomplete element type
dm9601.c:71: error: array type has incomplete element type
dm9601.c:76: error: empty scalar initializer
dm9601.c:76: error: (near initialization for 'dm9601_ids')
dm9601.c:80: error: 'DM9601_AUTO' undeclared here (not in a function)
dm9601.c:81: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'reg5'
dm9601.c:84: error: expected declaration specifiers or '...' before string constant
dm9601.c:84: warning: data definition has no type or storage class
dm9601.c:85: error: expected declaration specifiers or '...' before string constant
dm9601.c:85: warning: data definition has no type or storage class

and, so on ...
how can i fix it ? i just want to compile it, and get the .ko file i can handle the other work :)
pls

---

