---
title: "Using git to apply a patch..."
date: 2009-04-08
forum: General Help
---

### Post by teddyk on 2009-04-08
Hi,

I've been trying to implement a bug fix into WINE.

The patch I need to apply is from a mailing list archive:

[http://article.gmane.org/gmane.comp.emulators.wine.patches/63187]("http://article.gmane.org/gmane.comp.emulators.wine.patches/63187")

I've tried to copy and paste the code into a file and "git apply" that way however there are numerous errors. 

From what I've found it's probably because of mail formatting, correct?

How would I go about getting the patch out of that message and applying it successfully. I've looked around but most git documentation is heavy material...

Cheers,

Teddy

---

### Post by nunki on 2009-04-08
You need to make sure you are on the correct git branch for wine, and then type ```
git am -3 <name of patch>
``` This will merge it into that branch.

---

