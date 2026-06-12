---
title: "C++ compiler"
date: 2009-06-03
forum: General Help
---

### Post by Baconfatty on 2009-06-03
Does anyone know of a good C++ compiler?

---

### Post by Mikeee on 2009-06-03
You need to install g++.

If you want an ide try looking into codeblocks. It probably isnt the most popular but I enjoy using it

---

### Post by colau on 2009-06-03
> **Baconfatty said:**
> Does anyone know of a good C++ compiler?
```

sudo aptitude install g++ 
sudo aptitude install gcc

```

---

### Post by x33a on 2009-06-03
install build essential package, it'll install gcc.

```
sudo aptitude install build-essential
```

To use g++

> g++ filename.cpp -o filename

also, take a look here:

[http://ubuntuforums.org/showthread.php?t=796493](http://ubuntuforums.org/showthread.php?t=796493)

---

### Post by Baconfatty on 2009-06-03
ok I got g++ and gcc, but where is it? Sorry I'm used to visual studio 2005.

---

### Post by colau on 2009-06-03
> **Baconfatty said:**
> ok I got g++ and gcc, but where is it? Sorry I'm used to visual studio 2005.
To compile with g++ 
```

g++ filename.cpp -o filename

```
To run the file
```

./filename

```
See 
```

man g++

```

If you want a graphical IDE for C++ you can use codelite.
```

sudo aptitude install codelite

```
You can also use netbeans.
From System>Administration>Synaptic Package Manager.
Search netbeans.
Install it then running netbeans install C/C++ plugins from tools>plugins>C/C++ plugins.

---

### Post by Baconfatty on 2009-06-03
ok I got it now, thank you.

---

### Post by colau on 2009-06-03
Welcome.

---

