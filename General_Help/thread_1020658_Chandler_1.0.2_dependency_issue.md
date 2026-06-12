---
title: "Chandler 1.0.2 dependency issue"
date: 2008-12-24
forum: General Help
---

### Post by Reactor5 on 2008-12-24
Chandler 1.0.2 needs libicu36, but the version installed in 8.10 is libicu38.  How can I get this dependency to work?  I can compile the code, but I have no idea how to change the dependency.  Thanks!

---

### Post by cariboo on 2008-12-24
I just downloaded and extrated the tgz version and it runs without any dependency problems. You don't have to compile it. Once you have extracted the directory, I would suggest moving to /usr/local. like this:

```
sudo mv ~/sources/Chandler_linux_1.0.2 /usr/local/
```

You will have to change the path to where you extracted the directory. Then create a launcher either on your desktop or in the Applications menu.

Jim

---

