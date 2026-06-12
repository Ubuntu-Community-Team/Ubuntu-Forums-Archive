---
title: "gnome-system-tools - Where is shares-admin? (ubuntu 8.04 beta)"
date: 2008-04-01
forum: Desktop Environments
---

### Post by yyongpil on 2008-04-01
I'm using ubuntu 8.04 beta and gnome 2.22.0.
gnome-system-tools package is installed but I cannot find shares-admin (System - Administration - Shares). :confused:
The description of gnome-system-tools package and gnome online manual 2.22.0 also says it includes shares-admin.
Does anyone know wheather shares-admin exists in the package gnome-system-tools?

```
$shares-admin

The program 'shares-admin' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-system-tools
bash: shares-admin: command not found

$sudo apt-get install gnome-system-tools

[sudo] password for user:
Reading package lists... Done
Building dependency tree
Reading state information... Done
gnome-system-tools is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$
```

---

### Post by warp99 on 2008-04-01
The file should be in /usr/bin according to the package list:

[http://packages.ubuntu.com/hardy/i386/gnome-system-tools/filelist](http://packages.ubuntu.com/hardy/i386/gnome-system-tools/filelist)

you should reinstall the package with the following parameters:

```
sudo apt-get install --reinstall gnome-system-tools
```

This should work. If not you can download the package and install it from the command line:

[http://packages.ubuntu.com/hardy/i386/gnome-system-tools/download](http://packages.ubuntu.com/hardy/i386/gnome-system-tools/download)

```
sudo dpkg -i gnome-system-tools_2.22.0-0ubuntu5_i386.deb
```

Edit:

If that fails you can do the following:

```
echo "gnome-system-tools install" | sudo dpkg --set-selections
```

followed by:

```
sudo apt-get dselect-upgrade
```

---

### Post by lilian on 2008-04-02
I tried the reinstall command that upgrade the package gnome-system-tools. But there is no "shares-admin" command in my system.

I downloaded the package and opened it with gdebi but the list of files doesn't contain the command "shares-admin"...

How could I configure my network shares ?

---

### Post by yyongpil on 2008-04-02
warp99 // I'm asking wheather the package contains shares-admin..
Thanks though.

lilian // That's what I wanted to ask. The description of the package says it contains shares-admin but it doesn't really contain shares-admin.

---

### Post by warp99 on 2008-04-02
Well the file list says the file is in the package:

[http://packages.ubuntu.com/search?searchon=contents&keywords=shares-admin&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=shares-admin&mode=exactfilename&suite=hardy&arch=any)

I did download the .deb and extract the program for Hardy and yes it's missing:

```
ls -oh
total 372K
-rwxr-xr-x 1 117K 2008-04-01 01:04 network-admin
-rwxr-xr-x 1   61K 2008-04-01 01:04 services-admin
-rwxr-xr-x 1   93K 2008-04-01 01:04 time-admin
-rwxr-xr-x 1   92K 2008-04-01 01:04 users-admin

```

According to this bug report it's been changed to nautilus-share:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480)

so shares-admin has been deprecated and replaced with nautilus-share in Hardy.

---

### Post by lilian on 2008-04-03
INMHO it is a bad idea... Maybe nautilus-share is good for sharing a folder but I cannot manage all my network shares easily :(

I hope shares-admin will come back !!

---

