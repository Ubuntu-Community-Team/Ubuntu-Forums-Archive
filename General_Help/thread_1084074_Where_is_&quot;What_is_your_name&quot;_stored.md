---
title: "Where is &quot;What is your name&quot; stored?"
date: 2009-03-01
forum: General Help
---

### Post by larryalk on 2009-03-01
In the first question of step 5 of the installation process,
 (k)ubuntu asks "What is your name?".

Where is this item stored?

I can see it in /etc/passwd but suspect it is also stored
somewhere else on the system.

Is it possibly in the boot sector or buried in some unreadable file?
Or just a case of assigning user 1000 to that name and other programs pick it up when they need to know?

I've tried to grep the entire system but there are too many instances of that string and I think grep barfs.

Larry Alkoff

---

### Post by fragos on 2009-03-01
If youy want to do things with user names you should use the User & Group functions. What are you trying to accomplish?

---

### Post by Xiong Chiamiov on 2009-03-01
AFAIK, that's the only use of that particular field in /etc/passwd (or at least, most common), so I don't think it's stored anywhere else.

---

