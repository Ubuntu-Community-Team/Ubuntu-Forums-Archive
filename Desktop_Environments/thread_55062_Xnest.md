---
title: "Xnest"
date: 2005-08-07
forum: Desktop Environments
---

### Post by awilisch on 2005-08-07
I'm trying to get a nested xsession to a Solaris 9 server up and running for remote administration purposes. if I just type 

X :1 -query cube03

The session comes up fine allowing me to login and do whatever I want. However if I type this:

Xnest :1 -query cube03

It opens the session and gives me the login screen. however when I try to login it goes blank for a moment, then takes me right back to the login prompt. The /var/dt/Xerrors file gives me the following errors:
/usr/openwin/bin/xset:  bad font path element (#40), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
/usr/openwin/bin/xset:  bad font path element (#40), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
/usr/openwin/bin/xset:  bad font path element (#40), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
/usr/openwin/bin/xset:  bad font path element (#40), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-dt-interface system-medium-r-normal-l*-*-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-dt-interface user-medium-r-normal-l*-*-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-dt-interface system-medium-r-normal-xxl*-*-*-*-*-*-*-*-*" to type FontSet
Warning: Null child found in argument list to unmanage

Any help is appreciated.
Aric

---

