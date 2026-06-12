---
title: "Gedit recently used file list"
date: 2009-04-04
forum: General Help
---

### Post by c901906 on 2009-04-04
Hi,

How do I increase the size of the recently used file list in the file menu in gedit? Currently, it just shows the last five (5) files I've edited. I'd like to see 20 or so filenames that have recently been edited. Hardy 8.04. Gnome.

Thanks!
a.

---

### Post by ukblacknight on 2009-04-04
Hi, Welcome to the Forums :)

If you hit Alt+F2 anywhere in Ubuntu, you will see a Run like prompt.

Type: gconf-editor

You'll see a window pop up, with a tree like structure on the left hand side.  Under "/", you'll see apps.  Expand that, then navigate to:

gedit-2 > preferences > ui > recents

In the right hand side, you'll see "max_recents", and it will be defaulted to 5.  Change that to 20 :)

Hope this helps.

---

### Post by c901906 on 2009-04-04
Thank you. That is fantastic. 

):P

a.

---

