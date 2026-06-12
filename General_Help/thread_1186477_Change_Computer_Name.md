---
title: "Change Computer Name"
date: 2009-06-13
forum: General Help
---

### Post by measekite on 2009-06-13
When installing Jaunty I gave the computer a name.  For example I named it "computer1".

How can I change this name to some other name that would still be associated with the IP address it has.

---

### Post by synapsys on 2009-06-13
/etc/hostname

---

### Post by change_mode on 2009-06-13
I think you need to edit both

/etc/hosts
/etc/hostname

---

### Post by Soul-Sing on 2009-06-13
computername (not login/username!) I think you have to adjust:
/etc/hosts and /etc/hostname

---

### Post by Soul-Sing on 2009-06-13
lol

---

### Post by measekite on 2009-06-13
> **synapsys said:**
> /etc/hostname

Thanks.  That worked.  I assume it will still be associated with the same IP address.

One more question:

Isn't there a choice in the menu system that would allow you to do that without going into the file system to edit the file?

---

### Post by synapsys on 2009-06-13
Not that I'm aware of, although I'm on a windows xp box right now so I can't check. Most of the google results talk about editing /etc/hostname.... so I doubt it.

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

