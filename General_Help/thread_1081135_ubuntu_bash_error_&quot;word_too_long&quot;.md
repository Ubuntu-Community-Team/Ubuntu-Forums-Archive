---
title: "ubuntu bash error &quot;word too long&quot;"
date: 2009-02-26
forum: General Help
---

### Post by seeyouagain on 2009-02-26
I got the error message "word too long" in make Make file. 
A line "src = ...." have 4000 characters and caused the problem. I searched the internet for this error, but no good suggestion about this issue. 
The shell is bash. It looks like it only takes the 3000 characters in one line.

The same script works well on scali-cluster. But ubuntu (8.10) gives the error.

Any solutions for this problem?

---

### Post by barnex on 2009-02-26
I've had the same issue with too many arguments. As far as I can tell, the only solution would be to recompile bash or you kernel to reserve more space, but I would not recommend this. Perhaps you can workaround the issue by splitting your command into smaller pieces or so.

---

