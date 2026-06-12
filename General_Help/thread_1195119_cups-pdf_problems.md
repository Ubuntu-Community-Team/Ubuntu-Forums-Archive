---
title: "cups-pdf problems"
date: 2009-06-23
forum: General Help
---

### Post by nice_like_rice on 2009-06-23
Hi,

I was trying to print a document to pdf, apparently using cups-pdf is the way to do this.

I used "mkdir ~/PDF", then "sudo apt-get install cups-pdf". All went well, and I can then select "PDF" from the list of printers. Problem is that after printing, no file is actually created. No error messages, ~/PDF is still empty.

Permissions for PDF are 
drwxr-xr-x  2 david david 4096 2009-06-23 17:40 PDF

and the config file is set to save to this directory.

Any idea what I have done wrong? Or any other methods that could be used to achieve this. I am on 9.04.

thanks,

david

---

### Post by moster on 2009-06-23
funny, I used to have that same problem... I resolve it on some strange way that I cannot remember now. Now, after another installation of jaunty, that problem is gone. I can print right to pdf to my home directory.

Maybe you just need to run update on jaunty?

edit: I dont have any extra installed cups, pdf, etc... just plain jaunty.

---

### Post by nice_like_rice on 2009-06-23
Got it! :D

You were right about the strange way of solving it. I found many users with the same problem, and about 100 different solutions... I set the permissions of PDF to 777, and ran "sudo aa-complain cupsd", which fixed the problem. It's working great now!

david

---

### Post by kellysontheroad on 2009-06-29
This also worked for me (9.04 Jaunty Jackalope), and I did not have to create or change the PDF folder.

To sum up, if you want to print to PDF as we used to do with cutePDF in windows;
install cups-pdf using System->Administration->Synaptic or apt-get
open a terminal Applications->Accessories->Terminal and type sudo aa-complain cupsd

Things printed to pdf will show up in a folder labeled PDF in your Places->Home folder.

---

