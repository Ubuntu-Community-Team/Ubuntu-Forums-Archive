---
title: "bibtex problems -- title case"
date: 2009-10-07
forum: Education &amp; Science
---

### Post by rajan on 2009-10-07
Hi, I'm trying to write a big paper with pdflatex and I'm using bibtex for my references. I am having what I gather is a common problem -- that my titles are getting changed into lowercase even for things that shouldn't be changed. For example, the word CdS gets turned into Cds or cds, neither of which is acceptable. I tried to take the change.case$ command out of the .bst file i was using, but that started a whole bunch of other problems, including the title being followed by a "t" each time and the authors' names disappearing. 

Does anyone have a good .bst file that I can use that has the form:

J.Doe, M. Jane Synthesis of CdS Nanoparticles from Elements. *Journal of Fake Chemistry* **2009** 19, p12-154

I just need the information above, not in any particular order. I need the authors, the title of the article, the journal title, year, volume and inclusive pages. I have all of these things in my .bib file, but I am getting really desperate for a good .bst file. I've also tried the .bst files from the repository at [http://server.ccl.net/cca/text-processing/tex/bibtex/index.shtml](http://server.ccl.net/cca/text-processing/tex/bibtex/index.shtml)
but none of them are satisfactory. 

Thanks a lot in advance. 

rajan

---

### Post by samden on 2009-10-07
Forget the .bst file. 

In your .bib file, add an extra {} around the words you need to preserve the case of. For example:
```
 title = {How to eat CdS nanoparticles} 
```
becomes
```
 title = {How to eat {CdS} nanoparticles} 
```

---

### Post by rajan on 2009-10-07
works great ... i don't know why i thought this, but when i read that tip online a while ago, i thought the brackets were "[]" and not "{}" so it obviously didn't work. thanks for the tip. 

do you know any .bst files that will print the page numbers of the articles? it's probably not a big deal, since i can take a look at the sample.bst, but if anyone has one on hand i'd appreciate it.

---

### Post by spinoza666 on 2009-10-11
Maybe not what you're looking for but I quite like natbib with the chicago bibliographystyle. Then you pagenumbers as well.

---

### Post by spinoza666 on 2009-10-11
Crap I just realized that chicago doesn't quite fill all your criteria. It will put the year in a different place. Anyway if you check out natibib documentation on ctan I'm sure one of the styles there will suit your needs.

---

### Post by rajan on 2009-10-14
thanks for the reply, but it turned out i was just making a stupid mistake. i am using emacs to make my .bib file and i didn't know i needed to delete the "OPT" before the pages field. My .bib file read "OPTpages" so bibtex didn't read it. not sure why i didn't put that together on my own, but it might have been related to the 2 weeks i went without sleeping. project is done now, and after figuring out the emacs/bibtex problem, it looked great. all on linux too!

---

