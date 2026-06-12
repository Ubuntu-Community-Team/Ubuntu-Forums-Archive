---
title: "Sane &amp; Xsane only work as super user"
date: 2009-01-25
forum: General Help
---

### Post by SneakPeak on 2009-01-25
Hello,

I have a Scanmaker X6 from Microtek.  Sane and Xsane only work when I run them as superuser.

How can I fix this so that they work when I run them as a normal user?

I am running on 8.10 Intrepid

Thanks

Sneaks

---

### Post by wolfen69 on 2009-01-25
go to system>administration>users and groups. click unlock button. enter password. go to manage groups. highlight scanner, then click properties. make sure your user name is checked. then in the the previous manage groups window, highlight saned and do same. you may need log out or reboot for settings to take effect.

---

### Post by SneakPeak on 2009-01-26
Thanks Wolfen69

That has worked.  I still have two problems:

1. Everytime I exit Xsane I get an error "Failed to creat file: Permission denied" 
2. The scan comes out fine but the preview is unreadable nonsense.

SneakPeak

---

### Post by lionel47 on 2009-01-26
Check to make sure you have permissions to the default directory for saving images.

---

### Post by SneakPeak on 2009-01-26
Hi 

Adding myself to the scanner and saned groups solved the problem of sane and xsane.  Changing the permssions on the file Microtek:ScannerX6USB.drc solved the Permission denied problem.  I am still getting rubish on the preview in xsane though.  Also the thread tools won't let me mark this thread as solved.  Why is that?

Sneaks

---

### Post by albinootje on 2009-01-26
> **SneakPeak said:**
>  Adding myself to the scanner and saned groups solved the problem of sane and xsane.  Changing the permssions on the file Microtek:ScannerX6USB.drc solved the Permission denied problem.  I am still getting rubish on the preview in xsane though.

Are you saying that the preview worked fine when running as root ?
> Also the thread tools won't let me mark this thread as solved.  Why is that? 

The SOLVED and thanks have been temporarily removed because of stability reasons.

---

### Post by SneakPeak on 2009-01-27
> **albinootje said:**
> Are you saying that the preview worked fine when running as root ?

No the preview doesn't work irrespective of whether I run the program as a normal user or as root.  


> **albinootje said:**
> The SOLVED and thanks have been temporarily removed because of stability reasons.

Ok.

---

### Post by albinootje on 2009-01-27
> **SneakPeak said:**
> No the preview doesn't work irrespective of whether I run the program as a normal user or as root.  


For this specific question I suggest you search the archives of the sane project, and ask at the sane mailing list.

---

### Post by SneakPeak on 2009-01-27
> **albinootje said:**
> For this specific question I suggest you search the archives of the sane project, and ask at the sane mailing list.

Will do thank you.

---

