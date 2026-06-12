---
title: "New to it help!! (Updating Isue)"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Eyan on 2006-06-02
Hi, i am new to linux and i want to know if can download updates and copy it to a cd to load on my system at home where i don't have an internet connection.
If so how do i go about it. 
PS. I loaded the 6.06 last night on my pc looks great.

---

### Post by karthik085 on 2006-06-02
[QUOTE=Eyan]Hi, i am new to linux and i want to know if can download updates and copy it to a cd to load on my system at home where i don't have an internet connection.
If so how do i go about it. 
PS. I loaded the 6.06 last night on my pc looks great.[/QUOTE]
You can download all the packages, source code, etc and load into your home pc.

For .deb, package installation, sudo dpkg -i <package names>

---

### Post by MarcDM on 2006-06-02
[QUOTE=Eyan]Hi, i am new to linux and i want to know if can download updates and copy it to a cd to load on my system at home where i don't have an internet connection.
If so how do i go about it. [/QUOTE]


I think what you're looking for is APT-ZIP.  From the package description :

> 
These scripts simplify the process of using dselect and apt on a
non-networked Debian box, using removable media like ZIP floppies and
USB keys.
One generates a `fetch' script (supporting backends such as wget and
lftp, in a modular, extensible way) to be run on a host with better
connectivity, check space constraints of your removable media, and
then install the package on your Debian box.

And here's the manpage.
[http://debian.pffa.de/ger/howto/apt-zip.html](http://debian.pffa.de/ger/howto/apt-zip.html)

I hope this helps.

---

