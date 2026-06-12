---
title: "Tool to resize active window?"
date: 2008-12-10
forum: General Help
---

### Post by dustigroove on 2008-12-10
I am looking for a utility that will allow me to specify preset window sizes (for example, 800x600, 1024x768, 1280x1024, etc, etc,.. ) and then click on the active window to resize it to the selected size.

A number years back I had a simple Windows program that did this very well. In the taskbar there was an icon that when clicked would allow you to select your preset size, once the size was selected the cursor would change and you would then click on the window you desired to be resized. Presto, elegantly simple and effective.

I would assume this could be done with a script using xwininfo or xprop + wmctrl, but unfortunately I'm not the man for the task.

Does anyone have any suggestions? Thanks in advance!

---

### Post by dustigroove on 2008-12-10
Anyone? Bueller?

---

### Post by zhocchao on 2008-12-11
hi
You can use something like this

wmctrl -r :SELECT: -e  "0,-1,-1,800,600"

or

wmctrl -r :ACTIVE: -e  "0,-1,-1,800,600"

g

z

---

### Post by dustigroove on 2008-12-11
> **zhocchao said:**
> hi
You can use something like this
wmctrl -r :SELECT: -e  "0,-1,-1,800,600"


Completely missed that when I read the man page... thank you!

---

