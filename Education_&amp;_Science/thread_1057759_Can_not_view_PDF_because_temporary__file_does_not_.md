---
title: "Can not view PDF because temporary  file does not exist (Lyx, Ubuntu)"
date: 2009-02-02
forum: Education &amp; Science
---

### Post by avizcaino on 2009-02-02
I have installed a new layout in LyX but when I tried to create a PDF file to check the document, It was not possible because the temporary file does not exists.
I thank if any of you can assess me ;)

---

### Post by Roberto50 on 2009-11-26
I got the same problem. Using 
lyx -dbg 3
and compiling the document, I discover the trouble: I was using graphics with gif format. The converter gif2png was not configured properly.
I solve my problem using png graphics only.

---

