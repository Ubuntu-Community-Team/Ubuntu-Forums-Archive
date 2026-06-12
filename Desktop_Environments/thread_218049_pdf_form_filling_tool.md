---
title: "pdf form filling tool"
date: 2006-07-18
forum: Desktop Environments
---

### Post by whiteB on 2006-07-18
Is there any pdf form filling tool avilable..
   I have tried scribus,evince...not working..

---

### Post by aysiu on 2006-07-18
Filling? Adobe Reader.
1. [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
2. ```
sudo aptitude update && sudo aptitude install acroread
```

Filling and saving the filled form? There's no Adobe Acrobate Professional for Linux. Sorry.

---

### Post by whiteB on 2006-07-18
Thanks..anyway..
 I ve tried with adobe reader but i am not able to fill the forms.
 Are you sure there is no tools in linux for filling the pdf forms.

---

### Post by JoWilly on 2006-07-18
I don't know , never tried.

But, FYI, there's a google summer of code projet to add form filling support to gnome, so we should be seeing this in the comming months.

---

### Post by Tamihania on 2006-07-18
...I just found [pdftk]("http://www.accesspdf.com/pdftk/")
perhaps this will be the answer for your needs - there is deb file among downloads - should be easy to download and install through gdebi.

I hope it will help a bit,

tami

EDIT: there is also dapper version of pdftk for dapper in the universe!...ufff - just checked it...:rolleyes:

---

### Post by nick58b on 2006-07-18
whiteB, make sure you have the acroread-plugins package installed if you installed Adobe Reader from synaptic.

Also, Acrobat Pro 5 works well enough under wine to save PDFs with forms.

---

### Post by aysiu on 2006-07-18
> **whiteB said:**
> Thanks..anyway..
 I ve tried with adobe reader but i am not able to fill the forms.
 Are you sure there is no tools in linux for filling the pdf forms.
The form has to be designed to be filled out. It can't just look like a form. It actually has to *be* a form.

If it's not, then it can't be filled out.

The issue is whether the form can be *saved* once filled out, not whether it can be filled out at all. Adobe Reader will always let you fill out forms, but it will never (in Windows, Linux, or Mac) let you fill out things that simply *appear* to be forms.

---

