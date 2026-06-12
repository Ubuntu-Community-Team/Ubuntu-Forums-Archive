---
title: "md5 file comparison"
date: 2009-02-03
forum: General Help
---

### Post by IMSargon on 2009-02-03
I have two different (very long) md5 files I wish to compare. However, the normal diff tools won't work for me because the files are not in the same order in the two lists. I need to know what lines exist in one file but not the other, and I need to know what lines differ. What tool/script/command do I need?

---

### Post by jespdj on 2009-02-03
Try sorting the two files with the 'sort' command, and use 'diff' to compare them.

---

### Post by IMSargon on 2009-02-03
> **jespdj said:**
> Try sorting the two files with the 'sort' command, and use 'diff' to compare them.

I had considered this, but then what would happen if a line were missing in one of the files? The shift in the lines would skew the rest of the diff.

---

### Post by jespdj on 2009-02-03
I think diff is smart enough to match up the following matching lines again. Why don't you just try it?

---

### Post by IMSargon on 2009-02-03
> **jespdj said:**
> I think diff is smart enough to match up the following matching lines again. Why don't you just try it?

Okay. (Wow, that sort command is fast)

$sort First.md5 > First-sorted.md5
$sort Second.md5 > Second-sorted.md5
$diff --suppress-common-lines First-sorted.md5 Second-sorted.md5

Yeah, that seemed to do the trick. Thanks!

---

