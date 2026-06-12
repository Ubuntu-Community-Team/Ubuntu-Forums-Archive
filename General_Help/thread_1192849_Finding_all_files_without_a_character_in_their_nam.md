---
title: "Finding all files without a character in their name"
date: 2009-06-20
forum: General Help
---

### Post by DeathOnJuice on 2009-06-20
I'm having a problem with regular expressions. I'm trying to find a file with no letter m in the name. After a bit of research, I tried these:

ls|grep -E 'm{,0}'
ls|grep 'm{,0}'
ls|grep -E 'm{0}'

And similar, but they all either returned everything or nothing. And no, ls|grep '[^m]' will not work, since that only needs one character to not be m. I want every character to not be m.

Can anyone help? I was sort of thinking about the find command as well. Thanks.

---

### Post by geirha on 2009-06-20
Instead of trying not to match an m, match an m, and invert it.
```
ls | grep -v 'm'
```

You could also use the find command
```
find -not -name "*m*"
```

---

### Post by DeathOnJuice on 2009-06-20
> **geirha said:**
> Instead of trying not to match an m, match an m, and invert it.
```
ls | grep -v 'm'
```

You could also use the find command
```
find -not -name "*m*"
```

Thanks, didn't see that option.

---

