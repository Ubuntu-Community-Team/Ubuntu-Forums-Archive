---
title: "Mouse releases not processed until mouse moves???"
date: 2006-07-13
forum: Desktop Environments
---

### Post by christian.convey on 2006-07-13
I'm using a version of Dapper that's fully patched as of today (13 July 2006).  Either today or yesterday, I started seeing behavior where sometimes a mouse-click wouldn't register until I moved the mouse.

For instance, when I click on a button, the button looks depressed as it should.  But when I release the mouse button, the button continues to look depressed and the action normally triggered by a button click doesn't occur.  It's only when I next move the mouse that the button returns to its non-depressed appearance and its functionality executes.

I'm doing som Gtk programming with Python as well, and I started seeing this in my own program.  What I'm specifically seeing is that sometimes the gdk.BUTTON_RELEASE event doesn't get deliveted to  my application until the mouse is moved.  I don't know if this is an X, or a gdk, problem.

Has anyone else seen this?

Thanks,
Christian

---

### Post by lode303 on 2008-06-26
I've been experiencing exactly the same thing for the last few months on Xubuntu with fluxbox. It's definitely not app specific.


Wondering if anyone else has seen this and/or been able to fix it.

---

