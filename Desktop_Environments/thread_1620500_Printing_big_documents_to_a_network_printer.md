---
title: "Printing big documents to a network printer"
date: 2010-11-13
forum: Desktop Environments
---

### Post by narcisgarcia on 2010-11-13
I've already tested on 2 different computers with different networks and different printers (but both laser and network printers):
If the document to print has many pages or many data (such as images), it's not sent to printer and remains forever in a "hold" state in the printing spool. This happens with jobs bigger than 2MiB approximately.

The only solution I found to print this kind of documents has been to save in PDF format and print from a console:
```
lp mydocument.pdf
```

With this, the same document that occupied 2MiB in spool can have now the size of 200KiB and and is printed very fast. Printing the same document with Evince has the same effect than printing with OpenOffice (bad).

All this tested also with different Ubuntu versions (9.04, 9.10, 10.04)

Does somebody know which is the problem, and how to solve it?

---

