---
title: "gksu nautilus will not open"
date: 2012-06-07
forum: Desktop Environments
---

### Post by twiggy99 on 2012-06-07
Hi guys a bit of a noob here, I run gksu nautilus to change permissions to the usr/lib folder to put an app in there so it can launch from the unity bar. Now its messed up my ruby on rials install when ever I try and install a gem I get the following error: 

> sudo: /usr/lib/sudo/sudoers.so must only be writable by owner
sudo: fatal error, unable to load plug-insSo im guessing i need to change the permissions back to some default but when I put in the terminal  gksu nautilusnothing happens, the terminal just drops down to a new line and nothing opens. Any ideas?

---

### Post by traditionalist on 2012-06-07
> **twiggy99 said:**
> Hi guys a bit of a noob here, I run gksu nautilus to change permissions to the usr/lib folder to put an app in there so it can launch from the unity bar. Now its messed up my ruby on rials install when ever I try and install a gem I get the following error: 

So im guessing i need to change the permissions back to some default but when I put in the terminal  gksu nautilusnothing happens, the terminal just drops down to a new line and nothing opens. Any ideas?

I had some problems with gk commands. sudo nautilus works fine;

```
sudo nautilus
```

---

### Post by QIII on 2012-06-07
@traditionalist:  Open graphical applications with ***gksudo***.

See [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") for the whys and wherefores.

See the "error" comments at the bottom.

@twiggy99:  If you started changing permissions, we can't really begin to help without knowing what you did.

---

### Post by traditionalist on 2012-06-07
> **QIII said:**
> Open graphical applications with ***gksudo***.

See [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo") for the whys and wherefores.

See the "error" comments at the bottom.

If you started changing permissions, we can't really begin to help without knowing what you did.

Ah, I did not know about the bugs!  Will go back to gksudo.

---

### Post by Morbius1 on 2012-06-07
Um .... in Debian / Ubuntu gksudo = gksu:
> >> ls -l /usr/bin/gksudo
lrwxrwxrwx 1 root root 4 2010-05-18 07:19 /usr/bin/gksudo -> gksu


---

### Post by QIII on 2012-06-07
Yes.  I am aware of this.  I was responding to the suggestion to use sudo.

Previous post edited to clarify what was directed to whom.

---

### Post by Morbius1 on 2012-06-07
> **QIII said:**
> Yes.  I am aware of this.  I was responding to the suggestion to use sudo.

Previous post edited to clarify what was directed to whom.
Understood. My mistake.

---

### Post by QIII on 2012-06-07
No, my mistake.  I should have been more clear to begin with.  Mea culpa.

---

