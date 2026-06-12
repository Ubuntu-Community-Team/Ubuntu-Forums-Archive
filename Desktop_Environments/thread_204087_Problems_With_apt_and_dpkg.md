---
title: "Problems With apt and dpkg"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Johnsie on 2006-06-26
I wanted to install xchat but I got:
> 
john@st2:~$ sudo apt-get install xchat
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


So then I did:
> 
john@st2:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 5563 package `ubuntu-standard':
 `Depends' field, invalid package name `
john@st2:~$



Anyone know how to fix my problem? Thanks in advance :-)

---

### Post by Johnsie on 2006-06-26
bump

---

### Post by Johnsie on 2006-06-26
nevermind... I just deleted pretty much everything in /var/lib/dpkg

Apt-get is now working and finishing off my installation of ubuntu-desktop...

I have no idea what will happen.. I'm expecting some kind of breakage but it looks good so far :-)

---

