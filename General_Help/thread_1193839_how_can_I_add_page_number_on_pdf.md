---
title: "how can I add page number on pdf?"
date: 2009-06-22
forum: General Help
---

### Post by chanyunkwan on 2009-06-22
how can I add page number on pdf?
can pdfeditor do that? how? or using another software to do that?

---

### Post by ugm6hr on 2009-06-22
Editing PDFs is always difficult without Acrobat (full version).

Inkscape is my current favourite, but requires you to manually edit each page of a document.

---

### Post by m2xtreme on 2010-04-21
You can use this method until a simpler solution is found...

[http://forums.debian.net/viewtopic.php?t=30598](http://forums.debian.net/viewtopic.php?t=30598)

Props to the original poster, it saved me a lot of trouble and it's very well documented and straight forward.

:)

Also, you should name your files accordingly:

input book file = newbook.pdf
input numbers file = numbers.pdf

output will be called finbook.pdf

or you can edit the .sh script

---

### Post by TeAmigo on 2011-05-30
You can do it with OpenOffice. It will open the pdf in Draw. Select View/Master. In that view, do Insert/Fields/Page Number. Check that it positions it where you want it, and check the font size. It defaults to a really large font, you'll probably want it smaller. You may find that a given pdf has more than one master. You have to go through the above process with each master. You can export it to pdf again. Might want to give it another name so if something doesn't go right you still have the original.

---

