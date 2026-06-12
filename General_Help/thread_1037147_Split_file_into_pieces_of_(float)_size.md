---
title: "Split file into pieces of (float) size"
date: 2009-01-11
forum: General Help
---

### Post by MartijnLoth on 2009-01-11
Hi everyone!

I'm trying to split a file into smaller pieces.
Naturally, I used the split command in Ubuntu:

```
split --bytes=9.5  test.txt part

```

Unfortunately, it does not seem to recognize floating points or comma's.
Does anyone know of another way?

Thanks!

---

### Post by heindsight on 2009-01-11
a file always contains a whole number of bytes. so you cannot create a file containing 9.5 bytes.

---

### Post by MartijnLoth on 2009-01-11
That makes sense. Much appreciated :)

---

