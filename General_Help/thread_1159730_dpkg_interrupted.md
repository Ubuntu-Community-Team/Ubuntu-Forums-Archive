---
title: "dpkg interrupted"
date: 2009-05-15
forum: General Help
---

### Post by Crxss on 2009-05-15
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

This is the error I recieved when trying to install limewire. Now I can't install any programs at all. Is there a fix for this, or what can I do?

This has actually happened to me on another computer as well and I want to avoid having to reinstall ubuntu completely..

---

### Post by dtoronto on 2009-05-15
I don't believe that there is a .deb package for limewire and I'm pretty sure that it isn't in the Ubuntu repositories.  Are you trying to build this package from the source or run it through Wine.  It would be a little easier to assist you if you could provide more information about what it was that you were trying to do.

---

### Post by Crxss on 2009-05-15
limewire has a .deb package that's installable straight from their site, problem was that I didnt have sun java 6 installed for some reason, and it messed up limewire's installation and caused this error most likely.

---

### Post by bodhi.zazen on 2009-05-15
To fix that error message run:

```
sudo dpkg --configure -a
```in a terminal.

---

### Post by Crxss on 2009-05-15
it tells me --reconfigure is an unkown option.

---

### Post by bodhi.zazen on 2009-05-15
> **Crxss said:**
> it tells me --reconfigure is an unkown option.

my mistake, it is just --configure, see my updated post (above)

---

