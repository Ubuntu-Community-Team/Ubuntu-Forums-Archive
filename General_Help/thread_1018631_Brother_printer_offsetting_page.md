---
title: "Brother printer offsetting page"
date: 2008-12-22
forum: General Help
---

### Post by FlintZA on 2008-12-22
Hi, I have a Brother MFC-7225N on my network (connected directly to the router). I set up the printer for my Xubuntu 8.10 laptop, which was a breeze and all went flawlessly. When I print anything though, including a test page, the print is cut off at the top as if it's being offset too high on the page.
I have checked all the places I can think of to ensure the paper size is correct (A4), and did try modifying the top an bottom margins in the printer settings (this didn't have any effect at all). 
I have an Ubuntu PC on the same network which has no trouble at all printing correctly to the Brother, so it has to be a setting on the Xubuntu machine.

Any help would be greatly appreciated :)

---

### Post by LimCore on 2009-02-03
Hi,
I have the exact same issue here.
Printer: brother DCP-165C (driver: dcp165ccupswrapper-1.1.2-2.i386.deb)
amd64 ubuntu 8.04

The problem is the same: the top of the page is cutted off (in example I print PDFs with KPDF or any other).

One (bad) work around is to scale down the image, by setting (in print menu) the top margin to say 5.5 cm, then entire printout is smaller (a bit ugly) but it works.

* I seen some info that you could edit the printer definition file something, and define bigger printing region or something

* I written to some what appears to be support contact of Brother company, perhaps you (with same problem) should do so too - and please paste here if you get a solution!

Regards

---

### Post by LimCore on 2009-02-04
The Brother's support written back to me, and there is a solution that works for me :)

Actually it was in FAQ but I missed that part.

You have to edit config file, and set by hand A4 paper everywhere it seems.

[http://solutions.brother.com/linux/en_us/faq_prn.html#147](http://solutions.brother.com/linux/en_us/faq_prn.html#147)

I set =A4 in this rc file and that .ppd file, restarted cups, and now this all works.

---

