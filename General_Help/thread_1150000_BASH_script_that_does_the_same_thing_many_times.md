---
title: "BASH script that does the same thing many times?"
date: 2009-05-05
forum: General Help
---

### Post by lethalfang on 2009-05-05
I have very limited knowledge in BASH, does anyone know how to write a script that tells my computer to perform the same operating many times?

Specifically, I need to use an application called eps2pdf, such that if I type in the terminal:

> eps2pdf filename.eps 

It will create a PDF file, "filename.pdf" in the same directory. 

Now, eps2pdf takes only one input file, so eps2pdf *.eps does not work. 

Now, I have like 50 such .eps files. What can I do to automate this process?

Thanks in advance! :-k

---

### Post by lloyd_b on 2009-05-05
```
for FILE in *.eps; do
    eps2pdf $FILE
done
```will loop through all .eps files in the current directory, running "eps2pdf" for each of them.

Lloyd B.

---

### Post by lethalfang on 2009-05-05
> **lloyd_b said:**
> ```
for FILE in *.eps; do
    eps2pdf $FILE
done
```will loop through all .eps files in the current directory, running "eps2pdf" for each of them.

Lloyd B.


Thanks!

---

### Post by stchman on 2009-05-05
> **lethalfang said:**
> I have very limited knowledge in BASH, does anyone know how to write a script that tells my computer to perform the same operating many times?

Specifically, I need to use an application called eps2pdf, such that if I type in the terminal:



It will create a PDF file, "filename.pdf" in the same directory. 

Now, eps2pdf takes only one input file, so eps2pdf *.eps does not work. 

Now, I have like 50 such .eps files. What can I do to automate this process?

Thanks in advance! :-k

I think I understand what you want.  Since the program eps2pdf does not accept wildcards *.eps will not work.  Easy, use the find command with -exec switch.

Do this in your favorite editor.  Save it as whatever filename you want.  It is customary to give scripts a .sh extension.  Remember to make the script executable.

```

#!/bin/bash
find . -name '*.eps' -exec eps2pdf {} \;

```

What this will do is search for all files that have the extension .eps, then execute your eps2pdf program with the argument.  Spacing is important in this command.  Remember the find command is recursive.

---

