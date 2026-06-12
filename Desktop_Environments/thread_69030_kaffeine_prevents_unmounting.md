---
title: "kaffeine prevents unmounting"
date: 2005-09-25
forum: Desktop Environments
---

### Post by bongobonga on 2005-09-25
When I use kaffeine to view videos which I have saved on cdrom, I can unmount the cd afterwards. 
When I try to unmount the disk I get the message "umount: /media/cdrom0: device is busy". 
using 'fuser' on the device informs me that gam_server is using the device.  
So in order to unmount the disk I have to forcibily kill the gam_server, which may not be the ideal solution. 

This is a problem which only occurs with kaffeine. If I use xine, for example,  everything works fine. 

Is this a known problem, or should I file a bug report on this problems?

I am using the latest version of  kaffeine from
'http://kubuntu.org/pool/kaffeine/'

---

### Post by aysiu on 2005-09-25
[QUOTE=bongobonga]
Is this a known problem, or should I file a bug report on this problems?[/QUOTE] I've never encountered this problem, but before you file a bug report, you can search to see if it's already been filed.

---

