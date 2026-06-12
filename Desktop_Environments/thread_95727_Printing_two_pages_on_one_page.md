---
title: "Printing two pages on one page?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by ubuntuuser on 2005-11-27
Hi. I still need to print two pages on one single page because I have some very large documents I want to print. But everytime I select this option (Print... -> Paper tab -> Layout "2 Pages on 1") my printer (HP DeskJet 690C) ignores it and prints only one page per sheet. I am using hpijs as a printer driver and have installed HPLIP. I know about using pdfnup to get what I want, but in the long run this way is extremely userunfriendly. How can I get ubuntu to print the way I want it without using the command line? I have read somewhere that this way of printing is not supported with the ubuntu-delivered kernel, but I could not find that info again.
Are you able to print two pages on one via the GUI (e.g. out of evince or OOo), without using additional programs like pdfnup or psnup?

---

### Post by rattusdatorum on 2005-12-07
bump

come on! there must be a solution EXCEPT making pdf's with two pages -> one page "conversion".

---

### Post by drunken-wallaby on 2005-12-07
[QUOTE=rattusdatorum]bump

come on! there must be a solution EXCEPT making pdf's with two pages -> one page "conversion".[/QUOTE]

hi there. i use "gtklp" (sudo apt-get install gtklp) to do this...

hope this helps.

---

### Post by peacerist on 2006-01-03
Hi,

I have the same problem with Ubuntu breezy on 64-bit. Changing printer layout (2 pages on 1) settings does not work  me either through GUI. And still searching for an answer. :confused: 

Recently, I have installed Acrobat 7 32-bit and by changing its printer command from /usr/bin/lp to  /usr/bin/lp -o number-up=2  Now I can print double pages on one sheet . :) 


Hope it helps.

---

### Post by agapito on 2006-02-03
Thanks for the tip drunken-wallaby! Gtklp is great! :)

---

