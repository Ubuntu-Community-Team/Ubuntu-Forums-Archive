---
title: "Help!  I can't get a Canon ip6700d to work with 8.10"
date: 2009-04-10
forum: General Help
---

### Post by Raemir on 2009-04-10
Ok, first, I'm not going back to windows over a printer.

However, I can't find any reason why I can't get my Canon ip6700d to work under Ubuntu 8.10.  It shows up in CUPS, I can select it as a printer.  The "print test page" doesn't look god-awful (it actually looks pretty good for a 2-3 year old printer).  But, whenever I try to print from any application, document viewer, Open Office, Gimp, it really screws up the print job.  For example, in document viewer, looking at a B & W PDF, it looks fine, but when I print it, nothing.  I get a blank page.  I initially though it was just black that wasn't printing, but I set up an envelope in Open Office (default version) and changed the color to blue.  Parts of the address showed up in different fonts, sizes, and all of it was blury--none of it was readable.

Suggestions?  And if you don't have suggestions to fix the problem, can you at least suggest a good photo printer that works?  I don't mind buying another printer, it just needs to work and right now I'm not sure the problems is the physical printer....

Thanks!

---

### Post by IdahoBackwoods on 2009-04-10
TurboPrint has a driver for it.  Check out [http://www.turboprint.info/](http://www.turboprint.info/)

TurboPrint costs money, but I found that I got better results using it with my Canon iP5000 and later my iP4500 than I could get any other way.  For some Canon printers you can get Linux drivers from Europe or Japan, but that didn't work as well for me as TurboPrint.

The problem is that Canon is not interested in cooperating with the Linux community.  I wrote to them and they basically said "tough luck."

---

### Post by Raemir on 2009-04-10
Thanks, I took a look but they want 30 EUR for it.  That's probably ~US$40 and the printer isn't worth it.  Push comes to shove, and I'd rather actually support a company that wants to support Linux, so maybe it's time to start looking for a new printer?

---

### Post by Raemir on 2009-04-10
Looking at Newegg, does anyone have any experience with a HP Officejet J6480 CB029A.  The price isn't bad.... and I need to be able to print.

---

### Post by mrufino1 on 2009-04-30
I was just battling this same issue on a friend's machine, he has the ip6700d. Using linux mint 6 (same as ubuntu 8.10, just dressed up a little), and it was only printing color, not black. When I went to printer properties, it had used the correct URI for the printer but had loaded the driver for ip6000 by default. I clicked the "Change" button, and the driver for the ip6700 came up, I picked the one that said "recommended" and the printer now works perfectly, at least printing black text. Didn't have the time to test further. Hope that helped!

---

