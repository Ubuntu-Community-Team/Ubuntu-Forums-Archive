---
title: "Printer quit working sanely"
date: 2005-07-27
forum: Desktop Environments
---

### Post by elder68 on 2005-07-27
My printer is a Lexmark Optra EP,  Postscript Level 2 printer. It has worked fine through various levels of Mandrake, Red Hat, Libranet and up till now Kubuntu.

It was working fine, I did nothing to the printer or the system, and suddenly, any time I send anything to the printer, it simply prints out one line only, of letters and symbols at the top of the page. I have tried setting it as a generic postscript printer but get the same result.

When I print a test page of the printer itself (not a test page sent to the printer through the system, but a printer test page only) it works just fine.

Frankly, if I was not already bald as a billiard ball, I would be tearing my hair out. I have spent hours trying to get the printer working again.

Any help would be sincerely appreciated.

Bill.

---

### Post by rosslaird on 2005-07-28
I have also been sorely tried by this problem (including today). For me, it happens when I turn off the computer and printer that act as the print server on my network. Here's what I do to fix the endless stream of gibberish:

On the computer connected to the printer:

turn off the printer
from a terminal on the computer: sudo /etc/init.d/cupsys restart
logout and turn off the computer
turn on the printer
turn on the computer
log in

This procedure works for me every time (but it is a major hassle, which I try to avoid by just leaving the computer and printer on all the time).

I think the issue (at least for me) has to do with the order in which the computer and printer are powered up.

Cheers.

Ross

---

### Post by elder68 on 2005-07-28
[QUOTE=rosslaird]

turn off the printer
from a terminal on the computer: sudo /etc/init.d/cupsys restart
logout and turn off the computer
turn on the printer
turn on the computer
log in

This procedure works for me every time (but it is a major hassle, which I try to avoid by just leaving the computer and printer on all the time).

Ross[/QUOTE]

Thank you for the above and I will give it a try. It seemed to be something to do with stopping and starting but I could not figure it out.

Bill.

---

### Post by elder68 on 2005-07-28
[QUOTE=elder68]Thank you for the above and I will give it a try. It seemed to be something to do with stopping and starting but I could not figure it out.

Bill.[/QUOTE]

The printer is working again. I deleted all printers that I had been playing with and started again. Did what you suggested and the printing was OK. So then I turned everything off, printer and system, then I started the printer and waiting for it to fully load. Then I booted the system and was able to print again.

Thanks again for your help.

Bill.

---

