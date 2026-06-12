---
title: "unable to paste using middle mouse button"
date: 2014-06-06
forum: Forum Feedback &amp; Help
---

### Post by joee2 on 2014-06-06
Most X apps will let me paste text using the middle mouse button.  Whenever I middle-mouse into a forum post here, it just inserts a space.

The only way I have found to paste text from emacs is to paste it into gedit first, then ctrl-c ctrl-v it into my forum post.  Is there a better way?

---

### Post by sudodus on 2014-06-06
I have noticed that it does not work well with chromium-browser, while it works well with firefox.

In chromium-browser you can still mark text in a terminal window and select the pull-down menu Edit -- Copy, and then Paste into the edit box of the forum post. So you need no detour via gedit.

---

### Post by ajgreeny on 2014-06-06
I have autoscroll set in Firefox and a middle click does not paste on the first attempt but just shows the autoscroll cursor; however, a second middle click immediately after the first pastes the highlighted text exactly as expected.

---

### Post by joee2 on 2014-06-07
I'm using google-chrome. The Edit : Paste function in google-chrome doesn't seem to pull from the X-windows mouse selection buffer either; it seems to pull only from the clipboard.  My urxvt terminal (at least as I have it configured) has no pulldown menus for copying text to the clipboard.  Also, my emacs configuration doesn't seem to copy text to the clipboard -- only to the X selection buffer.

Another possibly-related problem is that this ckeditor text editing area hijacks a bunch of other handy events like ctrl-L and ctrl-U.  Not to be too old-fashioned, but a simple <textarea> would work a lot better for me, per the principle of least surprise.

---

### Post by cariboo on 2014-06-07
Right-click always works for copy/paste in Chromium. The standard keyboard shortcuts also work.

---

### Post by joee2 on 2014-06-07
> **cariboo907 said:**
> Right-click always works for copy/paste in Chromium. The standard keyboard shortcuts also work.

There are two mechanisms for transferring strings between X Windows applications.  You can read about them here:

[http://www.jwz.org/doc/x-cut-and-paste.html](http://www.jwz.org/doc/x-cut-and-paste.html)

The "primary selection" technique is handy because some apps, like the urxvt terminal I use, don't have a "copy" menu item to send the selection to the clipboard.  It also saves a couple keystrokes, FWIW.

Nearly all X applications that manipulate text (and certainly the 3 popular web browsers google-chrome, chromium, and firefox) let you insert the primary selection using the middle mouse button.  Most web sites (stackoverflow and gmail, for example) accept such middle-mouse-button insertions fine.  But it seems that the ckeditor widget used by this forum is doing something that interferes with this system.

---

### Post by bapoumba on 2014-06-09
TBH, I cannot reproduce either. Would you be using any extension that would interfere ?

---

