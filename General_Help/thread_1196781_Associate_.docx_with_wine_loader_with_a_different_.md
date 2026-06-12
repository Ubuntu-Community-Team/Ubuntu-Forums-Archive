---
title: "Associate .docx with wine loader with a different WINEPREFIX"
date: 2009-06-25
forum: General Help
---

### Post by tarekeldeeb on 2009-06-25
Hello all,

I have installed office_2007 on /opt/office2007, then copied some needed registry files to $USER/.wine_office2007 and linked others

I created an executable /usr/local/bin/word2007 having
 ```
env WINEPREFIX="/home/$USER/.wine_office2007" wine "C:\Program Files\Microsoft Office\Office12\WINWORD.EXE" $1

```

this works perfectly with:
1- terminal: word2007 mydoc.docx
2- desktop launcher that runs /usr/local/bin/word2007

But I want to associate the file-type docx with my installed office.

* The wine loader starts with .wine as WINEPREFIX
* When I select the previously created desktop launcher to open the document, nothing happens.

Can any one help?

thanks,
Tarek

---

