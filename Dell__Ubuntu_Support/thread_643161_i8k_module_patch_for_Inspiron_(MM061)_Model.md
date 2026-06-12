---
title: "i8k module patch for Inspiron (MM061) Model"
date: 2007-12-17
forum: Dell  Ubuntu Support
---

### Post by Linicks on 2007-12-17
Hi all,

You will be pleased to know I have had a kernel patch put into Andrew Mortons' -mm tree.  This allows the i8k module to recognise the UK (especially) Inspiron 6400 model, as it is called in the BIOS MM061.

This allows you to load it without the --force option.

[http://marc.info/?l=linux-mm-commits&m=119780439025165&w=2](http://marc.info/?l=linux-mm-commits&m=119780439025165&w=2)

Hopefully it will make mainline kernel, and Ubuntu kernel people will backport it.

Nick

---

