---
title: "Disable auto saving?"
date: 2016-06-13
forum: Forum Feedback &amp; Help
---

### Post by &amp;KyT$0P# on 2016-06-13
I've noticed that posts here, as well as editing my signature, gets automatically saved as I'm typing.  Is it possible to auto-save blank content (effectively delete auto-saved content) and disable this feature, such as by using a custom user script or "replacing" the yahooapis script with a local modified version?  If so, any advice what in the board's JS to start looking at (or how to figure that out)?

(Found [http://ubuntuforums.org/showthread.php?t=2271790](http://ubuntuforums.org/showthread.php?t=2271790) in a search, but while it explains the auto-save feature (and lack of any real interface to it), it doesn't get into this level of working with it on the client side.)

Thanks

---

### Post by bapoumba on 2016-06-13
Not sure you can disable auto-save at the user level..

---

### Post by &amp;KyT$0P# on 2016-06-13
Actually, I'm noticing these requests
```
POST http://ubuntuforums.org/ajax.php?do=autosave
```
which leads me to looking at vbulletin_textedit.js, from there I can see how to access the editor from JS:
```
vB_Editor.vB_Editor_001
```

I think disabling auto-save on the client side can be done with this JS command:
```
vB_Editor.vB_Editor_001.autosave_enabled = 0
```
So far it seems to be working... [-o<

What I'm still not finding, is how to delete pre-existing auto-save content.  Do you know if that's being done server side or with JS on the client side?
(I mean, I *can* hack something together to just send it a blank space or the like, but it would be preferable to bypass it completely.)


EDIT Hmm, "vB_Editor_001" isn't static editor name...

---

### Post by &amp;KyT$0P# on 2016-06-16
> **halogen2 said:**
> Actually, I'm noticing these requests
```
POST http://ubuntuforums.org/ajax.php?do=autosave
```
Wow #-o It's can be much easier than writing a user script.  Simply blocking this URL disables autosaving and doesn't interfere with the other functionality on the board AFAICT.
And can restore content auto-saved by the board regardless.
8-)

I don't think I've got any "leftover" auto-saved content, so marking this thread solved.

---

