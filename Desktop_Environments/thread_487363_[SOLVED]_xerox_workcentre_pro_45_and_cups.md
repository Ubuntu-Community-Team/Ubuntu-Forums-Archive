---
title: "[SOLVED] xerox workcentre pro 45 and cups"
date: 2007-06-29
forum: Desktop Environments
---

### Post by xfred on 2007-06-29
I've just got a new ubuntu setup at work and am having a hard time setting up a xerox workcentre pro 45 printer.  So far I've done the following:

- tried the system->admin->printing: detected the printer correctly, but no matching driver and the suggested one (workcentre 450cp) didn't work.
- downloaded the driver Linuxi386XPXX_4.10.33.tar_ from the xerox site.
- installed ok after some fancy footwork (had to copy some binaries around to allow for different expected paths, but nothing too traumatic).

So, at present I can print stuff ok using the command:

```
xprint -n stuff.ps
```

which is better than nothing.  However I would like to integrate this properly with cups so that I can skip the whole convert to postscript step.  At present the print queue shows up fine in system->admin->printing, but when I print without using xprint it just shows 1 paused job (resume doesn't help).  Basically I guess I need to somehow tell it to use xprint -n rather than lpr or whatever when it prints to this printer, but I really have no idea where to even start looking for such a setting.  Suggestions please?

---

### Post by xfred on 2007-07-08
*bump* Anyone?  Suggested readings?  Random thoughts?  Anything?

---

### Post by JoeLinux117 on 2007-07-27
I can't really help you with the cups issue, but I was wondering what exactly you did in order to get the Xerox driver to install?  I'm struggling with that part right now because all I get after typing "y" to the agreement is some dots and then "ERROR: No such file or directory", and then it quits.  If you can help me with this, then you would have another person in the same boat as you, but two heads are better than one, right?  Thanks.

--JoeLinux

---

### Post by gonr on 2007-08-10
JoeLinux117, I just had the same 'Error: No such file' problem. 
xfred, I also managed to integrate it in cups:

** To fix the broken installer: The problem is they forgot to gunzip a temporary tar file.

Go to the Linuxi386XpxxInstall/ directory from the tar package, and run setup, and let it fail. Then go to /tmp/XeroxInstall and do
$ gunzip Linuxi386Xpxx.tar.Z
$ mv Linuxi386Xpxx.tar ../

Then go back to Linuxi386XpxxInstall/ and run setup again, but this time press ctrl-Z once you see a few periods appear in the setup process.  Go back to /tmp/XeroxInstall and do
$ mv ../Linuxi386Xpxx.tar ./
$ fg

and it should work.


** To integrate with CUPS:

Install the PrinterPackageXpxx package, I had no problems with it. Then, in the gnome-cups-manager, when selecting the driver, press 'install driver', and go to /usr/Xerox/ppd and select the ppd file with your printer number.

Allan

---

### Post by dark_harmonics on 2007-09-11
I wanted to reply that using the generic PPD driver from the /usr/xerox/ppd directory fixed the mention issue (printer sits at paused). This was on a workcentre 275.

So heres the total process:

Downloaded and installed the printer driver from Xerox (that worked without errors on this model for me)
Opened the add printer dialog and selected the printer from a list of detected printers (you could also do this by adding the IP since this is direct IP printing).
installed the driver for generic from the /usr/xerox/ppd directory 
Applied changes and printer added. 
Sucessful test print!

---

### Post by xfred on 2008-01-03
Thanks for the help guys.  I did eventually get it working with the help of someone much more experienced with Linux than myself.  I'm not sure how he did it but I do know that the xprint thing wasn't actually needed in the end (which is just as well, as installation was a pain, and the interface once installed was awful).

---

