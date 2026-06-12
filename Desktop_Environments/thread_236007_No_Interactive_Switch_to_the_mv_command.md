---
title: "No Interactive Switch to the mv command?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by jackn on 2006-08-14
Can't seem to get the -i switch to the 'cut' command to work:

```
:~/experimental$ ls
garrels-script  test  test2
:~/experimental$ mv -i test test.del
:~/experimental$ ls
garrels-script  test.del  test2
```

Clearly, the renaming gets done without prompting the user.

?...

Thanks.

Jackn

---

### Post by Jussi Kukkonen on 2006-08-14
from *man mv*:
>        -i, --interactive
              prompt before overwrite

It only prompts if the new file already exists

---

### Post by jackn on 2006-08-14
Thanks a bunch, Jussi.

Jackn

---

