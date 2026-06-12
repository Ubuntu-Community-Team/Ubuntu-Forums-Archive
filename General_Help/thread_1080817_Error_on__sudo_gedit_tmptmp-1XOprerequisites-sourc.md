---
title: "Error on  sudo gedit tmp/tmp-1XO/prerequisites-sources.list"
date: 2009-02-25
forum: General Help
---

### Post by Pinejoker on 2009-02-25
Could some tell me why i cant save a file on  sudo gedit tmp/tmp-1XO/prerequisites-sources.list????


Could not save the file /home/family/tmp/tmp-1XO…rerequisites-sources.list.

Unexpected error: File not found

---

### Post by snova on 2009-02-25
> **Pinejoker said:**
> Could some tell me why i cant save a file on  sudo gedit tmp/tmp-1XO/prerequisites-sources.list????


Could not save the file /home/family/tmp/tmp-1XO&#8230;rerequisites-sources.list.

Unexpected error: File not found

Perhaps a missing leading slash?

```
gksudo gedit /tmp/tmp-1XO/prerequisites-sources.list
```

You should use gksudo for graphical programs, by the way.

---

### Post by Pinejoker on 2009-02-26
Ah thanks, I already fixed it =)

---

