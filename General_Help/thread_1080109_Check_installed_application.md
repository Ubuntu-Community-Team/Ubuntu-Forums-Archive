---
title: "Check installed application"
date: 2009-02-25
forum: General Help
---

### Post by Embun_pagi on 2009-02-25
What should I do to check which applications or services already installed and running on ubuntu server without GUI?
thanks

---

### Post by x33a on 2009-02-25
to check for running processes,

```
ps aux
top
```

for a list of installed packages
```

dpkg --get-selections
```

you should pipe it to less or redirect to a file, because the output will be huge.

---

### Post by Embun_pagi on 2009-02-25
thanks

---

