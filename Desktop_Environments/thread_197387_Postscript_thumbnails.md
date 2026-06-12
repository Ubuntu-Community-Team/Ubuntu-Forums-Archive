---
title: "Postscript thumbnails"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-06-15
Is it my problem or evince creates thumbnails for everything but ps files? It seems that thumbnailing for dvi, pdf and djvu is set in gconf under
desktop/gnome/thumbnailers
with the command
evince-thumbnailer -s %s %u %o
I'd try to add a similar entry for application@postscript but I can't find a way to add entries (and I'm not sure this would be a safe way to go)
Any ideas?

---

