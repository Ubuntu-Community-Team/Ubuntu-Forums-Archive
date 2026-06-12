---
title: "gnome-menu: No Icons for some Categories.. how to fix?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by andiii on 2006-08-20
I lost Icons on "Games", "Internet" "office" etc.

Only on Games and Education I still have Icons. I tried in Alacarte to manually pick an Icon, but it stays as the default folder thing. 

Rebooting and chaging themes didn't change a think. The problem occured after moving folders around in Alacarte. But also "Revert"  to get back the defaults did not help.

Is there a config file where I can look at?


I'm using Ubuntu Dapper 6.06.1 :)

---

### Post by H.E. Pennypacker on 2006-08-20
All you probably need to do is replace the icons folder.  I am not sure how you damaged the icons folder, because you'd need administrative permissions before working with it.

The following should be the directory you should replace (ask someone to send you a copy of the folder, and replace it with what you have now):

/usr/share/icons/hicolor/32x32/apps/

---

### Post by andiii on 2006-08-21
No, Icons were fine.

I just solved the prob, a bug in Alacarte. When I just changed the Icon the change was not recognized, so I had to change the description of the Category.

And now the Icons are back, strange..

---

