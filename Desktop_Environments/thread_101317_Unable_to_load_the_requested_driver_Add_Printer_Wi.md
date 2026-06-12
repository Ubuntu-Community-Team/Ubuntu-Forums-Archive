---
title: "Unable to load the requested driver: Add Printer Wizard in sys Settings"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Bagleemo on 2005-12-09
Hello:

When I try to add my Epson C86 printer with Add Printer Wizard in KDE System Settings (administrator mode), I get the following error message:

Unable to load the requested driver:
Unable to create the Foomatic driver [Epson-Stylus_C86,gimp-print]. Either that driver does not exist, or you don't have the required permissions to perform that operation.

Any ideas?

Also sounds like this bug:

[http://ubuntuforums.org/showthread.php?t=64963&highlight=Unable+load+requested+driver%3A](http://ubuntuforums.org/showthread.php?t=64963&highlight=Unable+load+requested+driver%3A)

Thanks

---

### Post by sdr_ar on 2005-12-09
Well, for Epson printers I recommend you to use the Turboprint drivers. I had the same problem as you with my Epson, and since i use the Turboprint driver it works almost perfect. Download the free edition.
The site of TurboPrint is:
[LIST]
[*][www.turboprint.de/english.html](www.turboprint.de/english.html)
[/LIST]
It has a Debian packet to download that works in Ubuntu/Kubuntu.
Regards.

---

### Post by Bagleemo on 2005-12-10
Thanks! I'll give that a try. 
I have since posted this as a bug with KDE, and the developer there said he thought it might be a packaging problem.  So, I figured I'd put some more details here to see if that is the case.  

From Bug 118027: Add Printer wizard fails: : Unable to load the requested driver:

Using KUbuntu 5.10
Open System Settings
Printers
Administrator Mode
Add > Printer
Add Printer Wizard
Local
Select Epson C86 (as detected)
Next
Gives error:

Unable to load the requested driver:
Unable to create the Foomatic driver [Epson-Stylus_C86,gimp-print]. Either that driver does not exist, or you don't have the required permissions to perform that operation.

Thanks!

---

### Post by Bagleemo on 2006-04-04
Hmmm... I've been rebooting windows to print... Oh so nasty... Can't figure out how to fix this problem.  It is especially annoying as my printer did used to work in release 5.04.  Anybody got any other ideas? The turboprint thing doesn't really look like a workable solution.

---

### Post by cosborn72 on 2006-06-05
Are you able to print at all?  I got the same message trying to set up a networked Lexmark T522.  However, the system went ahead and installed it as a raw printer.  It provides me with basic functioning, although I can't set any preferences.

---

### Post by jarlethorsen on 2006-06-05
For whats it worth I experience the exactly the same problem as Bagleemo (using the same setup). I really hope someone comes with a solution so I again can start using my printer. I haven't been able to get it working since moving from Mandriva to Ubuntu. Now I'm running Dapper.

---

### Post by Ze Fernandes on 2006-06-07
I have a Lexmark Z42 and I can print in OpenSuse, PCLinuxOS and I have printed with Ubuntu 5.04. Now I tried Dapper and I configure the printer but I get a blank paper, nothing prints in it. And it takes a long time for the paper to come out of the printer.

Help anyone ????
Thanks

---

### Post by Wollongong on 2006-06-17
I had the same problem as described above, with Samsung ML-1710 printer. Setting up the printer in the control panel gave the message "Unable to create the Foomatic driver ...". Trying to use it took a long time, and no paper came out.

From another mailing list, I found the suggestion to see what drivers are available, using this command as a regular user:
$ foomatic-datafile -A | grep Samsung    (or your printer name)

This found that my model was not listed (in Kubuntu 6.06)
From a linux printing website, I found that Samsung printers are
all much the same, and typically run with the same driver. By selecting "Samsung 1210 gdi" (that was found in the datafile), it all works OK now.


I wonder why printers are apparently missing in the datafile for (k)ubuntu 6.06?


Hope this helps.

Wollongong
Australia

---

### Post by alarson on 2006-06-18
Looks like kde/cups/foomatic is somehow hosed:

```
# printconf 
*** glibc detected *** double free or corruption (!prev): 0x0816e838 ***
Unable to read printer database.  Please ensure the "foomatic-db" package is
installed properly.
```

I installed gnome-cups-manager and it installed my HP882C printer without incident.

---

### Post by johanhake on 2006-06-21
I also had this problem.

Thanks for the some what ugly workaround with gnome-cups-manager that btw worked fine!

---

### Post by fadli on 2006-07-24
i also have the problem, at last solved it with this command:

# foomatic-cleanupdrivers

run it in kubuntu. then try to setup your printers again

---

### Post by donbbb on 2006-08-05
Had a similar problem in Knoppox 5.0.1 ...

First, CUPS was not running so I had to start a root Console and type cupsd (or similar, you might or might not need this - it is necessary if the web interface (next) reports page not found)

Then, as all attempts using KMenu | Control Center | Peripherals | Printers failed with  "Unable to load the requested driver:"
I used the web interface through ...
   [http://localhost:631/admin](http://localhost:631/admin)
then followed 'common sense' e.g. Add printer ...

There was a limited selection of generic drivers e.g.
Model: Epson Stylus Color Series CUPS v1.1 (en)
Model: Epson New Stylus Color Series CUPS v1.1 (en)
Both work very well (col/B&W; text and graphics; hi/lo res) with my Stylus C62

After the printer was successfully installed through the web interface, I was able to use all the options available from KMenu | Control Center | Peripherals | Printers

Donb

---

### Post by arvs on 2006-08-25
> **fadli said:**
> i also have the problem, at last solved it with this command:

# foomatic-cleanupdrivers

run it in kubuntu. then try to setup your printers again

I had the same problem with an HP Deskjet 690C and this solution fixed it. Thanks a lot!

---

### Post by cypher35 on 2006-08-28
thank you very much, that fixed it.  i was pulling my hair out this morning...

someone should fix the installer so this doesn't confuse newcomers.

---

### Post by elpuerco on 2006-09-11
Helllllllllp!!!!

HP5150.

Install gnome-cups-manager retried no joy

foo.....cleanupdrivers retried no joy

web interface keeps asking for cups password?  enter admin name & passord prompts amd prompts for cups password?

What gives???

Help

---

### Post by dsmyers2163 on 2007-11-15
I was having trouble loading a laserjet 3 driver - tried several other drivers - same problem - same error message "Unable to load requested driver".  Some drivers would load some would not - the ones that would not load returned "unable to load driver error".  Ran the following command at command line "foomatic-datafile -A"  - output indicated corruption in foomatic datbase - ie "*** glibc detected *** double free or corruption (!prev): 0x0816e838 ***"

Ran the following command at command line "foomatic-cleanupdrivers" - output indicated many errors were corrected - all errors were corrected by the removal of blank lines in the printer database.

I can now add any printer driver that was not loadable before running the cleanupdrivers command on the database.




.

---

