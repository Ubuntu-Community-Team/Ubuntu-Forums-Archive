---
title: "Correctly viewing PDF files in fullscreen"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Athropos on 2006-06-06
Hi,

I'm using LaTeX and the beamer class to creates slides for my talks. Well, the important thing is that I get PDF files that I must display in fullscreen.

I've been unable to find a viewer which correctly display these files in fullscreen mode :
 - Evince greatly renders text, but not figures. These figures are in .eps format. If I open one directly in Evince, they looks good. However, EPS files included in a PDF file are terrible, there is no antialiasing...
 - Acroread correctly renders everything (text and figures), but there are some flaws : for example, some lines are 'broken'. Moreover, the fullscreen mode does not overlap the gnome-panel. I've tried to hide the latter, but there is still a small part visible: this is not good for talks...
 - GGV has the best rendering, but does not have a real fullscreen mode. There is still some white borders around the slides, and there is no way to tell it to color them in black...

I've also tried xpdf, kpdf, gpdf... None of them is correctly able to do the job. I must boot on Windows just to use acrobat reader (which correctly renders everything, not as the Linux version).

Does someone know how I could correctly display my slides in fulscreen using Ubuntu?

---

### Post by harfooz on 2006-06-08
I also write presentations in beamer and noticed the same issue with gnome's panels and acroread's fullscreen mode. Here's a workaround that I did:

System > Preferences > Keyboard Shortcuts

Scroll down to Window Management and then find Toggle Fullscreen Mode. 

Then select a function key that you're not otherwise using.

Hope this helps!
Clint

---

### Post by Athropos on 2006-06-08
Hi,

Thanks for this tips, it works pretty well!

---

