---
title: "Desktop icons have disappeared"
date: 2021-02-20
forum: Desktop Environments
---

### Post by peyre on 2021-02-20
I had some trouble with my video card.  With a lot of switching out and trial and error I got my two screens to work extended again, using an older video card.  However, somewhere in the middle of all that I somehow made my Desktop icons disappear.  They still show in ~/Desktop (there are 53 items there), but nothing shows on either screen when I have everything closed or minimized.  I've tried renaming /home/leon/.config/xfce4 and rebooting - it does reset some of my customizations, but still nothing shows on the Desktop.  Anyone have any ideas?

---

### Post by peyre on 2021-02-21
I resolved the issue with the video card by upgrading from 20.04 to 20.10, so it must have been a software problem.  I still don't have my icons though.  I'd really like to get them back, if anyone has any suggestions.

---

### Post by peyre on 2021-02-22
Ok, I got them restored!  All I had to do was enter xfdesktop in the terminal.  Didn't even have to put in my password for sudo (it is, after all, a user setting).  The Desktop items suddenly reappeared all at once and I'm good to go.

---

