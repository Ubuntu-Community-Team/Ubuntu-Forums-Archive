---
title: "Python 2.6 instead of 2.5 seems like a big mistake to me."
date: 2009-04-27
forum: General Help
---

### Post by Mamsaac on 2009-04-27
There are several bugs that are happening because of that. Not only is now alarm clock causing a system freeze, but also other activities. I was wondering if there was a way to safely get rid of it?

---

### Post by Hellstudios on 2009-04-27
There is both version 2.5 and 2.6 in the repositories, simply just uninstall the 2.6 version and install 2.5.

---

### Post by Mamsaac on 2009-04-27
Nothing will break? If no new apps depend on Python 2.6, then I will do that.

Thanks.

---

### Post by blackened on 2009-04-27
> **Hellstudios said:**
> There is both version 2.5 and 2.6 in the repositories, simply just uninstall the 2.6 version and install 2.5.

You could give it a try, but I'm fairly certain that most of the core packages have been updated to depend explicitly on Python 2.6. The likelihood that you'll trash your entire system is very high.

Run a simulated uninstall of python and see what happens:

```
sudo apt-get remove -s python
```

---

### Post by Mamsaac on 2009-04-27
After reading a little, it's not a good idea to get rid off 2.6

And it seems that it is also a very bad a idea to install both 2.5 and 2.6

In other words, I'm stuck with the bugs 2.6 is causing. =(

---

