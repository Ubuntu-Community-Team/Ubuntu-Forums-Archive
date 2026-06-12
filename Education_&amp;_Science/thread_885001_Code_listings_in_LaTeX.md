---
title: "Code listings in LaTeX"
date: 2008-08-09
forum: Education &amp; Science
---

### Post by KLineD on 2008-08-09
Hello! I'm in the process of finishing my masters thesis, and I'm having trouble with code listings. I'm using the listings package, and \lstlistoflistings to generate the list of source code along with chapter, figures and tables listings. The list generates fine, but I want to be able to configure some things.

For example, the list header at the top of the page reads "Table of Content" (actually it's in spanish) while the list of figures header reads "List of Figures" and the list of tables "List of Tables" so I would like the list of source code to read "List of Code" or something like that. Also in the actual list, the leftmost item is the chapter and section where the listing appears (like VI.2) and I would like to change that to the listing number (1,2,3...n).

Anyone got a clue on this? thanks in advance.

---

### Post by MiKom on 2010-01-19
You may use listings macro from texlive-lates-recommended package. You can later use it as described here:

[Listings]("http://en.wikibooks.org/wiki/LaTeX/Packages/Listings")

---

