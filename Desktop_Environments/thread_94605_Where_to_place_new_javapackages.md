---
title: "Where to place new javapackages?"
date: 2005-11-24
forum: Desktop Environments
---

### Post by Nasso on 2005-11-24
I got java 1.4 sdk running and working. I got some packages that i want to use when i create my programs though, by adding "import packagename.something.something.* " go the beginning of a class. In the same way that you can add java.util.LinkedList. 

My question is, where in the filesystem do i put these files?

---

### Post by Leif on 2005-11-24
you can place them wherever you want, as long as they're on your classpath when you compile files that reference them.

---

### Post by Nasso on 2005-11-25
okay, thanks. how do i set the classpaths then? i should set them to the directory that i have placed the .jar-file containing the packages?

---

### Post by Leif on 2005-11-25
run with : 
```

java  -classpath ".:path-to-your.jar" your-java-file

```

---

