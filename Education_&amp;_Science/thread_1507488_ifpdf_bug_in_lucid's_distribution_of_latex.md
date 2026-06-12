---
title: "ifpdf bug in lucid's distribution of latex"
date: 2010-06-11
forum: Education &amp; Science
---

### Post by quackeroni_pizza on 2010-06-11
After an upgrade to Lucid the bundled latex distribution is acting weird.

The style ifpdf.sty conflicts with the \ifpdf variable. This breaks \includgraphics autocompletion. I now have to supply an extension to keep it happy...

All this worked just fine prior to the upgrade...

---

