---
title: "Evince renders Japanese PDFs in Chinese"
date: 2008-10-24
forum: Desktop Environments
---

### Post by clubsoda on 2008-10-24
Solution: Install the package **poppler-data**.

Strangely, evince-gtk was rendering japanese PDFs in what looked like chinese characters.  Running evince from the command line, the following error message appeared:= ```
Error: Unknown character collection 'Adobe-Japan1'
```How could that be?  For xpdf I had already installed cmap-adobe-japan1 and cmap-adobe-japan2!  It turns out that poppler requires additional code pages or links to access these.

What would be the correct way to fix this?  Should poppler-data be added to the *Suggests:* list of dependencies in poppler-utils, libpoppler2 or the cmap-* packages?  Searching Synaptic for "japan" doesn't bring up poppler-data, currently you have to search for "CJK"...

---

### Post by Mazin on 2008-10-24
I recommend Adobe's acroread over evince anyways. It's the gold standard for PDFs, and it has better printing options, features, etc.

My 2c.

---

