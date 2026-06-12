---
title: "apt-cache search doesn't work"
date: 2006-03-01
forum: Desktop Environments
---

### Post by m666 on 2006-03-01
I noticed strange thing recently, 'apt-cache search' and 'apt-cache show' don't work properly.
Example:
both 'apt-cache search gnome-utils' and 'apt-cache show gnome-utils' show no results.
'apt-get search gnome' lists some packages but not as many as before.
'sudo apt-get install gnome-utils' works though!
what happend???
shall I reinstall APT? If so, how can I do it?
(sources.list checked, apt-get updated)
without 'search' apt is useless! :(

---

### Post by RAOF on 2006-03-01
You can also search with "aptitude" -
```
aptitude search gnome-utils
aptitude show gnome-utils
```
Does that work as expected?

---

### Post by m666 on 2006-03-01
aptitude works fine

---

### Post by RAOF on 2006-03-01
Well, there's a work around, at least ;)

I'm not sure why apt-cache wouldn't work, but aptitude does exactly the same job.  Plus, you can use it to install/remove/purge stuff, too.

---

### Post by cwaldbieser on 2006-03-01
[QUOTE=m666]I noticed strange thing recently, 'apt-cache search' and 'apt-cache show' don't work properly.
Example:
both 'apt-cache search gnome-utils' and 'apt-cache show gnome-utils' show no results.
'apt-get search gnome' lists some packages but not as many as before.
'sudo apt-get install gnome-utils' works though!
what happend???
shall I reinstall APT? If so, how can I do it?
(sources.list checked, apt-get updated)
without 'search' apt is useless! :([/QUOTE]

Did you maybe clear out the package cache sometime ago?  You could try regenerating it.

---

### Post by m666 on 2006-03-02
I've just discovered that apt-cache works, but only for root! :???: 
(sudo apt-cache)

---

### Post by Ramses de Norre on 2006-03-02
It works without sudo for me, maybe the permissions on /usr/bin/apt-cache are set wrong, make it executable for you.

---

### Post by m666 on 2006-03-02
```
$ ls -l /usr/bin/apt-cache
-rwxr-xr-x  1 root root 89000 2005-10-05 14:40 /usr/bin/apt-cache

```
seems to be ok
lets check sources.list

```
$ ls -l /etc/apt/sources.list
-rwx------  1 root root 1216 2006-03-02 11:43 /etc/apt/sources.list
```

here it is!

```
$ sudo chmod +r /etc/apt/sources.list
```

now it works! thanx for help!!!

(I think the permission had changed after I used Automatix for a second time, but I can't be sure)

---

