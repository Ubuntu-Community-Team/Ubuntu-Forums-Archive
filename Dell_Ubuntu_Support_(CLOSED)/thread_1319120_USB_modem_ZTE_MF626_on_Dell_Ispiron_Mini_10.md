---
title: "USB modem: ZTE MF626 on Dell Ispiron Mini 10"
date: 2009-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tibalt-99 on 2009-11-08
Dear Sirs

I am not able to install ZTE MF 626 on Dell Ispiron Mini 10
The source thread: _[http://ubuntuforums.org/showthread.php?t=1302235](http://ubuntuforums.org/showthread.php?t=1302235)_
My config: [http://ubuntuforums.org/showpost.php?p=8212693&postcount=73](http://ubuntuforums.org/showpost.php?p=8212693&postcount=73)

What I see.
When I plug the device I see:

/dev$ ls -al | grep -i USB

> 
crw-rw----   1 root root    253,  15 2009-11-08 14:37 usbdev5.24_ep00
crw-rw----   1 root root    253,  16 2009-11-08 14:37 usbdev5.24_ep01
crw-rw----   1 root root    253,  17 2009-11-08 14:37 usbdev5.24_ep81
BUT I do not see anything like ttyUSB0
I have another modem, CDMA (AnyData ADU310A) - it works fine, and if I plug this modem - I am able to see ttyUSB0under /dev

Therefore I can not use gtkterm

Starting usb_modeswitch - does not appear to be helpfull 

Please assist!

Thank you

---

