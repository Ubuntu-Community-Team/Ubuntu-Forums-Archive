---
title: "How to install the Samsung ML-1520 printer on Ubuntu Dapper - Gnome"
date: 2006-09-10
forum: Desktop Environments
---

### Post by oneTime on 2006-09-10
Forget all that tweaking like adding cupsys to the shadow group (and forgetting to remove it afterwards), enabling the root account (what happened to <adduser yourUserName lpadmin>?) etc. Don't even bother yourself with the printer's driver:

1. First connect and turn on your Samsung ML-1520 printer.
2. Make sure libgtk 1.2 is installed. If you for instance search for libgtk in Synaptic you can tell whether libgtk 1.2 is installed or not.
3. Let's click on: System ---> Administration ---> Printing. A 'printers' window pops up.
4. Double-click on 'New Printer' to start 'Gnome-cups-add'. Be patient! It takes a while for the printer data base to be read. If all went well you'll see a 'Add a Printer' pop-up window with your printer listed as detected.
5. Do not change anything. Confirm the default selections by clicking on the 'Forward' button. Samsung ML-15**1**0 and not ML-15**2**0 is selected in the next window by default! Yes you don't see ML-1520! No problem.
6. Select and submit ML-15**1**0 with the Forward button.
7. Fill in the name (ML-1520 and not the ML-1510 default), description and location of your printer. The information you enter here doesn't affect the working of your printer!
8. When finished, click on 'Apply'. Notice a printer named 'ML-1520-Ready' will now appear in the 'printer' window!
9. Start any application and test print a page.

Stay clear of all those discussions on the restoration of the CUPS web interface admin functions and just be productive with Ubuntu Dapper.

-OneTime
Who else could it be?

---

