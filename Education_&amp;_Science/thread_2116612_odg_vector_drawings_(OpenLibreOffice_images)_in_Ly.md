---
title: "odg vector drawings (Open/LibreOffice images) in Lyx"
date: 2013-02-16
forum: Education &amp; Science
---

### Post by ugm6hr on 2013-02-16
I started this thread, but realised I had found a solution before posting. I posted anyway for others reference and comments.
First:
```
sudo apt-get install unoconv
```
Then , to insert an odg into Lyx, insert as Graphic in Lyx.
```
In Preferences -> File Handling -> File Formats
Enter a new vector graphics format: OpenOffice Draw / odg
Default display as PDFLATEX.
```
```
In File Handling -> Converters
Add new OpenOffice Draw -> PDF (create a separate entry for every PDF option - not just PDFLATEX)
Converter: unoconv -f pdf $$i
```
It should then work.

---

