---
title: "FAQ:  How to print from an application."
date: 2005-04-08
forum: Desktop Environments
---

### Post by michwill on 2005-04-08
Hello all.  I am curious as to the intricacies of printing over a network to either a Lexmark or HP laser.  At this point I can get a printer set up via the CUPS web interface, and get the printer(s) to successfully print a TEST PAGE.  However, when I go to print from an application, I get messages from the printers saying there is an error in the PS or PCL data.

I will eventually be writing my own backends to work with CUPS, but I need to get this basic functionality working first.  Any assistance would be greatly appreciated.

---

### Post by wernst on 2005-04-08
Well, it depends on the application. Firefox and Opera are two programs where printing doesn't work right out of the box.

The fix I use is to install "gtklp" from the Synaptics package manager. This is a gnome printer front end.

Then go to Firefox (or whatever program) and change the print command from "lpr....." to "gtklp...."

You'll get a nice dialog box with all your printer options when you print after you do this. It works great, and for all printers in CUPS.

-Warr

---

### Post by michwill on 2005-04-08
Thank you.  I'm curious though, how will this work with my backends once I decide to get them up and running?  I need a solution that allows CUPS to control the flow the entire way so that when the time comes it can pass to my backend. I would need to type something like "MYBACKEND://IP_ADDRESS".  So while this will allow me to print, it's not a CUPSified (I'm sure that's a word somewhere) solution.  Is it?  I'm almost positive there's something I'm misunderstanding

---

### Post by Franko30 on 2005-08-26
Hi,

thanks for the info.

But how am I going to use gtklp with OpenOffice (or other applications that don't have a printig command line like Firefox or Acrobat Reader)?

Franko30

---

