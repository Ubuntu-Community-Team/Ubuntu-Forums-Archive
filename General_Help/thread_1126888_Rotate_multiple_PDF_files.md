---
title: "Rotate multiple PDF files"
date: 2009-04-15
forum: General Help
---

### Post by afbase on 2009-04-15
How would one go about rotating 180 degrees multiple pdf's in say some folder /home/user/docs/

I know that I can rotate each page 180 degrees of one pdf as such: 
```
pdftk input.pdf cat 1-endS output output.pdf
```

Is there a way in command line to do this for every pdf found in some folder say /home/user/docs/ ?

As it seems, I have many, many pdf files that need to be rotated and it would take way too long to correct one by one.

Thanks.

---

### Post by ostrm on 2009-04-15
Do it with a for-loop (in bash):
```

for i in *.pdf; do pdftk $i cat 1-endS output rot_${i}; done

```

This will rotate all pdf-files (for example input1.pdf, input2.pdf, ...) in the current directory and save them to files with the original filenames prefixed with "rot_" (rot_input1.pdf, rot_input2.pdf, ...)

---

### Post by afbase on 2009-04-16
> **ostrm said:**
> Do it with a for-loop (in bash):
```

for i in *.pdf; do pdftk $i cat 1-endS output rot_${i}; done

```This will rotate all pdf-files (for example input1.pdf, input2.pdf, ...) in the current directory and save them to files with the original filenames prefixed with "rot_" (rot_input1.pdf, rot_input2.pdf, ...)


Thanks:popcorn:

This isn't exactly related to my issue but would anyone know a tutorial on how to do for loops, if statements, etc. in CLI?

---

