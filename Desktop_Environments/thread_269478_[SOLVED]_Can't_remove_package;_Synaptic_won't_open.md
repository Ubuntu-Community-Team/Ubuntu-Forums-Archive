---
title: "[SOLVED] Can't remove package; Synaptic won't open"
date: 2006-10-01
forum: Desktop Environments
---

### Post by altonbr on 2006-10-01
```
user@computer:~$ sudo aptitude remove mfc8440lpr
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  **mozilla-firefox-locale-en-gb**
The following packages have been kept back:
  **amarok amarok-engines amarok-xine libssl0.9.8 openssl**
The following packages will be REMOVED:
  **mfc8440lpr**
0 packages upgraded, 0 newly installed, 2 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 713kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing mfc8440lpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
user@computer:~$
```

Some pretty screwy things have been happening to my box since ever since I got Ubuntu.. but I've been able to fix them all. This time, I tried to install the correct driver for my printer but the packaged didn't install correctly and now I can't remove it. When I open Synaptic I also get:

```
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

Also, why is it trying to remove those packages that have nothing to-do with my manually installed printer driver?

---

### Post by Mr Frosti on 2006-10-01
It sounds like "aptitude" is trying to remove packages that are not in use by anything. This is just a side operation that doesn't involve your printer driver package, other than it is bugging aptitude. 

Try using the following command:

```
sudo apt-get remove mfc8440lpr
```

If this doesn't work, try running a search for the "mfc8440lpr" utility to see if it is part of another package.

---

### Post by altonbr on 2006-10-02
Yeah, I've tried that, and this is what I get:

```
user@computer:~$ sudo apt-get remove mfc8440lpr
Password:
Reading package lists... Done
Building dependency tree... Done
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by altonbr on 2006-10-02
```
"mv /var/lib/dpkg/info/mfc8440lpr.postrm /var/lib/dpkg/info/mfc8440lpr.postrm-bak"

... which backs up the post removal script, its just good practice!

"dpkg --purge mfc8440lpr"

... get rid of it
```

I found this on google (although it was for taskjuggler and not mfc8440lpr)... it seemed to work.. but I have no idea what it did.. besides basically removing mfc8440lpr.postrm.. but it worked.. for now.

---

