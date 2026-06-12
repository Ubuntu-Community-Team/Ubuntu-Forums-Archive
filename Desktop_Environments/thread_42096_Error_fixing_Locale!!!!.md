---
title: "Error fixing Locale!!!!"
date: 2005-06-16
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-16
Hey, I searched some threads to fix this, but nothing worked.  

Getting this error:
ocale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

So i try and do this:
chase@ubuntu:~$ sudo apt-get install locales localeconf
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  locales: Depends: glibc-2.3.2.ds1-20ubuntu13
E: Broken packages
chase@ubuntu:~$       

tried to apt-get instasll glibc* and it said ::

chase@ubuntu:~$ sudo apt-get install glibc-2.3.2.ds1-20ubuntu13
Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6 instead of glibc-2.3.2.ds1-20ubuntu13
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.

Help!!

---

### Post by Knome_fan on 2005-06-16
Could it be that you have the same problem discussed in the following thread?
[http://www.ubuntuforums.org/showthread.php?t=41929](http://www.ubuntuforums.org/showthread.php?t=41929)

Hope this helps. :-D

---

### Post by vtechstu on 2005-06-17
Hey, similar problem, but i managed to fix my bug.  The error was due to the wrong version of njb6c or whatnot.  I manually downloaded the ubuntu13 version 20 file and installed it over top of the version 22 i got off another site.  I then did

sudo apt-get install locales localeconf
sudo apt-get update

Version 22 is required to getting Creative micro zen working, but i guess i'll have to find another way, since that didn't seem to work either.

Bottum line it's fixed :).

---

