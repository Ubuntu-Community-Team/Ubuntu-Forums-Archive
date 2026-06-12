---
title: "SYSTEM &gt; ADMINISTRATION &gt; PRINTING doesn't work on ubuntu 9.10 !!!"
date: 2009-11-07
forum: Desktop Environments
---

### Post by chidokatoit on 2009-11-07
I want to configure my pdf printer , but after I install cups-pdf , I failed to start SYSTEM > ADMINISTRATION > PRINTING .
It just said something like " starting printing" and nothing happen ? 
Can anyone have me ??:popcorn::popcorn:

---

### Post by efflandt on 2009-11-07
Normally when you install cups-pdf it simply shows up when you go to System, Administration, Printing.  Are you saying that you do not see the PDF printer when you go there, or that you cannot get there to see it?

Or if you tried it and are looking for the pdf file, look in the PDF dir in your home dir ~/PDF

If you want it to save pdf files somewhere else, right click on the PDF printer and change Preferences.

---

### Post by chidokatoit on 2009-11-08
I mean i can't start PRINTING configuration , when i clicked on PRINTING icon ,nothing happened :(

---

### Post by gaothfanai on 2009-12-06
Same here, nothing happens - does anyone know the command line syntax to start the printing admin?

Thanks.

---

### Post by htseb on 2009-12-15
My HP Mini 1120NR has the same problem with U9.10.
The System->Administration->Printing application won't launch. 

I found this workaround in the forums.
                      
[LIST=1]
[*][SIZE=3]Use a web browser and go     to   [http://localhost:631/](http://localhost:631/)[/SIZE]
[*][SIZE=3]Choose the     [/SIZE][SIZE=3]**Administration**[/SIZE][SIZE=3]     tab.[/SIZE]
[*][SIZE=3]**Printer...Find New     Printer...Add this Printer**[/SIZE]
[/LIST]

It worked for me.

Good Luck.

---

