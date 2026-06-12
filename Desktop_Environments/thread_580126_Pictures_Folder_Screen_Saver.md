---
title: "Pictures Folder Screen Saver"
date: 2007-10-18
forum: Desktop Environments
---

### Post by joe007 on 2007-10-18
I have all my pics on a smb share and I would like to either make a link to the share or edit the path it looks at.  Anyone have a clue?

---

### Post by vayde on 2007-10-25
In Gutsy, you need to edit the file /usr/share/applications/screensavers/personal-slideshow.desktop

and change the following line:
Exec=slideshow
to:
Exec=slideshow --location=/full/path/to/pictures

Without the path, mine started showing random pictures from the hard drive... some of them terribly inappropriate *blush*  Good thing I noticed it on the laptop at home, not when it was at the office :)

---

### Post by John_T on 2007-11-17
Thanks **Vayde**, that worked just fine in Feisty too!

For other noobs like me, it's worth noting that the file was hidden, and owned by root, so I had to use the command line to see it, and "su" to edit it.

---

### Post by grimidau on 2008-02-17
can you explain for me how to use the commandline?

---

