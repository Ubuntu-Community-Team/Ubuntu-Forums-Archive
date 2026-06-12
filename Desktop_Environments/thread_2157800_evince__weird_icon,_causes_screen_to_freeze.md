---
title: "evince:  weird icon, causes screen to freeze"
date: 2013-06-26
forum: Desktop Environments
---

### Post by George Heine on 2013-06-26
Sometimes, when using evince to display a PDF flle, an unknown icon is displayed.  It looks like a page of text, with a hand and a "plus sign" (+) in the upper left corner.
Picture attached.  Activity that seems to cause this is left-clicking the mouse and then dragging.  (Although it doesn't seem to happen consistently.)

[IMG]http://www.mathnmaps.com/evicon.png[/IMG]

When this icon is visible, the computer freezes up for a number of seconds.   If I  happen to notice the icon before releasing the mouse button, I can drag it back into the document area and then release the button.  Otherwise, I need to wait until the program finishes whatever time-consuming operation it is doing and then the icon disappears and normal operation resumes.

Using evince 3.4.0 on Ubuntu 12.04 LTS. PDF files being viewed tend to be 5MB to 20MB in size.  

Questions:

- what is this icon?  what does it mean?
- what is the time-consuming process going on behind the scenes?
- how can I make the icon disappear and stop the freeze ?
- how can I configure evince to disable this feature entirely?
- are there alternative PDF viewers?  (Used to use xpdf but it seems no longer to be maintained.   Evince is not bad, actually, but sometimes it carries a lot of overhead when all the is
needed is a quick look at a PDF file.)

Thanks for any answers.

---

### Post by George Heine on 2013-06-30
Reply on the [evince forum]("http://blog.gmane.org/gmane.comp.gnome.apps.evince.general") identified this as a "Drag N Drop" icon; activated by clicking and dragging mouse.  Purpose seems to be to drop the pdf file  (or the part displayed) onto another application.  However, there doesn't seem to be a way (other than just waiting) to get the icon to go away if it is not your intention to select another application.  

Anyone still listening?  Any ideas?  thank you again for any assistance -

---

