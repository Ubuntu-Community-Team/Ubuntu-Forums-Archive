---
title: "latex + dvipdf + evince = not getting underscore into clipboard"
date: 2014-02-23
forum: Education &amp; Science
---

### Post by magowiz82 on 2014-02-23
Hi,
I'm writing a latex document, in this document , I need sometime to use "_" (underscore character), printing it with latex is quite simple, I only have to remember I have to add the "backslash" escape character before the underscore.
My pdf generation procedure is : latex hb.tex -> dvipdf hb.dvi , if I open the file with evince or acroread, the underscore is shown correctly, but if for example I try to copy and paste a word that contains the underscore into a terminal or somewhere else I get the word with a blankspace instead of the underscore .

What do you suggest ?

PS : I wrote my topic in this section because latex is often used for educational purposes

---

### Post by magowiz82 on 2014-02-23
I found a solution here : [https://bugzilla.redhat.com/show_bug.cgi?id=153724#c4](https://bugzilla.redhat.com/show_bug.cgi?id=153724#c4) , I preferred the one in last part of comment :
> Try using the Latin Modern font with T1 encoding; that font is an updated design of CM with more characters and built-in, rather than constructed, accented characters. To use the Latin Modern font with T1 encoding add the lines
```

\usepackage{lmodern}
\usepackage[T1]{fontenc}
\usepackage{textcomp}

```
to your preamble.

In this way I get underscore selected and can be copied to clipboard without any issues, also the other solution (using \tt ) was fine, I hope it helps.

---

