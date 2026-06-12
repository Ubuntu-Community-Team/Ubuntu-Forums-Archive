---
title: "Pdftex - create PDF with both portrait and landscape pages?"
date: 2009-01-20
forum: Education &amp; Science
---

### Post by Ng Oon-Ee on 2009-01-20
Hi all,

Am writing my conversion report (Masters to PhD) using LaTeX (pdftex, really). So far so good, but I have some pages which are landscape-oriented (large tables and figures).

Normally this would not be a problem, they just print out like any other pages, of course. However, this report will be distributed to my examiners in soft-copy PDF. I don't think it would be professional to have my examiners tilting their heads 90 degrees to view my large tables and figures (the large table is 6 pages long).

So, is there anyway to instruct pdftex to generate the landscape pages as landscape? That means, as I scroll down the document, I'd have something looking like this:-

```

    ------
    | pg |
    | 1  |
    |    |
    ------
---------------
|             |
|    pg 2     |
|             |
|             |
---------------
    ------
    | pg |
    |  3 |
    |    |
    ------
---------------

```

Any ideas? Or do I create the pdf first and then use some other software to rotate the pages in question?

---

### Post by galileon on 2009-01-21
[http://texblog.wordpress.com/2007/11/10/landscape-in-latex/](http://texblog.wordpress.com/2007/11/10/landscape-in-latex/)

---

### Post by Ng Oon-Ee on 2009-01-21
> **galileon said:**
> [http://texblog.wordpress.com/2007/11/10/landscape-in-latex/](http://texblog.wordpress.com/2007/11/10/landscape-in-latex/)
Thank you, sir! If I may ask, how did you come across that information? My normal googling only turned up \usepackage{lscape} advise, and I hadn't heard of pdflscape before this (obviously).

Edit: Ah, where's the 'thanks' button gone?

---

### Post by Ng Oon-Ee on 2009-01-21
Ah, okay, didn't realize that solving the recent downtimes required disabling the 'mark thread solved' and 'thanks' feature.

Anyway, since I can't click it, I can say it again. Thank you galileon, you were most helpful.

---

### Post by galileon on 2009-01-21
haha, no worries mate, I never cared about the thanks button anyway, lol. I googled "latex landscape  page" and middle clicked the first three links, and looked or one that was written in plain English :D

---

### Post by Ng Oon-Ee on 2009-01-22
Ah, I feel stupid. Thanks for your time and help. I'm pretty sure I googled 'latex landscape' and never came across pdflscape....

---

