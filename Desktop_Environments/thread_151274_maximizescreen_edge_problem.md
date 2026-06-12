---
title: "maximize/screen edge problem"
date: 2006-03-27
forum: Desktop Environments
---

### Post by mccarthy on 2006-03-27
My computer thinks that my screen edge is about 4 pixles to the left of where it actually is.  I'm using the lateset fluxbox release, and have used it before without this problem.  This is probably the most frustrating problem ever, because it is such a small thing but it just gets to me (like when the professor is erasing the board and misses a little mark)  Any help would be greatly appreciated.

---

### Post by mccarthy on 2006-03-30
Please?

---

### Post by mccarthy on 2006-04-01
Ok I'll answer my own question so people in the future have an easy answer.  It was the slit.  I had to go to my ~/.fluxbox/init file and change session.screen0.slit.maxOver: from false to true, and then reload Fluxbox, and there you have it.  So if a small portion of your screen is not being maximized over in fluxbox, it is most likely this variable is the issue.

---

