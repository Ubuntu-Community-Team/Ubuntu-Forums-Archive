---
title: "Help : editing in LyX"
date: 2009-01-21
forum: Education &amp; Science
---

### Post by Lovok on 2009-01-21
Simple question :
While in LyX, one can view the LaTeX source code being used. How can I edit this code?

This is my situation : I wrote a document in French, but when I export it to .pdf, the date is in English (even if LyX is set to French).
I see \documentclass[english]{article} in the source, and I want to change that [english] to [french], but I can't seem to find out how. Can this be done?

Thank in advance.

---

### Post by tommers on 2009-01-21
I would like to know about this as well.

In the past, I have deleted sections that were not imported into LyX correctly and inserted a TeX box into the document with the correct LaTeX - but it would be much easier to just edit the LaTeX code directly.  

I remember looking through the LyX wiki, but not finding much help.  It might be worth checking there... just in case.

---

### Post by IanH on 2009-01-21
Have you checked the language tab in the document settings? I suspect settings there would control that line.

As for editing the tex code, I don't think it's possible short of exporting to tex and editing that file. You can insert tex code in the document (Insert->TeXCode), but that won't overwrite the generated code.

---

### Post by Lovok on 2009-01-22
> **IanH said:**
> Have you checked the language tab in the document settings? I suspect settings there would control that line.

That did exactly what I needed, thank you good sir.

---

### Post by eljalill on 2009-01-22
Is there  specific reason why you need to edit it in LyX?
You could just open the source file in gedit or another editor, and change that bit there. Or does LyX change it back then?

---

### Post by Lovok on 2009-01-22
I just checked, and the changes I made to the language in gedit were carried over to LyX. 
If I need to play with the source, I will do it this way from now on, thanks.

---

### Post by FelixAkk on 2012-02-11
Over here it didn't if I made changed outside LyX. I've really been looking for a true WYSIWYG editor, but while I was glad to hear of LyX, it seems they went way to far with it and ended up in the ugly zone where MS Word is: no control over your document using the source whatsoever. This is exactly what LaTeX sort of aimed to fix. You want the best of both worlds! No just one of them!

At the moment Bakoma seems the only developed application that does this. The functionality seems quite amazingly well implemented, but the interface has a lot of room for improvement, and the pricetag for no updates and no API is quite high for a student imo.

---

### Post by overdrank on 2012-02-11
Please start a new thread. Back to sleep thread, thread closed.

---

