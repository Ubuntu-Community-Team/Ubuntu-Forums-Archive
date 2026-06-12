---
title: "Cannot lauch desktop effects with ATI RV516"
date: 2007-12-05
forum: Desktop Environments
---

### Post by t1hall on 2007-12-05
Can anyone tell me how to reconfigure xorg so my desktop effects will work. For some reason it says Desktop Effects could not enable I have a Dell Optiplex 745/ATI RV516, Radeon X1300/X1550 Series?
Thanks for your help

---

### Post by aamod on 2007-12-07
Have you installed ATi drivers?

They're also available on [www.ati.com](www.ati.com) website.
you can also use Synaptic, search for ati. you'll get list of packages. install them and your xorg is ready

---

### Post by bimargulies on 2008-01-28
The reply here is just wrong.

Gutsy Gibbon amd64, at least, does not recognize the PCI express ATI RV516. I was able to get it to work by manually selecting the fglrx driver and manually editing a number of other parameters. I haven't tried desktop effects, but there are some 'missing symbol' complaints that lead me to believe that aiglx won't work.

---

