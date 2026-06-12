---
title: "Frostwire not loading"
date: 2006-09-13
forum: Desktop Environments
---

### Post by nbpetts on 2006-09-13
OK, i have seen some varients of this problem, and i have tried all of the solutions to no avail.  I have installed Frostwire, and sun java 5.  when i open frostwire from the applications menu, nothing happens, and when i do it from the terminal, i get this error 

```
desktop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
```

i have tried converting the file as the frostwire forums suggested, but their error output doesnt look like mine, and anyway, it didnt work.  I also tried their new binaries, and reinstalling both java and frostwire.  any ideas?

nbpetts

---

### Post by amd6964 on 2006-09-14
Open into a terminal:
cd /usr/lib/frostwire && bash runFrost.sh :)

---

### Post by nbpetts on 2006-09-14
That works great, but i really want to know:  Why does this work?

---

