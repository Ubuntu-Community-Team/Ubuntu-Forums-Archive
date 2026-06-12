---
title: "Acroread and CUPS"
date: 2006-06-26
forum: Desktop Environments
---

### Post by mattG on 2006-06-26
Hello,

I installed the Acrobat Reader (with the help of Automatix) and it works fine. However, when printing PDF documents, the print dialog doesn't show my CUPS printers. Instead, I always need to use "lpr -P". My colleague (who is using Gentoo) also uses the Acrobat Reader and has a much more comfortable print dialog showing all printers...
Can anybody tell me whether this is a problem with the version of Acroread (I have 7.0.1), a problem with my configuration or whether my installation is lacking an important plugin?

Thanks!

MattG

---

### Post by padre999 on 2006-06-26
Same problem here...

I found a workaround to get it printing at least. I had to define my printer as the default printer. For that I went to System>System Settings>Printing (I have a German gnome, so the terms could be different)

In the appearing window I right clicked on my printer and chose "make default". Since then acroread prints fine using the usr/bin/lp command.

Still a printer dropdown menu and a proper printer setup menu should be expected in a powerful application as acroread. Other people are having the same problems in these forums. It seems to work with other distributions though.

Is there maybe some package that is missing in the repositories?

---

### Post by mattG on 2006-06-27
This workaround isn't a real solution for me as I need to be able to print to four different printers. For that reason, a graphical printer selection would be really nice...

---

