---
title: "Where is my netbeans?"
date: 2009-02-11
forum: General Help
---

### Post by pedramslhr on 2009-02-11
I uninstalled Netbeans 6.5 yesterday and installed it again today.
but it is not in my home folder as was before(in fact I mean the default installation path) and I do not know where is it.
When I attempt to reinstall it, it says all the components are installed so click on cancel.

and I should say that it just happens when I use sudo to start installation from command line. but not without that!
maybe I should login as root to access netbeans, yes? and if yes do you recommend it.
and maybe I should unistall netbeans for root user? and again if I shoulld how?

---

### Post by lykwydchykyn on 2009-02-11
If you used sudo, check /opt, /usr/local, or /root.  It probably went one of those places.

EDIT: I just tried installing it.  It defaults to /usr/local

---

### Post by pedramslhr on 2009-02-11
> **lykwydchykyn said:**
> If you used sudo, check /opt, /usr/local, or /root.  It probably went one of those places.

EDIT: I just tried installing it.  It defaults to /usr/local
thank you.
yes it was in /usr/local and I uninstalled it succesfully(again using sudo)
thanks again!

---

### Post by sr20ve on 2009-02-11
for future reference, you can use the whereis command to locate where specific programs and documentation are located.

```
#whereis netbeans
```

---

