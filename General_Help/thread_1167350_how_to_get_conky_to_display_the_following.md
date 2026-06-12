---
title: "how to get conky to display the following:"
date: 2009-05-22
forum: General Help
---

### Post by josephellengar on 2009-05-22
monthly download/upload statistics
version of operating system
version of gnome
anything else that you have that is really cool?

Thanks.

---

### Post by unutbu on 2009-05-22
You should be able to find all that you are looking for here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
or here:
[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

And this is just plain neat: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

---

### Post by frkblr on 2010-12-16
> **rossholley said:**
> monthly download/upload statistics
version of operating system
version of gnome
anything else that you have that is really cool?

Thanks.

What you can do is using nautilus like that:
${exec nautilus --version | egrep -m1 -o '[0-9]{1,2}\.[0-9]{1,3}\.[0-9]{1,2}'} :D

---

