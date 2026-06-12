---
title: "HELP installing this program"
date: 2005-12-16
forum: Desktop Environments
---

### Post by majkmil on 2005-12-16
Hi, I downloaded a program called VMWare Player. It's a program to make iteasy to run a virtual machine. There is a folder named installer, the only file in it is ( services.sh) can anyone help me install this prog. Thank You

---

### Post by soulestream on 2005-12-16
[http://ubuntuforums.org/showthread.php?t=84275&highlight=vmware](http://ubuntuforums.org/showthread.php?t=84275&highlight=vmware)


soule

---

### Post by HermanAB on 2005-12-16
First off, installing complex things like a VM may not be easy, so if you can't get it to work at all, don't feel bad about it.

Since it seems to be a script, all you probably need to do is run it.  I would first try to run it as a common user and based on what it reports, maybe run it as super user, but only if the machine you are running it on is a development machine and isn't doing anything important.

To run a script, you have to first set the executable flag:
$ cd where/ever/it/is
$ chmod 775 services.sh

then try to run it:
$ ./services.sh

If nothing happens, look at the first line of the script:
$ head services.sh

the first line should be something like:
#! /bin/bash

If not, change it to that with an editor and try to run it again.

To run a script as super user:
$ sudo su -
password
#

Now do the same as the above.

'Hope this helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by majkmil on 2005-12-16
Thanks, Great tutorial. Have you ever ran a vurtual machine on top of ubuntu? How about XP?

---

