---
title: "Latex font size"
date: 2009-06-04
forum: General Help
---

### Post by Hutom on 2009-06-04
Hi guys, I am having a problem here. I am using latex to write an article. I use kile as editor. But it does not allow me any fontsize other than 10pt, 11pt and 12pt. If in the preamble I write, say ```
\documentclass[a4paper,14pt]{article}
```it takes the default font size of 10pt. Any idea what is going wrong?

P.S. However, it allows me to increase the size of any selected text by those commands like, \huge, \large etc.

---

### Post by Stefan_K on 2009-06-05
Hi Hutom,

you could use the [extsizes package]("http://ctan.org/pkg/extsizes"). I prefer using scrartcl:
```
\documentclass[fontsize=14pt]{scrartcl}
```

Stefan


--
[TeXblog.net]("http://texblog.net")

---

### Post by Hutom on 2009-07-23
Sorry for such a very late reply. But thank you very much.

---

