---
title: "Replacing Adobe Reader Embedded In Firefox With Evince"
date: 2008-04-30
forum: Desktop Environments
---

### Post by rykel on 2008-04-30
Hi,

I prefer Evince to Adobe Reader anytime. I have in fact totally removed Adobe Reader from my system.

However, I get a "PATH" error (see screenshot) every now and then when I click on a PDF file link in Firefox 3.

As the title says, I wonder if you know how to replace the "embedded" Adobe Reader in Firefox 3 on Hardy Heron with Evince - or at least remove the reference to Adobe Reader in Firefox?

Without an "embedded" Evince or removal of any references to Adobe Reader, we would need to actually install Adobe Reader just to read the PDF files on the net sometimes.

Thanks for helping!

---

### Post by cdude on 2008-04-30
Try this.

In firefox addressbar, type:

about:config

and hit enter.

then search for this key:

extensions.pdfdownload.openPDF

change its value from "defaultViewer" to evince (or probably to the full pathname of evince)


OR, (maybe easier)

Install [PDF Download]("https://addons.mozilla.org/en-US/firefox/addon/636") extension for firefox, and change the deafault viewer from its settings.

---

