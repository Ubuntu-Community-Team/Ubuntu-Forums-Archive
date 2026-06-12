---
title: "Change printer margins in Adobe?"
date: 2008-05-12
forum: Desktop Environments
---

### Post by shane2peru on 2008-05-12
Ok, I have a bunch of books in PDF and print them.  I like Adobe PDF Reader for the booklet printing aspect, so please don't tell me to use evince, or kpdf or xpdf, unless you can give me very specific instructions to print a booklet print setup like Adobe has.  I have Adobe 8.1.2 installed from their web site.  When I print, I select booklet format, then print the front first and then back.  I need to make the margin in the center bigger, so that when I bind the book there is enough paper to bind with.  If anyone has any ideas how to do this, I would appreciate the help.  I found this info on the web:  [http://livedocs.adobe.com/en_US/InDesign/5.0/help.html?content=WSa285fff53dea4f8617383751001ea8cb3f-7049.html](http://livedocs.adobe.com/en_US/InDesign/5.0/help.html?content=WSa285fff53dea4f8617383751001ea8cb3f-7049.html)  However it seems this is only for Windows Adobe reader or something, because I don't have these options.  Any help would be appreciated.

Shane

PS.  I'm not opposed to using evince, kpdf etc, however historically I haven't been able to easily set it up to print the booklet style that I need.  :)  If there is an easy setup that you know of please post it, and I will look at it.  Thanks!

---

### Post by shane2peru on 2008-05-22
Ok, seems as no one has an answer for this, or at least no one that has read this.  I'm bumping this back to the top, hopefully someone with some info will chime in here.  I also have recently installed the KDE desktop, and have KPDF at my disposal as well, it seems a little more of an advanced program then Evince.  If someone knows how to do such things in KPDF I would welcome any help on this!  Thanks.

Shane

---

### Post by pedrogl on 2008-05-24
If you are comfortable with command line interface, there are a bunch of tools you can try, however the process is a little bit tedious.

First convert your document to ps (postscript) format, you can do this with acrobat.
Then use psbook to rearrange page order for suitable booklet printing.
Then you can use pstops and/or psdim to print them 2up.

psbook and pstops are in package psutils
you can downlod psdim from [http://www.mscs.dal.ca/~selinger/lpr-wrapper/]("http://www.mscs.dal.ca/~selinger/lpr-wrapper/")

---

### Post by shane2peru on 2008-05-24
> **pedrogl said:**
> If you are comfortable with command line interface, there are a bunch of tools you can try, however the process is a little bit tedious.

First convert your document to ps (postscript) format, you can do this with acrobat.
Then use psbook to rearrange page order for suitable booklet printing.
Then you can use pstops and/or psdim to print them 2up.

psbook and pstops are in package psutils
you can downlod psdim from [http://www.mscs.dal.ca/~selinger/lpr-wrapper/]("http://www.mscs.dal.ca/~selinger/lpr-wrapper/")

That is a thought, I would have to check into that, just with design and layout, I'm really more of a visual person.  I love cli, and use it for a lot of things, however, design and doc layout isn't one of them. lol.  I did find a graphical ps editor, page-cruncher, however, it is not of the greatest quality.  Maybe I can find a good ps editor, or manipulator with a visual layout.  Thanks for the tip though, perhaps we are heading in the right direction.

Shane

---

