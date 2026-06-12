---
title: "how to ls a file named &quot;--help&quot;"
date: 2009-06-04
forum: General Help
---

### Post by manoj_isi on 2009-06-04
I was wondering how to "ls" or "cat" or "rm" a file whose name is  "--help" ???

---

### Post by Chronon on 2009-06-04
I would give the absolute path to the file.

---

### Post by ibuclaw on 2009-06-04
> **manoj_isi said:**
> I was wondering how to "ls" or "cat" or "rm" a file whose name is  "--help" ???

```
ls ./--help
cat ./--help
rm ./--help

```

Regards
Iain

---

### Post by jenkinbr on 2009-06-04
cat ./--help
touch ./--help
ls ./--help
grep "some text" ./--help
rm ./--help

Basically, just use absolute path or the relative path ( ./ )

---

### Post by Chronon on 2009-06-04
Yeah, I guess relative paths work fine as well.  ;)

---

### Post by manoj_isi on 2009-06-04
right.. both absolute and relative paths will do.. 

also for 'rm'  : 
    $_ rm -- --help
will do.  (Source : man rm )

---

### Post by jenkinbr on 2009-06-04
Good point.  the optino '-- ' indicates to most programs that there are no options after.

May not work for all programs, though...

---

