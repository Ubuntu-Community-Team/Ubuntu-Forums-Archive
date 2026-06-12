---
title: "Adding a printer"
date: 2007-05-02
forum: Desktop Environments
---

### Post by ctcarton on 2007-05-02
I'm trying to add a new printer with the gnome wizard but on the second page where it askes me to pick a driver there are none to choose from.  The Manufacturer list drop down is empty.   I just want to pick the generic postscript driver.  This wizard is asinine.  Anyone know how to fix it?

---

### Post by taurus on 2007-05-02
Which release are you running and what is the manufacture of your printer?  Is it connected by USB or parallel?

A little more info would be real helpful.

---

### Post by Sef on 2007-05-02
1) What printer do you have?

2) Click foward and not install from the menu.

3) If the Manufacturer list is empty, you may have had a bad install.

4) What commands did you use?  example: system > administration > printing > etc...

---

### Post by ctcarton on 2007-05-02
I'm running dapper.  The printer is a windows network printer. The first page of the wizard where I browse to the printer and login to the server works fine.   I don't see why the actual manufacturer is important since I just want to select a generic postscript driver but it's a Xerox WorkCentre 5030 PCL6.

I can't click forward in the wizard because the forward button is greyed out.  I launched the wizard from the menu, system -> administration -> printing.

Just fyi, I tried the kde wizard kprinter and it worked.  It gave me a big list of manufacturers and models to pick from.  I picked generic postscript and everything's working now.  However kprinter did give me a warning/error popup after I picked the driver saying that it couldn't install it for some reason.  That's probably related to why the gnome wizard doesn't list anything.  I just ignored that and everything works anyway.  Just printed my document with no problems.

I remember now at home when I installed my HP Deskjet 880C as a local printer I had the exact same situation. The gnome wizard would give me an empty list and not allow me to proceed.  Kprinter would let me pick the driver (hpijs in that case, not generic postscript) but then give me an error popup about installing the driver that I ignored and my printer worked fine anyway.

---

