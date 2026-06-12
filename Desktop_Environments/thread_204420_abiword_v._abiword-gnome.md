---
title: "abiword v. abiword-gnome"
date: 2006-06-27
forum: Desktop Environments
---

### Post by waldorf on 2006-06-27
what is the difference between abiword and abiword-gnome?

why would I choose one over the other?

---

### Post by Gustav on 2006-06-27
Abiword-gnome seems to have bonobono support (at least it depends on some bonobono libs) and abiword does not seem to have these dependencies.

My suggestion would be to use abiword-gnome if you use gnome and abiword otherwise.

---

### Post by waldorf on 2006-06-27
That makes sense.

I noticed that if I try and install it using the "Add/Remove . . ." GUI in the Applications menu that there is no choice - the default is plain old abiword not abiword-gnome. Given that Ubuntu is gnome, that would seem odd.

Yes, no?

---

### Post by Th3Professor on 2008-03-10
What is "bonobono" (other than a manga)?

I see that Ubuntu 7.10 has "abiword", "abiword-gnome", and an additional one not previously mentioned in this thread, "abiword-common". There are some others, though they do not appear to be the main app, mostly plugins.

I'll probably just install good ol' generic "abiword", though am curious about those "-gnome" and "-common" differences. Any ideas?

---

### Post by KingCharles on 2008-03-20
The differences are actually many more than what I thought when I first asked this question myself.

**Abiword** seems suited to be more compatible with diverse desktop environments; that said, it will not allow full direct interaction with GNOME (like drag & drop of files from nautilus). To me, it seems a bit heavier package, although suited to handle more formats. The following is a list of formats that can manipulate, given that you have installed its plug-ins package.

It Opens:
-----------------------------
- AbiWord (.abw)
- Abiword Template (.awt)
- Microsoft Word (.doc. dot)
- Rich Text Format (.rtf)
- Text (.txt, .text)
- Encoded Text (.txt, .text)
- XHTML (.html, .htm, .xhtml)
- GZipped AbiWord (.zabw)
- XSL-FO (.fo)
- HTML [via libxml2] (.html, .htm)
- WordPerfect (.wpd, .wp)
- WML (.wml)
- T602 (.602, .txt)
- StarWriter up to 5.x (.sdw)
- Portable Document Format (.pdf)
- Palm Document (.pdb)
- OpenOffice Writer (.sxw)
- OpenDocument (.odt)
- Microsoft Write (.wri)
- MIF (.mif)
- KWord 1.x (.kwd)
- ISCII Text (.isc, .iscii)
- Handcom Word (.hwp)
- DocBook (.dbk, .xml)
- ClarisWorks / AppleWorks 5 (.cwk)
- BZipped Abiword (.bzabw)
- Applix Word (.aw)

It Saves:
-----------------------------
- AbiWord (.abw)
- Abiword Template (.awt)
- Microsoft Word (.doc)
- HTML/XHTML (.html, .xhtml)
- Multipart HTML (.mht)
- Rich Text Format (.rtf)
- Rich Text Format for old apps (.rtf)
- Text (.txt, .text)
- Encoded Text (.txt, .text)
- GZipped AbiWord (.zabw)
- Portable Document Format (.pdf)
- XSL-FO (.fo)
- WML (.wml)
- Palm Document (.pdb)
- OpenOffice Writer (.sxw)
- OpenDocument (.odt)
- Microsoft Write (.wri)
- MIF (.mif)
- LaTex (.latex)
- KWord 1.x (.kwd)
- ISCII Text (.isc, .iscii)
- Newsgroup Formatted Text (.nws)
- DocBook (.dbk, .xml)
- BZipped2 Abiword (.bzabw)
- Applix Word (.aw)

==================================
On the other hand, **Abiword-GNOME** is designed to be more integrated with GNOME itself, depending on GNOME's libraries for interaction with it: e.g. You can drag & drop files from nautilus. Again, given you have installed its plug-ins package:

It Opens:
-----------------------------
- AbiWord (.abw)
- Abiword Template (.awt)
- Microsoft Word (.doc, .dot)
- Rich Text Format (.rtf)
- Text (.txt, .text)
- Endoded Text (.txt, .text)
- XHTML (.html, .htm, .xhtml)
- GZipped AbiWord (.zabw)

It Saves:
-----------------------------
- AbiWord (.abw)
- Abiword Template (.awt)
- Microsoft Word (.doc)
- HTML/XHTML (.html)
- Rich Text Format (.rtf)
- Rich Text Format for old apps (.rtf)
- Text (.txt, .text)
- Encoded Text (.txt, .text)
- GZipped AbiWord (.zabw)
- Portable Document Format (.pdf)

Personally I do not need all the formats that the former provide, and I really enjoy the capability of drag & dropping since I always have nautilus open and navigate with it. Also please beware that some functionality, like Microsoft drawings embeded in Word documents (.doc) will not work flawlesly with either. If you need that kind of functionality, I would suggest using OpenOffice as it is fully designed to be able to handle all that kind of stuff better; then again is chunkier (A LOT chunkier thanks to its JAVA written interface, kind of like the difference between Firefox and Epiphany).

I guess it comes down to a matter of preference in how old, and how many the formats you are dealing with is. If you need a quick, responsive and lean application that can handle embeding of raster and some vector formats (SVG comes to mind), and save them so the Windows world can see it in MS Office, I would suggest AbiWord-GNOME if you use GNOME as your desktop environment.  :]

---

