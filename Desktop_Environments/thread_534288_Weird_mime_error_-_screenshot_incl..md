---
title: "Weird mime error - screenshot incl."
date: 2007-08-25
forum: Desktop Environments
---

### Post by CRCarl on 2007-08-25
Whenever I try and open a PDF I get this error - (screenshot)

The filename "WPS54G user guide rev B.pdf" indicates that this file is of type "pdf document". The contents of the file indicate that the file is of type "PDF document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "PDF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 



Any ideas?

C

---

### Post by Wolki on 2007-08-25
> **CRCarl said:**
> Whenever I try and open a PDF I get this error - (screenshot)


Weird. Sounds like a buggy mime database... Did you do anything special regarding to pdfs (such as install software for handling them that was not provided by ubuntu)? And which version of ubuntu are you running?

Anyway. let's try to see if we can find the cause. Non-standard mime stuff should be either in the user's home ( ~/.local/share/mime/packages/) or in usr/local (/usr/local/share/mime/packages/), the stuff from packages is in /usr/share/mime/packages/. freedesktop.org.xml is the shared mime database and should be alright (if you suspect it got corrupted, try reinstalling the "shared-mime-info" package in synaptic), look at other files to see if another pdf mime type is declared somewhere. I'd look in the order I described them, and then first at a file named Override.xml if it exists (as these entries will take precedence over the rest of the files in that directory). If you find something tell me and we'll try to fix it (basically, remove the offending file, then run "update-mime-database <directory minus the "packages/">")

---

