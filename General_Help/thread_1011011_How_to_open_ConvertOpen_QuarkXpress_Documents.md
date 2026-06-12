---
title: "How to open Convert/Open QuarkXpress Documents?"
date: 2008-12-14
forum: General Help
---

### Post by ToshibaLaptoplinux on 2008-12-14
I have some very old documents that I created years ago that I need to access/open. Unfortunately they were created in QuarkXpress. Is there any program available that will either open, convert, or extract data from them? I've already tried Open Office to no avail and the documentation for Scribus indicates it can not open Quark docs.

The output of "file -bi *filename*" is "application/x-quark-xpress-3".

Fortunately these are not layouts with images in them but straight text files. I wrote them over 10 years so no longer have access to Quark even on a PC. 

Help,Help.

---

### Post by editrix on 2008-12-18
I have the same problem with old PageMaker files. I can extract text (and a heck of a lot of code) using the "cat" command. It's not perfect, but at least I can see what text is in those files.

Get onto the directory where the Quark files are and then

```
cat filename.extension
```

It may work.

---

