---
title: "question about pypanel and &quot;un&quot;iconifying windows"
date: 2008-02-13
forum: Desktop Environments
---

### Post by bsunde on 2008-02-13
I've recently been using pypanel..and think it's great for the most part.  One thing about it seems quite different than other panels I've used though--when I click on the iconified window in the panel it opens it and puts it on the desktop, but it does not automatically raise the window as well.  In other words I have to click twice to get the window at a place where I can type in it. Any way to modify .pypanelrc so that I only have to click once?  Thanks!

---

### Post by bsunde on 2008-02-14
Ah hah...well I happened to have figured this out after randomly trying some things.  Apparently the key is to have pp.taskFocus(task) listed twice in the following part of .pypanelrc:

#-------------------------------------
def taskButtonEvent(pp, button, task):
#-------------------------------------
    """ Button event handler for the panel's tasks """

    if button == 1:
        pp.taskFocus(task)
        pp.taskFocus(task)
    elif button == 2:
        # Destroy the application
        task.obj.destroy()

---

### Post by Anzan on 2008-02-14
Thanks, bsunde. Good to know.

---

