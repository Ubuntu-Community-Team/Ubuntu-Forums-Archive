---
title: "Ubuntu, no internet connection"
date: 2006-01-16
forum: General Help
---

### Post by jago25_98 on 2006-01-16
Yes, I found this:
[http://www.ubuntuforums.org/showthread.php?t=57062&highlight=offline+udeb](http://www.ubuntuforums.org/showthread.php?t=57062&highlight=offline+udeb)

Let's say I want to get ndiswrapper-utils, how would I get apt-get to tell me where it would download it from? I don't want to search http repositories all the time trying to figure out if the package is in main or multiverse etc.

Thanks

---

### Post by AlanQ on 2006-01-16
I was wondering the same thing.
Then, when trying to install the free TrueType fonts, I came across a reply at [http://ubuntuforums.org/showthread.php?t=1261](http://ubuntuforums.org/showthread.php?t=1261)

Try 
```
sudo apt-cache show ndiswrapper-utils
```

Alan

---

