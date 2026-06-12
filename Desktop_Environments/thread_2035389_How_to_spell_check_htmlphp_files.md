---
title: "How to spell check html/php files ?"
date: 2012-07-30
forum: Desktop Environments
---

### Post by dargaud on 2012-07-30
Hello all,
I usually use Kate to edit html files, but the spell checking cannot be changed from one language to the next (I write in 3 languages). Either there's a function in kate I'm missing or I'm looking for a better software to spell check my files.

The current method I use is to copy the page from the browser and paste it in kate, then copy it again and paste it in OpenOffice (this way I only get the text, not the images, Iframes, etc). But I loose the image ALT tags.

I'd rather spell check the source directly. Any suggestions ?

---

### Post by Lars Noodén on 2012-07-30
You could use [HTML Tidy](http://tidy.sourceforge.net/) to check your XHTML.  It's in the repository.  Or if you need to parse the output of your scripts as they appear online, then you could use the W3C's [HTML Validator](http://validator.w3.org/).

Or you could use something like Bluefish.

---

### Post by dargaud on 2012-07-30
THank you, but I didn't ask about validation but about spell checking. English, croat, bengali, etc...

---

