---
title: "how to convert pdf to text?"
date: 2009-02-09
forum: General Help
---

### Post by danbuter on 2009-02-09
The pdf I need to convert to text is set up in columns, so just cutting and pasting leaves everything pretty screwed up. Is there a way to do this and preserve the format or have it come out in the right order? Thanks!

---

### Post by kaibob on 2009-02-09
The command-line utility, pdftotext, will do what you want. This utility's -layout option is described as:

> Maintain (as best as possible) the original physical layout of the text.  The default  is  to  ´undo&#8217;  physical  layout (columns, hyphenation, etc.) and output the text in reading order.

---

### Post by danbuter on 2009-02-09
That did it! Thanks a ton! Didn't even know about that utility.

---

### Post by HermanAB on 2009-02-09
Try this trick:
$ ls /usr/bin/*pdf*

Cheers,

Herman

---

