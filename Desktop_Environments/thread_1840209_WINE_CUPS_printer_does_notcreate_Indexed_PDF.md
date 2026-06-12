---
title: "WINE CUPS printer does notcreate Indexed PDF"
date: 2011-09-07
forum: Desktop Environments
---

### Post by Rob__oo00T on 2011-09-07
All

I have find an issue printing on CUPS queue, from a WINE application (notepad or others are the same)
The results of printing, is a PDF file that is not "searchable", I mean, you cannot use find function of PDF reader for looking for words. (easy to recreate a problem with notepad)
While, if you print from Ubuntu application, Gedit for example, the PDF generated if fully indexed.

I have see this problem with different ubuntu installation, and different ubuntu or wine version, (I use Natty 11.04 64bits).

any idea for a solution?
Rob

---

### Post by Rob__oo00T on 2011-09-17
> **Rob__oo00T said:**
> All

I have find an issue printing on CUPS queue, from a WINE application (notepad or others are the same)
The results of printing, is a PDF file that is not "searchable", I mean, you cannot use find function of PDF reader for looking for words. (easy to recreate a problem with notepad)
While, if you print from Ubuntu application, Gedit for example, the PDF generated if fully indexed.

I have see this problem with different ubuntu installation, and different ubuntu or wine version, (I use Natty 11.04 64bits).

any idea for a solution?
Rob

Long-known bug: [http://bugs.winehq.org/show_bug.cgi?id=6416](http://bugs.winehq.org/show_bug.cgi?id=6416) 
--- from wine forum!

:(:(

---

