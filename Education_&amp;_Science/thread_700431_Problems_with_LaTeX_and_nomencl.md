---
title: "Problems with LaTeX and nomencl"
date: 2008-02-18
forum: Education &amp; Science
---

### Post by amar on 2008-02-18
I am trying to write my report and I have followed the instructions on the nomencl.pdf however when I compile no .nls file is produced and the nomenclature does not appear in my report.

the warning "No file project.nls" is output

The .nlo file is produced without any problem and has a list of all my terms.

I have managed to find a couple of other references to this error but no replies or solutions.

Anyone else heard of or have a possible solution?

Thanks

---

### Post by amar on 2008-04-02
Apparently \makenomenclature doesn't actualy work, I needed to type:
```
makeindex project.nlo -s nomencl.ist -o project.nls
```

manualy in the command line.

Baaa

---

### Post by khaeru on 2008-04-09
FYI: [https://bugs.launchpad.net/ubuntu/+source/rubber/+bug/214910](https://bugs.launchpad.net/ubuntu/+source/rubber/+bug/214910)

I also notified the author of rubber.

---

### Post by amar on 2008-04-29
Just to update:
It is working fine in hardy

---

### Post by UeB on 2008-06-26
I am using Kile on hardy and have exactly this problem. To acually use the package nomenclature I have to type

makeindex project.nlo -s nomencl.ist -o project.nls

in the shell every time I add something with the \nomenclature command in my .tex file.

Does anyone have same problem or even better a solution?

---

### Post by louisgag on 2008-09-22
Using Kile on hardy I also experience the same problem.

I solved it (only for the LatexPDF command) by editing the build options of the LatexPDF command (settings menu):

added ```
; makeindex %S.nlo -s nomencl.ist -o %S.nls
``` at the end of the options list of the command. Make sure you include the ; which instructs the terminal that a new command is issued.

:popcorn:

---

