---
title: "Help with apache2"
date: 2008-12-23
forum: General Help
---

### Post by jkvan87 on 2008-12-23
I downloaded a template from online and it came with an image folder, index.html, style.css   when I open up index.html in fileviewer, the images show up however, when I go to localhost in firefox, it only shows the text and not the images. Is there a option I need to change in apache?

---

### Post by fragos on 2008-12-23
Look at the html file with gedit and see where it expects the images to be located. When I develop sites I use all relative URL addressing, to the index.html file, so that I can move the site folders between hosts and the addressing still works. Perhaps this wasn't done.

If your unfamiliar with html search for "<img" and see what "scr=" says.

---

