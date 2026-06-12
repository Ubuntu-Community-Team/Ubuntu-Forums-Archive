---
title: "Piping find into grep"
date: 2009-05-20
forum: General Help
---

### Post by Vyder on 2009-05-20
I am trying to search all the java files in a particular folder for a string "text".

Here's what I've got that doesn't work. The two commands work seperately, but not when I pipe one into the other.

```
find java-folder/ -name "*.java" | grep text-to-find
```

Why?

---

### Post by unutbu on 2009-05-20
Try this:```


find java-folder/ -name "*.java" -exec grep -l text-to-find {} \;

```
or
```

find java-folder/ -name "*.java" | xargs grep text-to-find
```

---

### Post by Vyder on 2009-05-20
the first one worked, the second one didn't.

I removed the -l switch to get the lines themselves.

Could you please explain what the "-exec" and the "{} \;" mean?

Thanks!

---

### Post by asmoore82 on 2009-05-20
> **Vyder said:**
> the first one worked, the second one didn't.

I removed the -l switch to get the lines themselves.

Could you please explain what the "-exec" and the "{} \;" mean?

Thanks!

-exec tells find to run a command when it finds a match
the name of the match is substituted for {}
the ; terminates the -exec statement for find, but it must be hidden from the shell with \

that second one should be like this:
```
find java-folder/ -iname "*.java" -print0 | xargs -0 grep text-to-find
```

---

### Post by wirelessmonkey on 2009-05-20
Just for fun, but you could double grep... 

```
 find java-folder/ | grep text-to-find | grep java 
```

---

### Post by Vyder on 2009-05-20
that seems to work. what does the "-print0" and "-0" switches mean?

---

