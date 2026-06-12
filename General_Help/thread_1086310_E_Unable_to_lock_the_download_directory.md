---
title: "E: Unable to lock the download directory"
date: 2009-03-03
forum: General Help
---

### Post by nonewmsgs on 2009-03-03
for some reason about a month ago synaptic and add/remove stopped working but apt-get install still did.  apt-get install no longer does now.  

someone online told me to try
```

sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a 

```

but it doesn't help.  no update or install thing works.

---

### Post by dcstar on 2009-03-03
> **nonewmsgs said:**
> for some reason about a month ago synaptic and add/remove stopped working but apt-get install still did.  apt-get install no longer does now.  

someone online told me to try
```

sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a 

```

but it doesn't help.  no update or install thing works.
Try:
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by nonewmsgs on 2009-03-03
thanks dcstar!  it required both of these but after you gave me the first one, the second was easy to get logically :D


sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock

---

