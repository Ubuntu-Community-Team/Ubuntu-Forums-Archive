---
title: "How to Restore back Desktop Icons"
date: 2008-12-13
forum: General Help
---

### Post by trendyabinash on 2008-12-13
Sir I have downloaded the UBUNTU tweaks softwares from the site [LINK]www.getdeb.com[/LINK] And used it to remove my desktop icons, and now when I want them back it is not working.

Despite of my clicking on the show desktop Icons button.

What should I do??

---

### Post by Ivo Moelans on 2008-12-13
Try this:

Open *Applications&#8594;System Tools&#8594;Configuration Editor* (or in terminal type: *gconf-editor*).
Go to *apps&#8594;nautilus&#8594;desktop*. In the right pane should be items like *computer_icon_visible* which you can check or uncheck.

Does this work for you?

---

### Post by trendyabinash on 2008-12-13
> **Ivo Moelans said:**
> Try this:

Open *Applications&#8594;System Tools&#8594;Configuration Editor* (or in terminal type: *gconf-editor*).
Go to *apps&#8594;nautilus&#8594;desktop*. In the right pane should be items like *computer_icon_visible* which you can check or uncheck.

Does this work for you?
It is only show computer icon on desktop.

By the way I found out how to restore back the icons.

After checking the show desktop icons in the ubuntu tweaks, just log out and log back in and it will be restored.

THANKS for your support SIR

---

### Post by diedo on 2008-12-14
> **Ivo Moelans said:**
> Try this:

Open *Applications&#8594;System Tools&#8594;Configuration Editor* (or in terminal type: *gconf-editor*).
Go to *apps&#8594;nautilus&#8594;desktop*. In the right pane should be items like *computer_icon_visible* which you can check or uncheck.

Does this work for you?


thanks i faced the same problem and it's work for me with no reason when i installed ubuntu 8.10 there  was no icons on the desktop i wasn't know how to configure nautilus:p

---

