---
title: "xpdf does not include pdftops"
date: 2006-03-09
forum: Desktop Environments
---

### Post by nimy on 2006-03-09
Some pdf files require you to type in a print command to print them, and the appropriate print command is pdftops name_of_file.  However pdftops is not included in the ubuntu distribution.  Should I uninstall the ubuntu distro of xpdf and install from xpdf from source, or is there an easier solution?

---

### Post by thnogueira on 2006-03-09
There is a pdf2ps (numeral command). Is it a mistake?

---

### Post by thnogueira on 2006-03-09
There is a pdf2ps (numeral command). Is it a mistake?

---

### Post by thnogueira on 2006-03-09
There is a pdf2ps. Also, you should install xpdf-utils

---

### Post by nimy on 2006-03-10
I have xpdf utils installed on my ubuntu client, and I used pdf2ps to convert the file to ps format, thanks very much.  However when I sent the file to print to my ubuntu server, the printer did not respond (the file shows up in the print queue but doesn't print).  I copied the file to the server, converted it there and then it printed.  There's no indication of what went wrong in the cups error log.  Any ideas?

---

### Post by nimy on 2006-03-14
ok pdftops.conf is looking for the fonts locally - I suppose I could configure it to look for the server from the client machine but I'm not sure how to do that :(

---

