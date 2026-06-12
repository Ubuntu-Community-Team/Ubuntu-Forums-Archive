---
title: "'make' command not found"
date: 2005-12-15
forum: General Help
---

### Post by Granduke on 2005-12-15
I'm trying to do my first compile but the 'make' command gives me "make: command not found". Tried it under sudo and still nothing. Other commands such as 'apt-get' and 'install' do work. I've tried restarting to no avail.

---

### Post by tlc on 2005-12-15
Do this:
```
sudo apt-get install build-essential
```
Should then work.

---

### Post by Granduke on 2005-12-15
Thanks tlc,

                That fixed it.

---

### Post by Snoopy2052 on 2005-12-15
I had exactly this problem yesterday!

---

