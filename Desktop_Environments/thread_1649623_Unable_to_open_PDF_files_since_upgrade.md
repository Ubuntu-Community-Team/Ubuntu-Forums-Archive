---
title: "Unable to open PDF files since upgrade"
date: 2010-12-20
forum: Desktop Environments
---

### Post by Bobhuber on 2010-12-20
Unusual problem. Since upgrading from 10.04 to 10.10 I am unable to open up any PDF files with document viewer as root. If I open nautilus with gksu,then attempt to open a PDF file it does nothing. I can go to Places from the main menu and right click on the file and open it just fine.I've checked the file properties and they are correct.

---

### Post by 3Miro on 2010-12-20
You can try to delete /root/.gnome2/evince, hopefully this will help.

Opening .pdf files as root is a very bad idea. Why would you ever need to do that?

---

### Post by Bobhuber on 2010-12-20
> **3Miro said:**
> You can try to delete /root/.gnome2/evince, hopefully this will help.

Opening .pdf files as root is a very bad idea. Why would you ever need to do that?
Didn't help. Thanks.
The question is not why I want to  but why the file wont open. Some more insight into the problem. Forget about the PDF file. Evince won't open at all as root even from a terminal.

---

### Post by oarion7 on 2010-12-20
> **Bobhuber said:**
> Didn't help. Thanks.
The question is not why I want to  but why the file wont open. Some more insight into the problem. Forget about the PDF file. Evince won't open at all as root even from a terminal.

What kind of output do you get when trying to run it from the terminal? Or does it just hang?

Uninstall and reinstall evince through sudo in the terminal via apt-get?

---

### Post by Bobhuber on 2010-12-20
> **oarion7 said:**
> What kind of output do you get when trying to run it from the terminal? Or does it just hang?

Uninstall and reinstall evince through sudo in the terminal via apt-get?
Did that. No luck.Heres the terminal error.

No protocol specified
Cannot parse arguments: Cannot open display: 

If I open evince from a standard terminal it works fine.

---

### Post by Frogs Hair on 2010-12-20
Try right clicking the pdf document and select open with another application ,select document viewer and make sure the remember this application box is checked.

---

### Post by wilburg on 2011-03-14
My evince will not open either from the gui or from a terminal. I get a 'no protocol specified' in a terminal and simply nothing in the gui. No warning, no error, nothing. Help here would be useful.

---

### Post by fonsi2099 on 2011-06-22
I have that: 
"Unable to open document. File type unknown (application/octet-stream is not supported.)" 

Thank you for replay

:guitar:

---

### Post by Bobhuber on 2011-06-22
> **fonsi2099 said:**
> I have that: 
"Unable to open document. File type unknown (application/octet-stream is not supported.)" 

Thank you for replay

:guitar:
Since I looked for days before finding the answer I'll give you a clue.
/etc/apparmor.d
edit the usr.bin.evince and the /abstractions/evince files

---

### Post by fonsi2099 on 2011-06-23
Sorry, It has not worked and I noticed that the o-oficce docs are not opening too, it is asking for ASCII filter options and after the doc is completly not readable
Thank you
:KS

---

### Post by fonsi2099 on 2011-07-28
Please update that thread to UNSOLVED.

"Unable to open document. File type unknown (application/octet-stream is not supported.)" 
Thank for any help

:guitar:

---

