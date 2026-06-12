---
title: "firefox problem"
date: 2007-01-28
forum: Desktop Environments
---

### Post by chris103549 on 2007-01-28
Hi. I have used ubuntu only since dapper but recently upgraded to edge. Since the upgrade, my firefox seems to be rendering html form elements differently. 

Specifically, "submit" buttons and input forms don't seem to look right. The buttons are white and the input boxes don't have a bottom border. I have attached a screenshot of google.com.

If anyone could point me in the right direction, I should would appreciate it!

---

### Post by Blutack on 2007-01-28
What's wrong with it?  Looks like mine...

---

### Post by yabbadabbadont on 2007-01-28
Dapper uses the 1.5.0.9 version of Firefox while Edgy uses the 2.0 series.  That is probably why it looks different than it did.

---

### Post by chris103549 on 2007-01-28
Okay I see. Other web browsers show submit buttons and input fields much nicer. I run firefox 2.0 on windows and it looks different than on linux, so I'm wondering if there is a setting somewhere within firefox for this?

Thanks!

---

### Post by chris103549 on 2007-01-28
Here is what Konqueror looks like at the same page... Maybe I am being anal here but the buttons look way better and the input box has an outline.

Any ideas how to make firefox look better?

---

### Post by chris103549 on 2007-01-28
oops. here's the screenshot.

---

### Post by yabbadabbadont on 2007-01-29
They look different because Konqeror is using the QT widgets to draw the buttons while Firefox is a GTK application and uses it to draw them.  (while windows has it's own widgets)  Change your gtk2 theme to something that doesn't use the ClearLooks gtk engine and you should see that they will change again.

---

### Post by chris103549 on 2007-01-29
awesome. Thanks. That's just the info I needed!

---

### Post by chris103549 on 2007-01-29
Would you mind pointing me at one of these themes?

---

