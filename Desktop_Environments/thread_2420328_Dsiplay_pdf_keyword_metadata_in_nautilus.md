---
title: "Dsiplay pdf keyword metadata in nautilus"
date: 2019-06-03
forum: Desktop Environments
---

### Post by alanbeck on 2019-06-03
Hi there, I am a recent convert to linux and really enjoying it so far  but I have come across a really annoying problem that is preventing me  from moving over fully. I do a lot of work with pdf files and have over  15,000 of them in a folder to work with.  I frequently have to do  searches and to make things easier I have information stored in the  “keywords” metadata section of the pdf. In windows I can view all the pf  thumbnails using windows explorer and can also display the pdf tags  using a COM program called pdf property extension.


 [https://coolsoft.altervista.org/en/pdfpropertyextension](https://coolsoft.altervista.org/en/pdfpropertyextension)

 
I need something similar for linux and thought the nautilus columns extension for nautilus would do the job for me.

[https://www.linuxuprising.com/2019/02/nautilus-exif-pdf-and-audio-metadata.html](https://www.linuxuprising.com/2019/02/nautilus-exif-pdf-and-audio-metadata.html)

The extension is pretty old and I am unsure if it is still supported, but I managed to get it installed and working.  The only problem is that pdf keywords are not one of the options available to display.  I think it may be possible to show them by altering the python code shown here

[https://gist.github.com/escoand/cf1605f7e0410b319fcb](https://gist.github.com/escoand/cf1605f7e0410b319fcb)

but I have no knowledge of python or where to start.

Has anyone been able to get this to work or have an alternative

Thanks

---

### Post by TheFu on 2019-06-03
I would caution against dropping Windows for Linux if PDF file creation and management is your primary need, especially if other people provide the documents.  

Linux PDF support is years behind, often unable to open newer PDF versioned files at all.  But there might be commercial PDF viewers/editors that will handle the newer PDF versions.  I'm talking about the Adobe PDF file format versioning, not any specific tool.  Last time I looked, most Linux F/LOSS tools supported v1.6 of the PDF standard, which is very old.  I've had problems even opening IRS PDF files, because the IRS used to create them using the newest PDF standards.

---

### Post by alanbeck on 2019-06-04
I am using master pdf editor on linux which is adequate for my needs, and creating the pdfs myself using a scansnap ix500.  The scanner does work in linux but a lot of the functionality of the scansnap software is lost as it doesn't run on linux so I have to  run it in a windows VM which isn't the end of the word but not ideal either.  I could do this for explorer as well but linux should work ok for the pdf metadata editing using master pdf editor if I can just find a way to display the tags though the file manager.

---

