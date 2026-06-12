---
title: "Several problems"
date: 2009-02-03
forum: General Help
---

### Post by jijin on 2009-02-03
I recently updated my computer after a few months and I have had several problems.

I have a Ath5k wifi card on my laptop, and I normally use this method to get it working again after updating the kernel:

[http://ubuntuforums.org/showthread.php?t=929486](http://ubuntuforums.org/showthread.php?t=929486)

However, I decided to try a different method, and now I'm worse off then when I started.

I did the update and as usual with a kernel update, everything worked except my wifi.

I decided to use a different method to fix it located here:
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

After the final reboot in that tutorial the wifi connects to a AP but then does not connect fully. Also my nvidia driver is not working.

I probably should have sticked with what works and would like to go back to that if possible. Looking it over, I think I have a problem with the "sudo update-rc.d -f linux-restricted-modules-common remove" part of the tutorial.

Does somebody here know how to reverse that command? Looking at the man pages for update-rc.d is over my head. Reversing that I hope will fix the nvidia driver.

After that gets fixed I need to do completely remove what happened with this tutorial and need help with that as well.

Thanks.

---

### Post by jijin on 2009-02-03
bumping for help

thanks again

---

