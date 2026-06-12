---
title: "skype aborted by memory error"
date: 2006-09-09
forum: Desktop Environments
---

### Post by baosheng on 2006-09-09
Hi guys, I have use skype on ubuntu linux for quite a long time.
But today it doesn't work.

forrest@orioleQ:~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a211e0 ***
Aborted
forrest@orioleQ:~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a1eff0 ***
Aborted
forrest@orioleQ:~$ skype
*** glibc detected *** free(): invalid pointer: 0x08a1eba0 ***
Aborted

I installed the skype via the source
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

How can I fix the problem?

---

### Post by datelus on 2006-09-09
maybe try to completly removing skype using synaptic, and than install it again.Or other thing could be, look in system monitor, there sometimes ar like 3 or 4 skyps opened, so close them all, and try to lounch it again. in proceses. Worked for me once :)

---

### Post by baosheng on 2006-09-11
well, I found OpenOffice also has this problem. And your method works for OpenOffice but not Skype. :(

---

