---
title: "Konqueror displays current tab's site icon in kicker(taskbar) - how to disable this?"
date: 2006-04-15
forum: Desktop Environments
---

### Post by tensor on 2006-04-15
I've got many programs running at the same time. To identify the needed one I look at at the icons (which is faster than reading program names, btw). I tend to have many tabs open in the konqueror and most of the time the pages have custom icons attached by the web developers. As a result I have to _read_ all the program names in the kicker to find Konqueror or even to deduce which window is actually a konqueror's because it also shows the page title, if it is long, the word "Konqueror" is not displayed. 

Are there any ways to display a generic icon in the taskbar for the Konqueror?

---

### Post by bruno666 on 2008-05-24
You should try to launch Konqueror with something like :

konqueror --miniicon <icon> 

where <icon> is the path for your custom icon.

For further information you could read the man page by typing this in konqueror's address bar :

#konqueror

---

