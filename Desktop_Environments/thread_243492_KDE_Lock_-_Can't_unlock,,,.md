---
title: "KDE Lock - Can't unlock,,,"
date: 2006-08-25
forum: Desktop Environments
---

### Post by lorenco on 2006-08-25
Pleas help....  It started since yesterday ?

After locking my KDE session I can not unlock it... it keeps on comming back telling me my password is not valid...

Only way to recover is to ctrl+alt+backsp and restart -- tried a couple of times already... ](*,)

---

### Post by lorenco on 2006-09-07
I Found the [following fedora post]("http://www.redhat.com/archives/fedora-test-list/2006-May/msg00044.html") after searching for the error in my xsession error log. 
> [INDENT]After this mornings upgrades, after my kde desktop locked (which I have
configured to do automatically), I could not unlock it.  This message may
be related:
X Error: BadAccess (attempt to access private resource denied) 10
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x2c0000e
WARNING: DCOPReply<>: cast to 'QStringList' error
WARNING: DCOPReply<>: cast to 'QString' error
------
[/INDENT]*it seems kcheckpass was not included in this version. I will push new  kdebase package in FC5 update ASAP which resolves this issue. *


Is kcheckpass included in the latest version ??

This started after the bad upgrade of xorg base a week or so ago.

---

### Post by lorenco on 2006-09-07
More info: 
I found another thread in the Solaris forum that had a samilar issue without resolution ???

I do have kcheckpass and it permissions  seems ok ?
Hovever it does not authenticate...

> kcheckpass; echo $?
Password:
Authentication failure
1

-rwxr-xr-x 1 root root 10992 2006-06-14 02:53 /usr/bin/kcheckpass


---

### Post by lorenco on 2006-09-07
SOLVED but must be a bug to fix...  !!! 

> ls -l /usr/bin/kcheckpass
-rwxr-xr-x 1 root root 10992 2006-06-14 02:53 /usr/bin/kcheckpass

***sudo chmod 4755 /usr/bin/kcheckpass  ***

ls -l /usr/bin/kcheckpass
-rw**s**r-xr-x 1 root root 10992 2006-06-14 02:53 /usr/bin/kcheckpass

kcheckpass; echo $?
Password:
0

Sticky!!! :)
:D

---

