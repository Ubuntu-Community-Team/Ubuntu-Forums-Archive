---
title: "Remmina blank screen on ssh session Ubuntu 17.10"
date: 2017-10-25
forum: Desktop Environments
---

### Post by snpz on 2017-10-25
Hello!

Found one more bug - tried to make an ssh session to external host using Remmina. Had to fill in passwd as usual, but than Remmina screen gets black and thats it.
Googled some records from april of 2016. debian and arch linux forums with same symptoms. Than it was an Terminal emulator widget for GTK+ 3.0 (VTE3) issue.
```
Oct 25 15:59:40 snpz-Latitude remmina[10716]: GtkDialog mapped without a transient parent. This is discouraged.
Oct 25 15:59:43 snpz-Latitude remmina[10716]: Allocating size to GtkScrollbar 0x556ec3a81070 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
```
At the moment i have to say that 17.10 is a pretty buggy OS, that is pretty hard to use for daily tasks! :(

Bug report here - [https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1727332](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1727332)

---

### Post by snpz on 2017-10-25
Workaround - just upgrade Remmina from PPA
[https://github.com/FreeRDP/Remmina#from-ppa](https://github.com/FreeRDP/Remmina#from-ppa)

---

