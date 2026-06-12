---
title: "some pdf files can not be viewed under root account"
date: 2011-03-11
forum: Desktop Environments
---

### Post by babybellabell on 2011-03-11
Hi, 
     My laptop is running ubuntu 10.10,  upgraded to kernel 2.6.36.  
     Today I switched my work space and files from a normal user account to root account,
because I need to run some experiments using root level access.  
Now I can not view some of the pdf files,  for example,  
one of the .pdf files I created from latex.  
The document viewer gives this message:  
"unable to open document,  access denied.  
Error opening file: permission denied."  
At the same time,  the document viewer has no problem opening some pdf files I downloaded
from the internet. 

I kept a copy of the files in my previous user account,  and when I switch back to that account, 
I can open them with document viewer without any issue. 

I tried  chmod 755  but it does not help. 

Can someone enlighten me what is going wrong?  Is my file system corrupted?  Is my kernel 
broken somewhere?

Thanks  a lot for your help!
yy

---

### Post by smiddy84 on 2012-10-29
Hello,

I experienced a similar problem when saving pdfs to a ntfs partition without the ending ".pdf"

In my case the following helps: Rename your file and add ".pdf", e.g. change "pdf_file" to "dpf_file.pdf". Afterwards I can work with this file as usual.

Best
Markus

---

