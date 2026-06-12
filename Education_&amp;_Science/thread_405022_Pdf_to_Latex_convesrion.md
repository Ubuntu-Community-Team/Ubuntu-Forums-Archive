---
title: "Pdf to Latex convesrion"
date: 2007-04-09
forum: Education &amp; Science
---

### Post by slaanco on 2007-04-09
Hi guys,

is there any way how to generate Latex Source file from Pdf ? I tried google and found nothing relevant :( Is it possible to generate such conversion tool ? I was thinking about writing code that would act like pdf viewer, but instead of rendering graphical output it would interpret the commands for visual formatting to Latex formatting. The text would be transfered with pdftotext. Could you help me with it ? I'm not familiar with programming of such things. 

thanx

---

### Post by sam81 on 2007-04-09
just a hint, I think koffice has the ability to import .pdf files... don't know if that can help

out of curiosity, why would you want to get LaTeX source from a pdf?

---

### Post by slaanco on 2007-04-09
I want to get Latex source from pdf file, because there are some things that are more efficiently done in other app, which can export it to pdf.
Can KOffice export files to Latex ?

---

### Post by sam81 on 2007-04-09
yes, koffice can export to LaTeX, as well as OpenOffice. Don't expect great things from the koffice pdf import though, I just tried it an the results weren't that impressive... I think it depends on the complexity of your document

---

### Post by slaanco on 2007-04-09
thank you very much :)

---

### Post by ssam on 2007-04-09
remember that PDF's main design goal is visual layout. it does not contain structural information.

a latex will specify that something is a section or subsection heading, pdf only says what font,size and position the words should have.

also latex keeps track of figures, tables and references, and only puts the numbers in when exporting to pdf (or dvi if you are oldschool). the pdf file will just have the numbers, not the associations.

you would need clever code to rebuild all the information that is lost in a pdf file.

if you just want to make small changes to a pdf file you might find some useful information at [http://www.linux.com/article.pl?sid=07/03/09/1810218](http://www.linux.com/article.pl?sid=07/03/09/1810218)

---

### Post by frisket on 2007-04-09
> **slaanco said:**
> is there any way how to generate Latex Source file from Pdf ?

No. Not in the way that you mean. There are several quite good text-extractors from PDF, and even some which try to deduce structures like lists and headings, but their output is either Word (virtually useless) or XML (quite useful)...but not LaTeX format, as far as I know.

Trying to get LaTeX out of a PDF file is like trying to recreate whole cows out of hamburgers, or turn scrambled eggs back into chickens. A PDF is a dead-end document, a one-way street, and the process of creating a PDF obliterates all the useful information that was in the application that created it.

///Peter

---

### Post by kleeman on 2007-04-11
To reiterate since I had to do this recently:

You can get the text out but not equations.

I accidentally deleted my lyx file and had to recreate from a pdf. Not nice.

Looks like kword is one easy method to get the text.

---

### Post by raja on 2007-04-11
Abiword (with the plugins) can open a pdf and export as latex too. Again it is unlikely the formatting is going to come out very well.

---

### Post by timmie on 2007-04-16
Hi,
you can also try the commande line tools:
[[LIST]
[*]pdftohtml
[*]pdftotext
[*]null
[/LIST]

And then get the output into Latex.

---

### Post by slaanco on 2007-04-18
thanx a lot  to everyone :)

---

