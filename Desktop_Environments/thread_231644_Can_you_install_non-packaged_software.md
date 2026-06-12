---
title: "Can you install non-packaged software?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by necro351 on 2006-08-07
In Ubuntu, where is the best place to install non-packaged software? Is there a pre-designated spot for that (e.g., /usr/local)? I need to know so I can properly set --with-prefix during ./configure of my software.

---

### Post by fdoving on 2006-08-07
/usr/local or /opt is OK. That way the packaging system won't overwrite your files.

- Frode

---

