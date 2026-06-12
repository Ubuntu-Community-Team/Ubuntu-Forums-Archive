---
title: "how do i remove firefox 3 bookmark drop down icon"
date: 2008-06-26
forum: Desktop Environments
---

### Post by gilbert_george on 2008-06-26
On my ubuntu laptop FF3 has a drop down icon (a little downward pointing black triangle) the the right of each folder in my bookmarks toolbar, this makes each folder wider than they used to be (with FF2) and so they now overflow.

These drop down icons are not present on FF2 or on FF3 on Windows so I guess it's something to do with FF3 using the gtk theme.

Anyone know how to remove them?

just to be clear it's the drop down triangles I am trying to remove from the right of each folder in the bookmarks toolbar not the folder icon to the left.

Ta

g-g

---

### Post by gilbert_george on 2008-06-27
Fixed this by using a different FF3 theme.

XP on Vista did nicely :-)

---

### Post by dda on 2008-07-07
I solved it by adding the following to userChrome.css:

/* Dropmarker for folder bookmarks */
.bookmark-item[container] > .toolbarbutton-menu-dropmarker {
  display: none !important;
  }

---

### Post by sayakb on 2008-07-07
Please mark the thread as solved.

---

