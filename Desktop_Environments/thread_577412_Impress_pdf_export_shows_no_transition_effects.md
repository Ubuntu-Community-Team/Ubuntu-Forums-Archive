---
title: "Impress pdf export shows no transition effects"
date: 2007-10-16
forum: Desktop Environments
---

### Post by Fifo70 on 2007-10-16
When I export my impress presentations to pdf I get one pdf page for each slide. That means I get no transitions, such as showing one box at a time, as I had in my presentation. What could that be?

---

### Post by vob on 2007-10-18
Hmmm, as far as I can tell PDF is not designed for such fancy stuff, so I wouldn't even expect these effects to be there. 
IIRC, this also doesn't work when converting slides from M$ PowerPoint to PDF via the Adobe Acrobat Distiller under WinDOS.

---

### Post by cpbl on 2007-11-01
I have the same problem. I was quite suprised to find this deficiency. 
No, Microsoft's s/w seems not to do it right either.
But there is a special box in the Impress PDF Export options which selects to apply transition effects to the PDF document.

Not only can PDF do all kinds of fancy special effects, but they are mostly not needed. Each time a page changes / is updated in a presentation should generate a new page in the PDF file.
I believe PDF can store such things efficiently, but even if it couldn't, one should be able to end up with a PDF which can be clicked through one stage at a time.
 This is the way packages like Beamer (for LaTeX) work to make progressive changes on each slide appear nicely in PDF output.

Does no one have a trick for making this work? Does anyone know what the "transition effects" checkbox is supposed to do?

C, Ubuntu Gutsy, OOo 2.3

---

