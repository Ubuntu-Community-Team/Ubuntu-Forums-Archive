---
title: "grep-trouble solved (partially)"
date: 2006-07-08
forum: Desktop Environments
---

### Post by jimw on 2006-07-08
I was looking through things and found that I had had success with grepping in a file that I'd done all the input myself, in gedit.

So I took a copy of the Kazakh constitution, oened the html version in OpenOffice, cut it and pasted to gedit and tried it.

No joy.  Got a blank file.

So I took html2text, had it go over the Kazakh constitution and output it as an rtf file, then did my grep through that.  

It worked, with the exception of not recognizing certain Cyrillic Upper-case letters.

Since those ones are mostly fairly guessable (Capital R in Republic, captital P in President, and one or two like that) the situation is liveable.

If someone more knowledgeable than I could tell me what the problem is that I'm dealing with, and what to do about it, I'd be grateful.

JimW

---

### Post by aysiu on 2006-07-08
It sounds as if it's simply a character encoding issue.

---

