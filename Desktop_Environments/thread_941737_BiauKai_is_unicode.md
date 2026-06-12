---
title: "BiauKai is unicode?"
date: 2008-10-08
forum: Desktop Environments
---

### Post by jeffATwork on 2008-10-08
I'm trying to use this font in a PDF I'm generating using Perl and PDFlib 6. BiauKai is an Apple royalty-free dfont. I used fondu to convert it to ttf.

Other Chinese fonts (Uming, Ukai) work. But when I try with BiauKai, I get the error:

PDFlib Error [2230] PDF_create_textflow: Can't show character with Unicode value U+8278

...

etc.

So, anyone have experience with BiauKai indicating it _should_ work after converting with fondu on unicode (utf8)?

Thanks!
-J

---

