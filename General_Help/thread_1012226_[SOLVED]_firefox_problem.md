---
title: "[SOLVED] firefox problem"
date: 2008-12-15
forum: General Help
---

### Post by melenor on 2008-12-15
The font used in firefox, only in firefox, no makes everything look like it is tabbed instead of spaced, but i did not change any settings i just restarted my computer and when it restarted firefox was like this. please help.

---

### Post by fooman on 2008-12-15
could you post a screenshot?

---

### Post by melenor on 2008-12-15
okay. it gives me a headache.

---

### Post by fooman on 2008-12-15
seen this before...you need to remove the "pango-graphite" package if it is installed.

first close firefox if it is open.  then type or copy/paste the following into a terminal:

```
sudo apt-get remove pango-graphite
```

press enter followed by your password.

hope that fixes it.

---

### Post by melenor on 2008-12-15
thank you so much, it was giving me a head ache. btw what is pango-graphite, i am not quite sure why it was installed.

---

