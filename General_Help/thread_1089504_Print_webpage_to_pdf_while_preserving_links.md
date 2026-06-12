---
title: "Print webpage to pdf while preserving links"
date: 2009-03-07
forum: General Help
---

### Post by taecha on 2009-03-07
Does anyone know how to print/convert webpages to pdf while preserving the document's '*internal*' links?

**cups-pdf** will print nicely but ditch all links.

**htmldoc** preserves all links but as '*external*' http-links only. That is, links referring to other sections of the document will still link to the original http-page rather than to the relevant section **within** the pdf document.

Since I have been googling this issue for weeks now I'll be thankful for any suggestions.

---

### Post by Ken Wood on 2011-09-15
Bump

---

### Post by Ken Wood on 2011-09-15
Nevermind resolved.

```
htmldoc -t pdf14 input_name.html > output_name.pdf
``` :guitar:

---

