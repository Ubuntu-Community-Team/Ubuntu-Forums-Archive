---
title: "apt-cache search command problem"
date: 2009-02-28
forum: General Help
---

### Post by babyboss on 2009-02-28
Hello, Just wonder, if I want to search a package, with two key words such as "commandline" "graph" in the both package name or package description, how can I perform it with apt-cache search?

Thank you

---

### Post by khelben1979 on 2009-02-28
```
man apt-cache
```

---

### Post by NoReflex on 2009-02-28
From the man page : Separate arguments can be used to specify multiple search patterns that are and´ed together.

Or you could try something like :
  apt-cache search python | grep gtk

Best wishes,
NoReflex

---

### Post by geirha on 2009-02-28
```
apt-cache search commandline.*graph
```

---

