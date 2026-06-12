---
title: "Cannot install packages because of dependency problems"
date: 2006-06-18
forum: Desktop Environments
---

### Post by peletomi on 2006-06-18
Hello All,

I have installed Xubuntu on my computer, and I wanted to add some additional stuff like openoffice, gtk vim etc. In both cases synaptic says they are not going to install because of some dependency problem:

```
openoffice.org2:
 Depends: openoffice.org2-writer but it is not going to be installed
 Depends: openoffice.org2-base but it is not going to be installed
```

Can somebody help me with this, it is somewhat urgent?

Thank you in advance!

pele

---

### Post by aysiu on 2006-06-18
Dependency problems usually stem from conflicting repositories.

Get a fresh set here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Make sure to click **Reload** in Synaptic before trying to install that stuff again.

---

### Post by peletomi on 2006-06-18
Thank you! You were right, it seems that EasyUbuntu changed my repos to Breezy. :/

---

