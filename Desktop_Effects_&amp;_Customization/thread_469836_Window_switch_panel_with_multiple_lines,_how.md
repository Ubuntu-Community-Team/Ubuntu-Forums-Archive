---
title: "Window switch panel with multiple lines, how?"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by kam1kaz3 on 2007-06-10
Hi,

Is it possible to make my window switch panel have 2+ rows?
I find myself with a bunch of windows opened at the same time, and a single row to list all the windows isn't good enough for me :(
Oh, and since I'm at it, is it also possible to limit the horizontal size of each window button (in the window switch panel)?

Thank you very much in advance :)

---

### Post by thelinuxguy on 2007-06-10
Right Click on panel >> New panel
Lets put it on top if it isnt already.
Right click on new panel >> properties >> size >> say 60
Right click on new panel >> Add to panel >> Window List
Right click on handle of window list in new panel >> preferences >> size 
[INDENT]minimum size >> say 200
maximum size >> say 300
[/INDENT]

That should do it. I got something as shown at the top in the screenshot.

---

### Post by kam1kaz3 on 2007-06-10
Thanks for answering, but that's not what I meant.

Here's a screenshot of this being done on Windows:
[IMG]http://kam1kaz3.net/ubuntu_windows.png[/IMG]

And the way you're limiting the horizontal size, it limits the size for the whole sub-panel, I want to limit the size of each window button in the panel.

Thank you for trying to help anyways, much appreciated :)

---

### Post by scarpent on 2007-09-09
I'd like to have multiple rows as in Windows Explorer also.  Does anyone know if this is possible?

I see where I can right-click on an empty part of the panel and increase the height from 24 to 48 pixels, which helps with giving more room to my desktop switcher, but the window list items just double in size.  I opened up about 20 terminal windows to see if they'd eventually form two rows, but no luck.

---

### Post by scarpent on 2007-09-09
Ah!  Making the panel 50 pixels tall gives me two rows.  Very nice.

This page at gnome.org gave me the hint that it could be done:

[http://library.gnome.org/users/window-list/stable/windowlist-introduction.html.en](http://library.gnome.org/users/window-list/stable/windowlist-introduction.html.en)

"The number of rows that Window List uses to display the buttons depends on the size of the panel in which the applet resides."

Just knowing that something is possible helps a lot.

This solves it for me since I'm not also looking to limit the width of each window button like kam1kaz3.

---

