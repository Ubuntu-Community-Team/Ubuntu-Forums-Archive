---
title: "Printing to a non-default printer with non-Gnome apps"
date: 2006-03-01
forum: Desktop Environments
---

### Post by unperson on 2006-03-01
My system is setup to use multiple different network printers.  When I'm printing from a Gnome app, like the Gnome pdf viewer, this works great.  When I go to print, I get a dialog allowing me to print on any of the printers I've setup in Administration->Printing.  

Sometimes, however, I want to print from an older app or 3rd party app, like acroread.  It doesn't give me any dialog, it just asks for a printing command.  The default is "/usr/bin/lp".  That works fine if I want to print to my default printer, but what do I do if I want to print to a non-default one?  Specifically, I want to print to one that is setup as a network printer using the "UNIX printer (LPD)" setting.  I wrote "gr" in the queue box in that setup window, and I assumed that later I could print to it using "/usr/bin/lp -d gr", but that does not seem to work.  I get "lp: unable to print file: client-error-not-found" if I enter that command from the command line.  So, what command can I use to print to this non-default printer?

---

