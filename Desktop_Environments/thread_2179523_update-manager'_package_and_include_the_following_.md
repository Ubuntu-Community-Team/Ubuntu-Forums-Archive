---
title: "update-manager' package and include the following error message:"
date: 2013-10-08
forum: Desktop Environments
---

### Post by rdema19403 on 2013-10-08
I am running ubuntu 12.04 lts 64 bit any how I went to install adobe reader 9.5.5-1 I 386 Linux enu.deb file I started to install it but thought I read somewhere that 32 bit would not work on a 64 bit system so I shut the computer down now I cannot access Ubuntu software center an error occurred please run package manager from the right click menu or apt-get terminal to see what is wrong the error message
unknown error


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package adobe reader-enu:i386 needs to be reinstalled, but I can't find an archive for it.' any ideas on what to do ?
Thanks in advance Ralph

---

### Post by grahammechanical on 2013-10-08
Ubuntu since 12.04 has what are called Multi- arch libraries. This is what they do

> [COLOR=#333333][FONT=Ubuntu]If you have any need for 32-bit programs on a 64-bit system, then lots of library packages need to be installed for 32-bit support (denoted by "(i386)" in the package name) in addition to their native 64-bit versions. Multi-arch is a new way of handling this developed by Debian. [/FONT][/COLOR]

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

Have you tried re-installing that deb package by right clicking on the  deb package and selecting to open with Software Centre? I think that the archive you are looking for is that deb package.

Regards.

---

### Post by rdema19403 on 2013-10-08
package manager will not run it trys to start then disappears

---

### Post by rdema19403 on 2013-10-08
i tried to use the software center it starts up then disappears

---

### Post by rdema19403 on 2013-10-09
Ubuntu software center has closed unexpectedly 
/usr/share/software-center/software-center any ideas what to do

---

