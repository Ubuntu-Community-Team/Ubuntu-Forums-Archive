---
title: "Wrong fonts being displayed in PDF file"
date: 2006-06-10
forum: Desktop Environments
---

### Post by WebDrake on 2006-06-10
Hello all,

I've noticed that various PDF files don't display correctly in Ubuntu, either in the Linux PDF viewers or in Adobe Acrobat.  I had a similar problem when I was using SUSE, except that here Acrobat displayed them correctly.  I'm guessing this is to do with proprietary fonts being packaged with SUSE's acroread, but not Ubuntu's.

As an example, see [http://neuro.webdrake.net/papers/wakeling_bak_2001.pdf](http://neuro.webdrake.net/papers/wakeling_bak_2001.pdf).

I attempted to install Acrobat from Adobe's download site but this didn't work---Ubuntu couldn't deal with the rpm, citing many missing dependencies.

Can anyone suggest a solution?

Many thanks,

     -- Joe

---

### Post by Rondonjin on 2006-06-10
[QUOTE=WebDrake]Hello all,

I've noticed that various PDF files don't display correctly in Ubuntu, either in the Linux PDF viewers or in Adobe Acrobat.  I had a similar problem when I was using SUSE, except that here Acrobat displayed them correctly.  I'm guessing this is to do with proprietary fonts being packaged with SUSE's acroread, but not Ubuntu's.

As an example, see [http://neuro.webdrake.net/papers/wakeling_bak_2001.pdf](http://neuro.webdrake.net/papers/wakeling_bak_2001.pdf).

I attempted to install Acrobat from Adobe's download site but this didn't work---Ubuntu couldn't deal with the rpm, citing many missing dependencies.

Can anyone suggest a solution?

Many thanks,

     -- Joe[/QUOTE]

There are various font packs available to download on Adobe's site. I can't remember the exact URL right now.

Wayne

---

### Post by mannheim on 2006-06-10
The pdf file in your link uses the Times family of fonts. The Adobe Reader that is packaged for ubuntu does not include these fonts, and so the Reader subsitutes its own (which don't look the same -- for example, the italic will just be a slanted version of the roman font).

I worked around this in my own case by copying the fonts from another installation. The relevant directory in ubuntu is /usr/lib/Adobe/Acrobat7.0/Resource/Font/ and here is the listing, with all the needed fonts added:

```
 ls /usr/lib/Adobe/Acrobat7.0/Resource/Font/
AdobePiStd.otf              HEB_____.ttf           MyriadPro-Regular.otf
COBO____.ttf                HEN_____.ttf           PFM
COB_____.ttf                HEO_____.ttf           SY______.PFB
CON_____.ttf                MinionPro-BoldIt.otf   timesbd.ttf
COO_____.ttf                MinionPro-Bold.otf     TIMESBI.TTF
CourierStd-BoldOblique.otf  MinionPro-It.otf       TIMESI.TTF
CourierStd-Bold.otf         MinionPro-Regular.otf  times.ttf
CourierStd-Oblique.otf      MyriadPro-BoldIt.otf   ZX______.PFB
CourierStd.otf              MyriadPro-Bold.otf     ZY______.PFB
HEBO____.ttf                MyriadPro-It.otf

```

If you compare the fonts listed here with your machine, you'll find you have some missing. Some are avaiable in msttcorefonts. I grabbed the rest from my Windows installation.

---

### Post by WebDrake on 2006-06-15
Many thanks for useful info. :)

---

