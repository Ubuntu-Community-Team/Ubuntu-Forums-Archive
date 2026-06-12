---
title: "Fonts in firefox - huge!"
date: 2005-07-27
forum: Desktop Environments
---

### Post by neylitalo on 2005-07-27
In gnome, Firefox worked just fine. Now, when I'm using KDE, Firefox's fonts are HUGE. They are too big to work with. The text (hyperlinks and text on a page, etc.) is fine, but the fonts on the menubars, etc. are huge. I've posted a screenshot [here](http://s128792503.onlinehome.us/screenshot.png) Be warned - it's a huge image.

Any and all help appreciated - I miss Firefox  :-|

**EDIT:** Thunderbird looks like that too; a Mozilla issue?

---

### Post by f1dave on 2005-07-28
Tried in firefox- edit -> preferences -> fonts and colours?

That might help...

---

### Post by tdjokic on 2005-07-28
This was my big problem for years, now I know 2 answers:

1. edit -> preferences -> fonts and colours -> Display resolution - make some experiment here and fonts will change

2. File manager Super user mode -> home -> [your_user_name](view / show hidden files) -> .gtkrc-2.0 - this file is responsible for menu fonts size, open it and adjust fonts

(3. There is even third solution, but I forget it - if you install something about fonts, you will get something in Control center, that works with .gtkrc-2.0 with GUI)

---

### Post by neylitalo on 2005-07-28
Thank you so much, tdjokic, it was in Edit > Preferences... etc. I appreciate it a lot. Thank you again.

Neal

---

### Post by tdjokic on 2005-07-29
You are wellcome! Any way, I recomend to your attention .gtkrc-2.0. It is easier to adjust and, what is more important, it works all over the system, not only in FF - as far as I know.

---

