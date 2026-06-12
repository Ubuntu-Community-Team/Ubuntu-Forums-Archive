---
title: "[Kubuntu] sudo plasma-desktop brought me &quot;system problem detected&quot; error (I think)"
date: 2014-06-12
forum: Desktop Environments
---

### Post by chuckyanutsup on 2014-06-12
I run kde on top of ubuntu studio. The other day in a misguided attemt to run plasma-desktop, I ran it as sudo. This has caused an error on launch of xfce and kde sessions. I can reproduce the error by running 
```
sudo apt-get install --reinstall upstart

```
I get a "sytem problem detected" prompt.
I'm not sure where to go with troubleshooting from here. I suspect a permissions issue as it's present over multiple desktop environments.

---

### Post by chuckyanutsup on 2014-06-12
That was weird. I ran the above command a few more times to test, and now the problem appears to be corrected.

---

### Post by chuckyanutsup on 2014-06-22
I'm wondering if I've broken anything else by running sudo plasma-desktop. Any thoughts folks?

---

