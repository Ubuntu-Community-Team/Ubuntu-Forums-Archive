---
title: "Change MIME type"
date: 2008-03-29
forum: Desktop Environments
---

### Post by HuckleSmothered on 2008-03-29
**PROBLEM:**
I need to change the MIME type of a specific file that is incorrectly labeled.

**SPECIFIC:**
Change a .rm file that is currently incorrectly recognized as a MIME type *text/plain* to MIME type *RealMedia*

**BACKGROUND:**
I have recently downloaded a .rm file, a *RealMedia* Document MIME type.
It is a link to a streaming video, if that matters, I'm not sure.
But when I save it to my computer, it changes to a *text/plain* MIME type.

**ATTEMPTED FIXES:**
Using the 'Open with' option and selecting RealPlayer allows me to open the .rm file with a double-click properly.
HOWEVER, it also changes all text files to open with RealPlayer, not a good solution.
Using the 'Open with' option on a text file then changes .rm back to opening with a text editor.

I've installed assoGiate 0.2.1 and discovered that .rm files are already associated with some RealPlayer types.
Nothing under the 'text' MIME types reference the .rm or any other RealPlayer extension.
I poked through the /usr/share/mime and /usr/share/mime-info and /etc/mime.types and, while not knowing exactly what I'm looking for, I did not see anything obviously saying the RealMedia Document equals text/plain.
[B]
Any suggestions?[/B]

---

### Post by HuckleSmothered on 2008-04-03
I've recently come across this document:
[MIME Types System Administration]("http://library.gnome.org/admin/system-admin-guide/2.22/mimetypes-0.html.en")
It seems like it discusses how to do this with an Overrides.XML document in one of the MIME folders, such as /usr/share/mime.

However, it loses me about half way through.
Can anybody help out with a laymen's explanation?

---

