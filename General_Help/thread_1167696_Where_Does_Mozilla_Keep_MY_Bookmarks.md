---
title: "Where Does Mozilla Keep MY Bookmarks"
date: 2009-05-23
forum: General Help
---

### Post by Mark76 on 2009-05-23
I can find its default bookmarks file easily enough. But I have no idea where the one with the bookmarks I've set up is.

---

### Post by lukjad on 2009-05-23
Open Firefox and go to ***Bookmarks-Organize Bookmarks->Import and Backup->Export HTML***. Then choose which folder you want it exported to (I usually choose the Desktop so that I see it right away and can move it, but some people prefer the home folder). Click Save and a file called *bookmarks.html* should appear on you desktop (or wherever). All your bookmarks will be placed in there on a nice webpage for you to access and read. If you wish to use this as a backup, and restore it someday, go to ***Bookmarks-Organize Bookmarks->Import and Backup->Import HTML*** and make your way to this file. Then click open, and all your bookmarks from the day you saved it should be there.

---

### Post by DeMus on 2009-05-23
> **Mark76 said:**
> I can find its default bookmarks file easily enough. But I have no idea where the one with the bookmarks I've set up is.

They are in a file of the sqlite type. I can't figure out which one exactly. I think it is places.sqlite but I'm not sure.
What you can do is export your bookmarks from within Firefox. Click boormarks, organize bookmarks and choose import/export. Ten you will get your "normal" bookmarks.html file.
Hope I could be of any help.

---

### Post by Tibuda on 2009-05-23
~/.mozilla/firefox/randomname.default/

---

### Post by lukjad on 2009-05-23
> **danielrmt said:**
> ~/.mozilla/firefox/randomname.default/
True, but if you try looking there, you will only see what looks like gibberish. You need to export them into a readable format first.

---

### Post by glotz on 2009-05-23
[QUOTE=lukjad007]True, but if you try looking there, you will only see what looks like gibberish. You need to export them into a readable format first.[/QUOTE]That's the answer to the question.

---

