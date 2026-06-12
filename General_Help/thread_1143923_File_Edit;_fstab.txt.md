---
title: "File Edit; fstab.txt"
date: 2009-04-30
forum: General Help
---

### Post by vaughnm on 2009-04-30
I want to edit the fstab.txt file in File System>ect but it's says I need to be root in order to do this.
I read online that you can get your Ipod touch to work if you add a line to this file. The only problem is...it won't let me edit it. Any ideas guys?

Here the link to the site. 
[http://blog.taragana.com/index.php/archive/use-iphone-and-ipod-touch-for-ubuntu-810/#comment-505937]("http://blog.taragana.com/index.php/archive/use-iphone-and-ipod-touch-for-ubuntu-810/#comment-505937")

---

### Post by taurus on 2009-04-30
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
p.s.  It's /etc/fstab, not /etc/fstab.txt.

---

### Post by vaughnm on 2009-04-30
Cool, that did it. 
And thanks for the tip :)

---

