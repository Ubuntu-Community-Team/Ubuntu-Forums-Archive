---
title: "Desktop Effects no longer works (ATI 200M)"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by kirtimaan on 2007-04-26
Hello,

I am using ATI Radeon 200M XPRESS graphic on my Compaq notebook. Today I have installed Ubuntu 7.04 and all went fine. 

First while ATI drivers was disabled (System -> Administration -> Restricted Device Driver) I clicked on Desktop Effects item. That made my whole desktop while and I wasn't able to see any thing. When I pressed ALT + F4 it come back to normal. Then I googled and found beryl. I installed that using instructions shown on Ubutnu guide. I checked that and tried various themes and then un installed that. Now when i go to Desktop Effects, I get an error message saying : 

The Composite extension is not available


I checked my Xorg.conf file and found that in extensions section Composite is set to false. I searched for that and found that it is required for ATI drivers to enable 3d accel. 

Can any one suggest if I can get Desktop Effects item working ? My laptop have 256 mb ram and ATI card have 32 mb.  I am using AMD 3000+ (1.8ghz) processor.

Thanks, Kirtimaan

---

### Post by danboy on 2007-04-26
As far as I know the ati 200m only works with the proprietary FGLRX drivers (they're in the muliverse repos) and XGL. make sure you have these installed and working (there are threads all over these forums).

The good new is I have compiz and desktop effect running well on my 200m. It can be done. Just find and follow one of the many compix/xgl guides.

Good Luck.

---

