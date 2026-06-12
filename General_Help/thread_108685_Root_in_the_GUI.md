---
title: "Root in the GUI?"
date: 2005-12-26
forum: General Help
---

### Post by DKCO on 2005-12-26
When I log into Ubuntu, I give it my id and password.  However, once I log in, it's almost as if Ubuntu forgets who I am. I'm asked for my password at multiple other dialogues, and there are some tasks I can't even seem to perform at all outside of a terminal (deleting certain files).  I can open a root terminal which never asks for passwords - is there any way to do the same and have root access with the GUI?  Or maybe my account doesn't have the proper permissions set?  I just don't understand why I'm even providing a password in the first place if the OS isn't going to remember who I am.

All that to say, though, I'm a recent convert from Windows and like Ubuntu Linux enough to not go back :D  (except for certain OS specific applications).  It (Linux) just has a MUCH bigger learning curve. 

-DKCO

---

### Post by 23meg on 2005-12-26
The OS does remember who you are; it's just that you have to authenticate as superuser whenever you have to perform system-wide operations. Using the root account is discouraged and you should prefer sudo and its GUI equivalent, gksudo instead.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by DKCO on 2005-12-26
Thanks, that makes sense.

DKCO

---

