---
title: "Find and Replace missing glyphs with Sed"
date: 2009-01-13
forum: General Help
---

### Post by justin75 on 2009-01-13
I've got a script that processes text files with grep. sed etc, but problems arise when the text contains a 'missing glyph' represented by a white-on-black-diamond question mark.

Note: I'm not sure if other missing characters are also represented by the question mark, but in all the files i've seen (dozens) the problem character is always an apostrophe.

With Kate i can easily search and replace these question-mark-diamonds with apostrophes, but how do i do it with sed?

tia

---

### Post by dagnabit dang doohickey on 2009-01-13
This will replace left and right single smart quotes with single quotes:
```
sed "y/&#8216;&#8217;/''/" *input-file*
```
This will replace left and right double smart quotes with double quotes:
```
sed 'y/&#8220;&#8221;/""/' *input-file*
```


If you need to type the smart quotes, try holding down **Ctrl+Shift** while typing the following 4-digit codes:
**2018** -> left single smart quote
**2019** -> right single smart quote
**201C** -> left double smart quote
**201D** -> right double smart quote

---

