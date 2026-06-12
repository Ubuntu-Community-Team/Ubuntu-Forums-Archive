---
title: "Page numbering in LaTeX."
date: 2009-10-10
forum: Education &amp; Science
---

### Post by lemonicetea on 2009-10-10
Hi all,

I am currently writing my PhD thesis. My uni says the thesis must be numbered from the title page to the end of the document. My thesis has following layout.

1. title page (manual format)
2. abstract
3. list of figures
4. list of tables
5. table of contents
6. text

I found that the page numbers of both abstract and contents will be automatically set to 1. Could someone tell me how can I force the page number start from the literally first page to the end? Thank you.

---

### Post by XCan on 2009-10-11
You can force latex to set the page number on a page by using ```
 \setcounter{page}{2} 
``` Replace 2 with whatever page number you want it to be of course.

---

### Post by spinoza666 on 2009-10-11
Hey XCan,

that was what I was thinking as well. Do you know if there's a way of getting \setcounter to work with \maketitle as well? I mean using setcounter to number the titlepage produced by maketitle.

I'm just asking out of interest, so no biggy if you don't know:P

---

### Post by samden on 2009-10-11
You can try putting the \setcounter command directly before \maketitle. However if for some strange reason your title page is not the first page in the document that may set the number of the page before the title page instead. If so, use:
```
 \pagebreak
\setcounter{2}
\maketitle 
```
Which will make a new page, set its page number, and start the title on that page.

---

### Post by spinoza666 on 2009-10-14
Doesn't work for me, but no worries. Thanx for the reply:P

---

### Post by samden on 2009-10-14
The style file may not print page numbers on the title page by default, even if the counter has assigned it a certain page number.

---

