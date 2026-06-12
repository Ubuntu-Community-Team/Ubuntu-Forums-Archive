---
title: "wine questions"
date: 2006-01-20
forum: Desktop Environments
---

### Post by drotter on 2006-01-20
I have two questions that im wondering if anyone has any experience with.

1.  I currently have xp dual booted with ubuntu.  Since I cant find my old office cds is there a way to run office through wine off the xp partition?

2.  Does anyone know how to install a microsoft installer (.msi) program with wine?  I havent figured out a way to do it but there must be a way since most windows programs are installed this way...


thanks for any help..

---

### Post by happyponcho42 on 2006-01-20
Ubuntu comes with OpenOffice.  Have you trialed it yet?  It's a completely free, almost-clon, of Microsoft Office.  All my documents switch between MO and OO without a problem.

---

### Post by drotter on 2006-01-20
I've tried oo and for the most part I have no problems with it.  But i do have some issues with powerpoint and some of the functions in excel.  Some files that i use are not completely compatible.
Its not a huge issue I just want to see if i can do it.
When i try and run "wine winword" from the windows partition through the terminal it tells me that 
"The visual basic environment can not be intialized"
"Add in template is no valid"
"Microsoft word has no been installed for the current user"
And then it closes.

But there are some other programs that i would like to run in linux.  A couple of windows based bioinformatics programs.  Thats why I'm wondering how to install a program with the windows installer (.msi file)

---

### Post by qaqa on 2006-01-21
I've installed wine 0.9.4 MS Office runs more or less fine on that.
After you apt-get wine, remember to install winetools as well. Winetools lets you install some additional windows libs which are needed by most windows apps. 
Addl info is on the wine website

---

