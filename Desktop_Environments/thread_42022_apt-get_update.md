---
title: "apt-get update"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-15
Setting up gnomebaker (0.3-3) ...

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
dave@D5:~$ sudo apt-get update gnomebaker
E: The update command takes no arguments
dave@D5:~$


What? :(

---

### Post by desdinova on 2005-06-15
I think they're having server issues at the moment

---

### Post by Dave_is_sexy on 2005-06-15
oh good :)

---

### Post by r0ydster on 2005-06-15
Per other members on this board:

The nermin.net server has changed its directory structure. As noted at [ftp://ftp.nerim.net/debian-marillat/index.html](ftp://ftp.nerim.net/debian-marillat/index.html) the former structure (stable, testing, unstable) has been changed to sarge, etch, sid. By changing /etc/apt/sources.list from:


deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

to

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sarge main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sid main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) etch main

will fix the errors.  

Once the sources.list file is changed and saved, just re-run apt-get update (as root, of course), and you should be good to go.

Hope this helps,

Mike

---

### Post by Dave_is_sexy on 2005-06-15
so

apt-get update

is like

apt-get install

? Computer says no ;)

---

### Post by desdinova on 2005-06-15
As I understand it, update does some housekeeping....

---

### Post by r0ydster on 2005-06-15
[QUOTE=Dave_is_sexy]so

apt-get update

is like

apt-get install

? Computer says no ;)[/QUOTE]

Once the /etc/apt/sources.list file is updated, when you run apt-get update, it will hit the marillat servers this time, and "update" the list of package updates.

Then to "update" the previously installed marillat packages, you need to run apt-get upgrade.

apt-get install *package_name* would install *package_name* from the first available repository.  

apt-get install is usually used to install a package that one knows the name of.

Hope that helps!

Mike

edit: type man 8 apt-get in a terminal window for more detailed info.

---

