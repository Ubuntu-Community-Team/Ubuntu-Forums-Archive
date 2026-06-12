---
title: "edit iso file with dd"
date: 2006-01-16
forum: General Help
---

### Post by stoeptegel on 2006-01-16
Hi guys,

I was wondering if it's possible to edit files on a iso file with dd command(or such). I could only find articles on making images of cd's or floppy, but not editing.

Thanks for all hints.

---

### Post by Billquinn1 on 2006-01-16
Have you tried Kiso? I think it is in the repos.

EDIT: I did not see it in the repos but you should be able to download it here
[http://kiso.sourceforge.net/index.php](http://kiso.sourceforge.net/index.php)

---

### Post by ardchoille on 2006-01-16
Is it possible to just mount an ISO file, add/remove files to/from it, unmount it and it all works?

---

### Post by ioannis.th on 2006-01-17
No because by definition, an iso image is representing a readonly ISO9660 filesystem (cd-rom). However, you can edit the iso with an appropriate application and add/remove data as a second, third, etc session.

As for the dd command I have never heard or imagined it could be used to edit ISOs. I don't think it is possible.

---

### Post by stoeptegel on 2006-01-18
Sorry for the late response. (too much work)

I will definitely try kiso when i have time.

Thanks for this tip.

---

### Post by cas118 on 2007-12-23
I know that this is from ages ago - but for anyone who's still looking, ISO Master does the job in a nice, easy GUI:

```
sudo apt-get install isomaster
```

---

### Post by stoeptegel on 2007-12-30
There is also [isotoneiso2](http://kde-apps.org/content/show.php/Acetoneiso2?content=71954) now...

---

