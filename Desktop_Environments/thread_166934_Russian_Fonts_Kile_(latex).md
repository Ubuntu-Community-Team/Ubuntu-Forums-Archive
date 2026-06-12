---
title: "Russian Fonts Kile (latex)"
date: 2006-04-27
forum: Desktop Environments
---

### Post by zappa86 on 2006-04-27
Hi I installed kile via synaptic and I would like to make some russian tex files. I also added the gnome keyboard switcher to a panel so I can switch between russian and english. I have tested this out in gedit by writing some english and then going into russian mode and it works fine. In kile when I made a little file with about half english and half russian (switching between the language with the gnome keyboard language selector as I did before), however when I make the pdflatex file the russian (cryillic) characters dont appear, only the english (latin) ones do. I have seen a few tutorials online but none of them are clear and none of them work. I have tried adding a few things in the preamble like the tutorial said but latex could not find the packages.

---

### Post by Spie on 2006-04-28
What did you write in your preamble?
Something like this:
```
\usepackage[T2A,OT1]{fontenc}
\usepackage[ot2enc]{inputenc}
\usepackage[russian,english]{babel}
```

It works for me. Maybe you need to install the tetex-extra packages?

---

