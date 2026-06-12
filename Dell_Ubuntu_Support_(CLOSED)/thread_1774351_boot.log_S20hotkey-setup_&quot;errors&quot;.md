---
title: "boot.log S20hotkey-setup &quot;errors&quot;"
date: 2011-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Old_Brewer on 2011-06-03
Hi all  
I'm using a Dell Inspiron B130 & Ubuntu 10.04 (lucid), kernal linux 2.6.32-32 generic, GNOME 2.30.2.

I have noticed the following in the boot.log:

fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 251079/4702208 files, 2116722/9396009 blocks 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
 * Setting sensors limits       [80G  [74G[ OK ] 
 * Doing Wacom setup...       [160G  [154G[ OK ] 
/etc/rc2.d/S20hotkey-setup: line 58: /usr/sbin/dumpkeycodes: No such file or directory 
/etc/rc2.d/S20hotkey-setup: line 64: /usr/share/hotkey-setup/key-constants: No such file or directory 
/etc/rc2.d/S20hotkey-setup: line 89: /usr/share/hotkey-setup/dell.hk: No such file or directory 
/etc/rc2.d/S20hotkey-setup: line 149: /usr/share/hotkey-setup/generic.hk: No such file or directory 
 [33m*[39;49m Speech-dispatcher configured for user sessions 
 * Starting Network connection manager wicd       [160G 

Should I be concerned with the lines ending in:  No such file or directory?
The errors might have started after I used the cleanup program BleachBit.

Thanks

---

