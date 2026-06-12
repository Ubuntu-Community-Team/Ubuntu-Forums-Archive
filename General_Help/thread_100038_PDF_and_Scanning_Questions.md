---
title: "PDF and Scanning Questions"
date: 2005-12-06
forum: General Help
---

### Post by kairu0 on 2005-12-06
I have a lot of paper documents that I would like to scan and put back-to-back in a single pdf document. How can I do this?

---

### Post by aysiu on 2005-12-06
I think most scanning programs will let you do this. I've never used a scanner with Ubuntu, but the scanning program that came with our HP scanner asks after each page whether you want to complete that document or scan more pages before saving it as a PDF.

---

### Post by kairu0 on 2005-12-14
I managed to do this using XSane and ImageMagick's convert command.

First, I changed the XScan mode to only save the scanned files (this is handy because it autoincrements the filenames), and I scanned all of my documents as 0001.png 0002.png, etc.

Then, I used:

```

convert -density 200 -quality 90 -resize "1200x1200>" 0001.png 0002.png 0003.png newdocument.pdf

```

---

