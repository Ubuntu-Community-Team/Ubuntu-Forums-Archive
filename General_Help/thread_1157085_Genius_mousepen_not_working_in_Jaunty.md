---
title: "Genius mousepen not working in Jaunty"
date: 2009-05-12
forum: General Help
---

### Post by admarshall2 on 2009-05-12
Hi,
I'm having a lot of trouble with my Genius 8X6 mousepen since moving to Jaunty. It worked fine without any manual configuration by me in Hardy Heron. But I did a clean install of Jaunty last night, and now it won't move. When using the mouse on the tablet, right-clicking does open the context menu. But I can't move from the center of the screen. I am not very savvy with Linux yet, so any help would be greatly appreciated.
Thanks in advance

---

### Post by admarshall2 on 2009-05-12
I'd really appreciate some assistance.

---

### Post by Favux on 2009-05-12
Hi admarshall2,

I'm sorry I can't help you directly but maybe I can point you in the right direction.

I don't know what you mean by:
> It worked fine without any manual configuration by me in Hardy Heron.
I thought you had to install the driver and configure xorg.conf as this wiki page shows:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)  And the link to the Hardy setup:  [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)

Basically the driver does not yet work for the Xorg Xserver 1.6 in Jaunty.  But it looks like the problem has been solved:  [http://aur.archlinux.org/packages.php?ID=18158](http://aur.archlinux.org/packages.php?ID=18158)

The link to the Intrepid HOW TO:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  You can see he has the 0.7.0 alpha 2 driver there now.  And a link to the 0.7.0 alpha 1 driver:  [http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html](http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html)

Hopefully that's enough info. to get you going, and some people you could potentially contact.

Good luck!

---

### Post by vanaardt on 2009-07-20
Favux,
thanks for the info, the link to [digitalbluewave]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") gives all the relevant information.

The only problem I had was with compiling the driver but as [tjpp]("http://http://aur.archlinux.org/packages.php?ID=18158") noted : > Does not work with xorg 1.6.0. To compile it with the new xorg, I have removed xf86GetMotionEvents from src/wizardpen.c in the faulty line (line 659, IIRC).

Works great now!

---

### Post by Favux on 2009-07-23
Hi vanaardt,

Glad I could help.

---

