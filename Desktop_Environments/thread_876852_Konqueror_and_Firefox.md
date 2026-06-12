---
title: "Konqueror and Firefox"
date: 2008-08-01
forum: Desktop Environments
---

### Post by eudemus on 2008-08-01
Is it possible to get Konqueror web links to open in Konqueror even when Firefox is the default browser.

Usually, I do all my browsing in FF, and when I click on links in (e.g.) TB or other apps, I want them to open in FF. This is easily achieved by having FF as the default browser for my system.

Occasionally, however, I want to browse in Konqueror rather than FF, and I want links that I click on in Konqueror not to immediately send me back to FF!

Is this possible? Does anyone know?
Cheers, Eudemus

---

### Post by kerry_s on 2008-08-01
sounds like you need to make a choice. the os is not magical it can't change settings when you change your mind. :lolflag:

right click the link and use the open with.

---

### Post by eudemus on 2008-08-01
Thanks, Kerry, for your thoughts.

I'm not asking for magic from the os. In fact, I don't want the os to determine how Konqueror behaves (in this respect) at all. 

I want to be able to configure Konqueror independently of the os defaults that are applied to other apps and other bits of the os.

---

### Post by thestig_992 on 2008-08-01
What the file opens with depends on the file extension, if its different then its possible to change those settings, otherwise it doesnt really make sense...

---

### Post by eudemus on 2008-08-01
Many thanks, thestig_992

> **thestig_992 said:**
> What the file opens with depends on the file extension, if its different then its possible to change those settings, otherwise it doesnt really make sense...

What I'm wishing for surely does "make sense" - there is nothing unintelligible about it.

I'm wanting the way Konqueror handles different file extensions to depend BOTH on the file extension AND on the application in which the link is clicked.

Perhaps there is some reason why it would be unwise for the way file extensions are handled to be configurable differently in different applications. But if so, I'm missing it.

---

### Post by kerry_s on 2008-08-01
> **eudemus said:**
> Thanks, Kerry, for your thoughts.

I'm not asking for magic from the os. In fact, I don't want the os to determine how Konqueror behaves (in this respect) at all. 

I want to be able to configure Konqueror independently of the os defaults that are applied to other apps and other bits of the os.

konqueror is a part of kde, it is the os, it's that pretty gui you see, that pretty desktop with icons on it. it's like ie in windows.

you can change what things are open with, but like all os's you have only 1 choice for a click, but you can put as many programs as you want on the right click open with.

---

### Post by eudemus on 2008-08-01
Ah, ok - I suppose I thought that Konqueror was just an app (albeit one that was designed to integrate well with KDE).

What you've said also explains why my wishing for the OS to operate independently of the OS might not seem to make too much sense! ;-)

Cheers, Eudemus

---

### Post by GeneralZod on 2008-08-01
> **kerry_s said:**
> it is the os, it's that pretty gui you see, that pretty desktop with icons on it. it's like ie in windows.

(None of this is true, BTW)


eudemus: 

If I'm understanding you correctly, the solution to your problem is to open Konqueror -> Settings -> Configure Konqueror -> File Associations and select text/html.

Then click the "Embedding" tab, "Show File in Embedded Viewer" and make sure KHTML is the first in the list.  Clicking on an html link in Konqueror should then open the page in Konqueror, and I *think* will leave non-KDE stuff untouched (i.e. Firefox should still be your "default" browser).

Middle-clicking an html link will probably launch Firefox, but I haven't got Firefox installed so can't check.  Make note of your original settings in case I've made a mistake, here ;)

---

### Post by kerry_s on 2008-08-01
> (None of this is true, BTW)

does konqueror not draw the desktop anymore?
the only part that might be a given is kdm is the window manager and it draws the the windows and kde-panel is separate. but that has nothing to do with what he wants to change.

anyways, my kde is a bit rusty. i'll let you handle it from here. :)

---

### Post by GeneralZod on 2008-08-01
> **kerry_s said:**
> does konqueror not draw the desktop anymore?
the only part that might be a given is kdm is the window manager and it draws the the windows and kde-panel is separate. but that has nothing to do with what he wants to change.

anyways, my kde is a bit rusty. i'll let you handle it from here. :)

Hehe - a "bit rusty" indeed ;)

I'm not sure there ever was a time when Konqueror itself drew the desktop - that has been, for as long as I can remember, the responsibility of kdesktop.  kdesktop and konqueror do share some back-end code, though, but the Konqueror process itself is not required in order for KDE to run.  Are you thinking of GNOME and Nautilus, perhaps? IIRC, by default, the Nautilus process itself (i.e. - not just a shared library) draws the GNOME desktop, although this can of course be changed.

kdm is the login manager, like GNOME's GDM.  kwin is the window manager, and draws the window decorations.  KDE's panels are the responsibility of kicker.  

In KDE4, kdesktop and kicker have been condensed into a single executable called "plasma".

And thus ends today's "How KDE Works 101" lesson :)

---

### Post by kerry_s on 2008-08-01
> **GeneralZod said:**
> Hehe - a "bit rusty" indeed ;)

I'm not sure there ever was a time when Konqueror itself drew the desktop - that has been, for as long as I can remember, the responsibility of kdesktop.  kdesktop and konqueror do share some back-end code, though, but the Konqueror process itself is not required in order for KDE to run.  Are you thinking of GNOME and Nautilus, perhaps? IIRC, by default, the Nautilus process itself (i.e. - not just a shared library) draws the GNOME desktop, although this can of course be changed.

kdm is the login manager, like GNOME's GDM.  kwin is the window manager, and draws the window decorations.  KDE's panels are the responsibility of kicker.  

In KDE4, kdesktop and kicker have been condensed into a single executable called "plasma".

And thus ends today's "How KDE Works 101" lesson :)


and that's why i don't use kde, to many parts that must work perfectly together to do the simple task of drawing a desktop. :lolflag:
(that is a joke, kde is what i started with back in the day when it works it works)

---

### Post by ingomueller.net on 2008-08-17
> **GeneralZod said:**
> If I'm understanding you correctly, the solution to your problem is to open Konqueror -> Settings -> Configure Konqueror -> File Associations and select text/html.

Then click the "Embedding" tab, "Show File in Embedded Viewer" and make sure KHTML is the first in the list.  Clicking on an html link in Konqueror should then open the page in Konqueror, and I *think* will leave non-KDE stuff untouched (i.e. Firefox should still be your "default" browser).

Middle-clicking an html link will probably launch Firefox, but I haven't got Firefox installed so can't check.  Make note of your original settings in case I've made a mistake, here ;)

Works like a charm, thanks many times! Middle-clicking opens a new tab in the background, just as desired :-)

Regards, Ingo

---

