---
title: "[SOLVED] Lyx referencing not showing in PDF view"
date: 2008-05-27
forum: Education &amp; Science
---

### Post by Vuddha on 2008-05-27
Hi all,

I've been using Lyx and Jabref for nearly two years with no problems (since Ubuntu 6.04). I've written dozens of documents. Currently I'm using Ubuntu 8.04.

The problem: I can attach the Bibliography as usual, and I set up the document as usual. I can see the bib file in Lyx, and I can insert references as usual. However, when I go to view PDF (or PS or DVI) none of the references show up, and instead are replaced by "[?]". Also, there is no bibliography in the PDF view.

This has only occurred since installing 8.04.

I've tried searching online and the forums and have found nothing. Please help, I've got a big essay due soon!

---

### Post by kleeman on 2008-05-27
Usually when this has happened to me in the past it is due to a conflict in styles between the document and the bibliography. Try changing either and see if it works. The document style is in 

Document----> Settings

while you can get at the bibliography style by right clicking on the final bibliography box at the end of the document.

---

### Post by Vuddha on 2008-05-27
Thanks, for the reply. I've already looked at this potential factor. I can see no reason why the references shouldn't be showing. This is very strange.

---

### Post by kleeman on 2008-05-28
If you look in the /tmp directory with the lyx session open there is a directory like

lyx_tmpdir2211928CScj (yours will differ with the numbers)

within this is a further subdirectory

lyx_tmpbuf0

this contains all the output files from a compile (i.e. a run of latex).
One will have a log suffix. If you look in there you may be able to see the reason for the error.

---

### Post by Vuddha on 2008-05-28
Thank Kleeman. I did that, and looked at the log, and one line says 
"LaTeX Warning: There were undefined references."

How do I remedy this?

Thanks.

---

### Post by kleeman on 2008-05-30
That's not very informative. Try exporting to a latex file 

File----> Export -----> Latex (plain)

(a *.tex file will be produced)

then run 

latex yourfile
bibtex yourfile
latex yourfile
latex yourfile

(yourfile stands for the the first part of the tex file i.e. yourfile.tex) 

Check the error messages as you execute these for clues. This sequence will produce a dvi file which you can view with xdvi

---

### Post by Vuddha on 2008-05-30
Hi Kleeman

Thanks for your help. The problem turned out to be missing bst files with the new install of Ubuntu (a change in texlive?).

I usually used the bibliography styles included with the Lyx installation (texlive?), and tried multiple bst files, but still had the same problem. I tried using a bst file I had in my /home, which solved the problem. 

I explored the /usr/share/texmf-texlive/bibtex/bst and noticed most bst files, which had been present before upgrading to 8.04, were now missing. 

I wonder why this change occurred in texlive.

Thanks for the help.

---

### Post by kleeman on 2008-05-31
I am running 8.04 also and have plenty of bst files there. Sounds like either you have had a corrupt package installed or the upgrader removed some texlive packages because of dependency issues. I would reinstall (using synaptic) all my packages containing texlive...

---

