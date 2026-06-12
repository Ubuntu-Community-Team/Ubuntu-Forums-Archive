---
title: "Mendeley export PDF with annotations fails to produce anything"
date: 2009-10-11
forum: Education &amp; Science
---

### Post by cpbl on 2009-10-11
I've installed Mendeley Desktop on 64bit Ubuntu 9.04 and cannot get some basic features working. Most immediately, when I make some annotations on a PDF file and choose to export PDF with annotations, I am allowed to choose the output file name, accept the choice, and then nothing happens. No error notice and no exported file created.

Has anyone else got this behaviour? Anyone else having more luck?

(for earlier discussion of Mendeley Desktop, you could see thread: [http://ubuntuforums.org/showthread.php?t=1067681]("http://ubuntuforums.org/showthread.php?t=1067681") )

---

### Post by PGScooter on 2009-10-12
yes, I am having the same problem. I know that this worked before, because it was a crucial feature for me. If you post a bug report (to mendeley or ubuntu?), let me know.

---

### Post by mustaqil.ali on 2009-10-12
Sorry about this, I've managed to confirm that this is indeed a problem, and it appears isolated to our Debian and Ubuntu packages. I've filed a bug for this on our internal bug tracker and we'll look into fixing it as soon as possible.

You can try heading to [http://www.mendeley.com/download-mendeley-desktop/](http://www.mendeley.com/download-mendeley-desktop/) and using the "generic" linux package as this seems to work fine for exporting with annotations.

---

### Post by PGScooter on 2009-10-13
thanks for looking into this!

---

### Post by PGScooter on 2009-10-21
the newest update (9.4.1) fixed it for me. Note that mendeley does not say 9.4.1 in the about, but rather 9.4. To know that you have 9.4.1, do apt-cache policy mendeleydesktop

---

### Post by frabjous on 2009-12-15
I've tried this with the generic 9.5.1 on Ubuntu Karmic, and although a PDF is produced when I export with annotations, the annotations do not show up in acroread. Are they supposed to?

---

### Post by fgfuigi on 2009-12-15
I am allowed to choose the output file name, accept the choice, and then nothing happens. No error notice and no exported file created.

---

### Post by PGScooter on 2009-12-15
have you upgraded to the current version fgfuigi?
What version are you using?

---

### Post by benjamin2008 on 2010-06-09
Same problem with pdf export: nothing happens after choosing file name. 

> **PGScooter said:**
> have you upgraded to the current version fgfuigi?
What version are you using?

What is fgfuigi? 
I have mendeley in the newest version (using repository) and googling fgfuigi only turns up results connected with mendeley.

---

### Post by PGScooter on 2010-06-09
> **benjamin2008 said:**
> Same problem with pdf export: nothing happens after choosing file name. 



What is fgfuigi? 
I have mendeley in the newest version (using repository) and googling fgfuigi only turns up results connected with mendeley.

Benjamin, I should have used the Quote tags. fgfuigi is the name of an ubuntuforums user who posted right before my last post. I was asking him.

Sorry for not using the QUOTE tags.

---

