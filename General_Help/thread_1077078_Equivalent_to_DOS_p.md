---
title: "Equivalent to DOS /p?"
date: 2009-02-22
forum: General Help
---

### Post by faitswulff on 2009-02-22
I don't have terribly extensive knowledge with either bash or DOS, but one thing I do miss from DOS is the ability to scroll through results by pages.  For instance:

```
dir /p
```

in DOS will show me all the files or directories by page instead of just vomiting them all at me at once.  Is there some sort of universal option in bash to do the same thing?

---

### Post by mb_webguy on 2009-02-22
Use "*command* | more".  That's a bar (or pipe), btw, which you get with Shift+backslash.  You could also use "less" or "most" instead of "more".

EDIT:  FYI, "more" isn't more than "less", or less than "most".  They're just different commands that do similar jobs, and are accordingly (and humorously) named similarly.  I like "more" most, and "less" least, but it's really down to personal preference.

---

### Post by faitswulff on 2009-02-22
Thank you!  Wow, that was quick.

Much love,
faitswulff

---

