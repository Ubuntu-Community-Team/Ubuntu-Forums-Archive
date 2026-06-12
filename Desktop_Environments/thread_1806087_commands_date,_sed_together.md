---
title: "commands: date, sed together ?"
date: 2011-07-17
forum: Desktop Environments
---

### Post by 71GA on 2011-07-17
Hello.

Can anyone tell me, what this returns and explain it a bit :)

```
date -u +%W$(uname)|sha256sum|sed 's/\W//g&#733;&#733;
```

---

### Post by ABCC on 2011-07-17
Surely that should be
```

date -u +%W$(uname)|sha256sum|sed 's/\W//g'

```

It calculates a sha sum of the date and the word Linux, then sed is used to only print the actual sum.

If you want to see it work, just run it step by step:
```

date -u +%W
date -u +%W$(uname)
date -u +%W$(uname)|sha256sum
date -u +%W$(uname)|sha256sum|sed 's/\W//g'

```

You could also use cut rather than sed:
```

date -u +%W$(uname) | sha256sum | cut -d' ' -f1

```

---

