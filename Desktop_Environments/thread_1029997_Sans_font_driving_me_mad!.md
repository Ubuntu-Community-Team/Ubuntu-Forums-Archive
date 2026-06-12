---
title: "Sans font driving me mad!"
date: 2009-01-04
forum: Desktop Environments
---

### Post by Gizmonty on 2009-01-04
Hello,

I have been slowly going mad over a fonts related issue for the last few weeks. I run intrepid on my desktop and my laptop. On my laptop, I use Sans for most of the fonts (application, document, desktop, window title) and they come out beautifully anti-aliased, as does Monospace for the fixed width font. On my desktop, the same fonts come out pixelly and ugly.
I have all of the rendering options in my appearance preferences set the same so there must be some other setting. I even tried copying the entire fonts directory from my laptop to my desktop without success (thinking I might have different versions of the fonts). Does anyone know where to change this?
Interestingly, OpenOffice 3 refuses to antialias documents on my desktop despite it doing so very nicely on my laptop. I thought that antialiasing in OO was internal. Coincidence?

---

### Post by Gizmonty on 2009-01-04
OK. A bit of fiddling and I've solved this. I had a few files in my /etc/fonts folder that have presumably gotten in there as a result of following some how-to. I deleted them and things are now the way I want them. (Almost, I'd love fonts to be better rendered in general in linux but that seems like a bigger issue).

---

### Post by Ivo Moelans on 2009-01-04
Please mark this thread as "solved".

---

