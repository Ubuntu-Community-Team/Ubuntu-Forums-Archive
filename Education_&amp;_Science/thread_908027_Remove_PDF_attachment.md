---
title: "Remove PDF attachment"
date: 2008-09-02
forum: Education &amp; Science
---

### Post by stumbleUpon on 2008-09-02
Hi,

I use pdftk ([http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)) to attach bibtex files to PDFs and then use them to maintain a bibliographic database for my research papers. 

I do this because when i rename or move the PDFs around, it is convenient to have the bibliographic information right in the file. Hence i decided to use pdf attachments to store bibtex info.

I sometimes need to edit the attached bibtex file.

How do you remove attachments from a PDF?

The existing option in pdftk 'unpack_files' only dumps the attachments, it does not remove them from the PDF. 

Attaching another file with the same filename does not overwrite the already attached file -- it just renames it as filename.ext-1, filename.ext-2 and so on.

Is there a way to remove the PDF attachments completely...?

---

### Post by parktownprawn on 2008-11-19
apparently you should eventually be able to do this with evince or okular. 

in the meantime i have two suggestions:

1) you can run something like pdf-xchange via wine. it works relatively well for me. 

2) there is a tedious way to do this with pdftk:

- extract the relevant page 
- convert the page to ps and then back to pdf. this will kill the attachment
- insert the page back in your document.

---

