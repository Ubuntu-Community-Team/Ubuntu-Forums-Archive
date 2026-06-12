---
title: "Apt-get not working"
date: 2006-02-13
forum: Desktop Environments
---

### Post by varean on 2006-02-13
Right after I installed my system, I wanted to do an apt-get, so I did:
```
root@tux:/home/varean# apt-get install mozilla-firefox
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

However, there is no other process using that directory.  What's up with this?

---

### Post by nurdin on 2006-02-13
Sure you didn't have synaptic or another apt-get working at the same time? Just a thought.

---

### Post by astoltz on 2006-02-13
Yeah, that's a wierd error message...  It means you have to have admin privileges to use apt-get.  Try: ```
**sudo** apt-get install mozilla-firefox
```

EDIT:  Ooops... I didn't see the root prompt at the front, sorry.  The error message is similar when you try apt-get as a normal user.

---

### Post by %hMa@?b&lt;C on 2006-02-13
try 
```
killall apt synaptic
```
then try again

---

