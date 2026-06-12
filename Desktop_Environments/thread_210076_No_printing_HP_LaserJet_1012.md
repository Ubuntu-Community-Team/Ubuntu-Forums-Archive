---
title: "No printing HP LaserJet 1012"
date: 2006-07-06
forum: Desktop Environments
---

### Post by babis85 on 2006-07-06
Hello, i 've just installed my printer HP LaserJet 1012 using CUPS from System->Administration->Printing->Add Printer and i have printed the CUPS test page successfully.
But, it doesn't print anything when i try to print a pdf file using acrobat. Furthermore, at the Printing->HP LaserJet1012->jobs there aren't any.
Any idea?

Moreover, i doubt if printing dublex side is supported. Isn't it?

---

### Post by babis85 on 2006-07-08
Hey guys, any help please??
I will appreciate it if anyone could tell me "Dublex printing is not supported yet, don't waste your time searching".
Thanks, in advance.

---

### Post by jobli on 2006-07-09
Hi!
Try: [http://www.linuxprinting.org/show_driver.cgi?driver=foo2zjs&fromprinter=HP-LaserJet_1020](http://www.linuxprinting.org/show_driver.cgi?driver=foo2zjs&fromprinter=HP-LaserJet_1020)
and [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

Compile the driver and follow the install instructions and you should be fine.

---

### Post by babis85 on 2006-07-09
Hello, thanks for your reply.
I forgot to mention that i have installed this printer using the HPLIP driver and it works fine except this problem.
Do i still have to install foomatic?
Can foomatic get on well with the HPLIP driver or shall i have problems.
Lastly, do you have such a printer installed using foomatic and printing dublex side? Have you tested that?
Thanks for your help.

---

### Post by babis85 on 2006-07-11
I found a manually solution.
First i print the odd number pages, the reload the printed papers and next print the even number pages.
To print the odd simply give the option ```
-o page-set=odd
``` to the /usr/bin/lpr command
To print the even simply give the option ```
-o page-set=even
``` to the /usr/bin/lpr command

---

