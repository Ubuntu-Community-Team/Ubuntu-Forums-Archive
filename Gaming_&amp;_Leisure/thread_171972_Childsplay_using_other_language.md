---
title: "Childsplay: using other language"
date: 2006-05-07
forum: Gaming &amp; Leisure
---

### Post by fnando on 2006-05-07
Hi. How can I use Childsplay with another language?
I installed Portuguese language (sounds), but I don't know how to activate it.

---

### Post by kgeis on 2009-11-13
3 1/2 years late, but I figured an answer might help someone.  It took me some digging to figure it out.  You can use the LANGUAGE environment variable.  So from the command line, you would

```
LANGUAGE=pt childsplay
```

---

### Post by angelsguitar on 2009-12-31
> **kgeis said:**
> 3 1/2 years late, but I figured an answer might help someone.  It took me some digging to figure it out.  You can use the LANGUAGE environment variable.  So from the command line, you would

```
LANGUAGE=pt childsplay
```

Thanks, I've been looking to an answer for this for a long time. In my case, I used

```
LANGUAGE=es childsplay
```

to launch it in spanish succesfuly.

Thanks again!

---

### Post by angelsguitar on 2009-12-31
Just discovered another way. When launching the program, use the --language=LANG option.  For example, to launch childsplay in spanish, use

```
childsplay --language=es
```

This works on the newer version from schoolplay; not sure if it would work on the older version.

Hope this helps someone.

---

