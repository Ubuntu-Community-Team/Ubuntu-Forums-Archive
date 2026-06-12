---
title: "Printing in Kubuntu"
date: 2005-11-07
forum: Desktop Environments
---

### Post by leo123 on 2005-11-07
Hi,

The printers - HP PSC 1315 & Epson Stylus C82.

When printing, the status of the document goes from "processing" to "queued" and a red "X" appears on the printer icon.

Googling or searching forums hasn't turned up any "SOLVED" on this issue.

Someone please help me solve this or point me in the right direction so printing is possible in Kubuntu.

Thank you

---

### Post by leo123 on 2005-11-08
Hi,

If anyone can suggest configuration files to check or anything else that would get me closer to PRINTING in Kubuntu it would be greatly appreciated.

Thank you

---

### Post by ltmon on 2005-11-08
Hi,

Can you print in non-kde programs?

What if you type into the terminal:

> lpr <somefile.txt>

Does that cause the printer to work?

Just trying to determine if this is a KDE problem, or a problem with the underlying system (cups).

L.

---

### Post by leo123 on 2005-11-09
Using the command you suggested results in "command not found."

The only lpr's that show up are: 
/usr/bin/make_driver_db_lpr
/usr/bin/lprsetup.sh
/usr/bin/unix-lpr.sh
/usr/lib/kde3/kdeprint_lpr.la
/usr/lib/kde3/kdeprint_lpr.so
/usr/lib/kde3/kdeprint_rlpr.la
/usr/lib/kde3/kdeprint_rlpr.so

What directory is "lpr" located in?

---

### Post by sdr_ar on 2005-11-09
In my case, with an Epson, I had to try with all of the drivers that appear. The one that works well for me is that called Epson xxx (the model) + CUPS ...
If that driver doesn't appear, try another driver.

---

### Post by sdr_ar on 2005-11-09
All the drivers appear in a list that Kubuntu proposes to you when installing or setting up your printer

---

### Post by leo123 on 2005-11-10
Thank you for your reply.

If I understand you correctly, you're saying to try all of the different drivers since the correct driver for my printer doesn't work.

Surely, the correct driver should work. 

Kubuntu is not ready and I'm not ready for it either. Something as simple as printing shouldn't be this difficult.

A challenge is okay every-now-and-then, but this is ridiculous.

The $hit doesn't work and if there is assistance with printing, where is it.

It's understandable that this is a user forum where users help one another, but if I keep posting then, I become the PROBLEM.

If not here, where can I get assistance with printing?

Thank you,

leo123

---

### Post by scokar on 2005-11-10
Are both of these printers USB?

If so, disconnect one printer from your PC and then reconnect it back into its usb port -- while the printer is powered up.

open a console window and type in: dmesg

do the last few lines seem to be activity about the printer you just plugged in?


to get lpr, try this command in a command prompt:

   sudo apt-get cupsys-bsd

then try the tests recommended above.

---

### Post by leo123 on 2005-11-11
Yes,

They're both usb printers.

Did what you suggested and there was activity showing the printer disconnected and reconnected.

Still can't print.

Installed the cupsys-bsd and gimp-print files.  What other files are needed to print?

Also, why do the files sent to the printer show up as "processing" and then switch to "queued?"

scokar, thank you for your post and any other suggestions you may have.

Is there a process of elimination to figure out why PRINTING is not happening?

---

### Post by leo123 on 2005-11-14
Hi,

Is there a list of printers that are known to work out-of-the-box with Kubuntu?

If so, where is the list?

Thanks,

leo123

---

### Post by f1dave on 2005-11-14
My HP Deskjet 970Cxi worked very nicely out of the box for me, and I've also had some Canon bubblejets work too. I'm not sure if you'll find a list, but [http://www.linuxprinting.org/](http://www.linuxprinting.org/) might be of some use to you.

---

