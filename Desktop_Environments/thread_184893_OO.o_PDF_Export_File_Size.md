---
title: "OO.o PDF Export File Size"
date: 2006-05-30
forum: Desktop Environments
---

### Post by mark on 2006-05-30
I had previously (may even have been in Breezy) exported a 1-page OO.o doc to .pdf and it worked great - no problems reading it with anything that understands PDF (evince, Adobe) and the file size was a modest 6.2KB.  Today, I edited the file (actually removing a small amount of text) and exported to PDF.  Imagine my horror at finding that my 1-page document is now *228.8KB*!

Anybody got any idea of what happened?  Anybody else seeing this?  This is OO.o version 2.0.2-2ubuntu12, latest Dapper updates.

---

### Post by kuja on 2006-05-30
Well, its been a while since I've been able to use OOo, but if I remember right you can optimize it for screen, print, and maybe something else that I can't remember. Which were you using when you exported it? Could that be it?

---

### Post by mark on 2006-05-30
[QUOTE=kuja]Well, its been a while since I've been able to use OOo, but if I remember right you can optimize it for screen, print, and maybe something else that I can't remember. Which were you using when you exported it? Could that be it?[/QUOTE]
I just used the same method as earlier - File>Export to PDF.  I looked in the subsequent dialogue & didn't see anything re: optimization.  I also went through the Tools>Options settings & didn't see anything pertinent.

I guess I'm baffled that it worked so well & efficiently earlier and now it turns what was 6KB into 208KB.

Maybe I'll d/l the Win version & try it in my XP partition to see if there's any significant difference...

---

### Post by linuxbz on 2006-05-30
6KB is extremely small for a PDF.  The only way it can be that small is if it is ONLY using internal fonts.  If you are using any other font(s) they will have to be included in the .pdf.  Maybe that?

---

### Post by mark on 2006-05-30
Nope.  The document was originally created in MS Word, imported into OO.o and then saved in .odt format.  I do not have *msttcorefonts* installed, so it used the OO.o equivalent fonts.  Then I exported it to PDF, yielding the 6.8KB file size.

Since my last post, I did d/l and install the Win version of OO.o 2.02, loaded the .odt document and exported to PDF.  This yielded a file size of 58.9KB.

I guess my next step is to log onto the OO.o forum and see if anybody there can shed some light on this.  If I get anything useful, I'll post the information here.

---

### Post by paulpoe on 2006-11-19
I've got this same problem. My single page document is being exported to a pdf of 228 kb. I need it to be under 150kb. Anybody know how to fix this?

---

### Post by avryhof on 2006-12-19
Lower the resolution to 144dpi...

---

### Post by abovett on 2007-01-20
I'm having the same problem. I have some systems with Dapper on them (OOo 2.0.2) and some with Edgy (OOo 2.0.4). PDFs created under Edgy are a lot bigger than those created from the same documents under Dapper.

I'm not aware of anywhere that PDF quality/size can be tweaked in OOo, but if anyone does know please say. Otherwise I'll have to switch to a Dapper machine every time I want to do PDF conversions, which is rather inconvenient.

Andy B

UPDATE:

I just had a look on Launchpad and found that _[bug #23573]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/23573")_ appears to be relevant. Looks like it's to do with font embedding. Also - my earlier comment about dapper vs edgy is not true for all documents - it probably depends on what fonts they use is my guess. Under some circumstances Dapper also produces big (200kB +) PDFs from small documents.

---

### Post by Hagar Delest on 2007-01-21
You're right, the problem comes from fonts embedding. You can compare the old files : menu Files>Properties in any PDF viewer, it will tell if fonts are embedded or substituted.

I know that PDFCreator under XP can substitute all the fonts, file is therefore very small. Embedding is mandatory to insure a really exact input. But OOo should be abble to subsitute fonts when users request it.

---

