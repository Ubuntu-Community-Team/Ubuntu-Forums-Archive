---
title: "evince does not save window size"
date: 2016-07-18
forum: Desktop Environments
---

### Post by Skaperen on 2016-07-18
in _14.04 LTS_ *evince* would remember the last window size of a document so that opening the same document got the same window size, same window position, and same text magnification.  now in _16.04 LTS_ it does not and always opens each document in a default size which is is very unusable.  this works ok in *okular*.  should i switch to *okular*?

---

### Post by sudodus on 2016-07-19
The general rule is to use the linux tool, that works best for you.

If there is a problem with your favourite tool, please check if there is a bug report about it, and create a bug report if necessary. If you create a thread about it here, others can find the bug report and create 'heat' to increase the chances that it will be fixed.

-o-

***evince*** is a gnome tool, and the current policy of gnome is to make tools simpler. It may be by intention (not by mistake alias a bug), that the window size is not preserved from the previous time you used it. But anyway, a bug report is the way to communicate with the developers.

---

### Post by mc4man on 2016-07-21
It works fine here in 16.04, all .pdf's re-open to last size/zoom. It's actually quite difficult to get a pdf to open at the default size once it's been opened & re-sized.
There doesn't seem to be 1 file that accounts for this, a bit of a mystery. 

I have the rename _both_ .config & .local to .bak to get evince to forget previously opened .pdf size/zoom, ect.
But then renaming _either_ back to normal restores the previous size/zoom. (- go figure that...
So seems to be some interaction between gsettings/dconf & maybe recently-used.xbel?

---

