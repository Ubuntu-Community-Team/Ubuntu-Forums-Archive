---
title: "grep or egrep question"
date: 2009-01-27
forum: General Help
---

### Post by hardysummer on 2009-01-27
It is annoying trying to type in "grep -e first -e second -e third" etc.  Is there a shorter way to replace the extra -e's?

I tried egrep which is suppose to be the same as "grep -e" but it did not work very well when I typed in "egrep first second third"

Some *rc files use the | to mean and/or. But I know the | is used for piping in bash. I was wondering if there is another similar character(s) that can be conveniently used.

---

### Post by bgerlich on 2009-01-27
Escape the "|" char (\|) and instead of a pipe you'll get OR :)

---

