---
title: "KDE software wants to print on ISO A4 (I want US Letter)"
date: 2010-01-25
forum: Desktop Environments
---

### Post by Pafnoutios on 2010-01-25
When I try to print from KDE programs, my printer asks me to insert A4 paper before it prints.

My printer is an HP LaserJet 5Si. I'm using cups configured through HP gui device manager with the hpijs PCL3 driver.
My CUPS configuration, HP manager configuration, and KDE printer manager configuration all say letter is the default paper size.
My KDE Regional settings say USA location and letter paper default.
Output of locale says en_US.UTF-8 for all entries including LC_PAPER.
Output of paperconf says letter, and /etc/papersize says letter.

But when I try to print, my printer asks for A4 paper.  This includes from Konquerer browser and okular PDF viewer on letter size pdf's (according to the File/Properties dialog).

The following usually works as a workaround.  After selecting print from the File menu, the print dialog comes up.  I click on the button that says "Properties" next to the printer selector drop-down box.  The printer properties dialog already says letter paper.  I press the "OK" button without doing anything.  Then I press the print button on the print dialog.  My document prints on letter paper.  Just opening and closing the printer properties dialog usually gets it printed on letter paper.  Sometimes I have to click on the Advanced tab in the printer properties dialog before closing it.

Printing from non-KDE programs (Firefox and OpenOffice) has no problems.

---

