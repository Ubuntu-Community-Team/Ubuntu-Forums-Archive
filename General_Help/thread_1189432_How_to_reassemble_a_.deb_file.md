---
title: "How to reassemble a .deb file?"
date: 2009-06-16
forum: General Help
---

### Post by Nyken on 2009-06-16
Simply enough, I took apart a .deb file with the right-click Archieve Manager and experiemented with a few files inside. Now I want to put all this back together again. How do you do it? :)

---

### Post by lamego on 2009-06-16
You are not expected to modify .deb files contents directly, .debs are built from source packages using building rules, you change the source/build rules, not the resulting binary .deb file.

If you really want to, you can do it from the terminal using "ar", since a .deb is an ar archive.

---

### Post by Nyken on 2009-06-23
Hmmm... thought it wouldn't be so simple. :( Back to the drawing board :D

---

