---
title: "grep and rm"
date: 2009-02-05
forum: General Help
---

### Post by cybo on 2009-02-05
i'm trying to remove files in my directory using ls, grep and rm but for some reason it doesn't work.

example:
say my directory has the following contents

test1 test2 test3 test4

>> ls | grep test | rm -f

it doesn't work. after executing this command i cant still see all my files.

does anyone understand why this is happening?

---

### Post by Dies on 2009-02-05
Because what your piping into rm isn't what it expects, use xargs

ls | grep test | xargs rm -f

or better yet skip all the pipes and use rm directly

rm -f test*

since the result would be the same for your example.

---

### Post by FearlessPc on 2009-02-05
Hi

I use the command find for this.
With your example i will do:

```
find /the/path  -maxdepth 1 -type f -name "test*" -exec rm -v {} \;

```

also read
```
man find
```

Its a great command!

---

### Post by cybo on 2009-02-05
thank you everyone for your help

---

