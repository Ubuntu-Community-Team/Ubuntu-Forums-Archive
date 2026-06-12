---
title: "error installing chmviewer gnochm:  Depends: python-gtkhtml2  but it is not installab"
date: 2010-10-15
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-10-15
I tried installing
System-->Administration-->Synaptics Package Manager
and  I got following error
```

gnochm:
 Depends: python-gtkhtml2  but it is not installable

```I am using Lucid  64 bit and in my sources.list 
multiverse,partner,universe,restricted and backports are enabled.

---

### Post by luvshines on 2010-10-15
Had this problem a couple of days ago. There is also a launchpad bug for this.
If you want to install gnochm, you'll have to download that package (.deb) and install it by dpkg.
It may complain of another dependency, for some libgtk..., that you can install from apt-get itself

But believe me, it is not worth all this trouble. I didn't find gnochm any worth. The fonts were too small.
**People have suggested xchm as a better alternate. I have installed that (apt-get), and it is pretty good. So I would say, drop gnochm and go for xchm**

---

### Post by tapas_mishra on 2010-10-15
Ok I installed kchmviewer

---

