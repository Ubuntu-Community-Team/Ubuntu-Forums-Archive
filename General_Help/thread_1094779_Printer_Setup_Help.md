---
title: "Printer Setup Help"
date: 2009-03-12
forum: General Help
---

### Post by theiLLziLLa on 2009-03-12
Hi, I am a not a total noob but I am not exactly the most experienced user. I have an HP Photosmart c3150 printer and I have no idea how to set it up... btw I am using ubuntu intrepid... thanks

---

### Post by sgosnell on 2009-03-13
System, Administration, Printing.  Click on New, follow the wizard, and you printer will be installed and ready.

---

### Post by theiLLziLLa on 2009-03-13
Ok thanks thats definitely a start... but when I try and choose the printer from the database, my model does not show up

---

### Post by sgosnell on 2009-03-15
Then pick the closest model.  Some printers aren't supported, but they're rare.  I've been able to use every printer I've tried, several different brands and models, even though they weren't listed, by just picking the closest model.

---

### Post by HermanAB on 2009-03-15
Note that HP has Linux drivers for *all* their printer models.  So when all else fails, go to the HP web site, get a driver and follow their instructions to install it.

Cheers

Herman

---

### Post by ramjet_1953 on 2009-03-16
The easiest way to install HP printers is via HPLIP.

If you haven't already done so, go into Synaptic Package Manager.
[COLOR="Blue"]System>Administration>Synaptic Package>Manager[/COLOR].

Do a search for hplip

When the results come up, make sure that these packages are installed:

[COLOR="Red"]hpijs
hplip
hplip doc
hplip gui[/COLOR]

This will give you total control over your printer and a GUI install.

Regards,
Roger :D

---

### Post by theiLLziLLa on 2009-03-16
Thanks for all the help I got the printer installed... this great community was one of the reasons I switched to linux from that evil microsoft empire :)

---

### Post by sgosnell on 2009-03-16
Glad you got it working.  IME installing printers is far easier in Linux than in Windows.  My HP 6310xi still won't scan in Windows, even after hours on the phone talking to India and receiving a new CD in the mail.  Under several different Linux distros it took a few minutes, and under Ubuntu it was dead simple.  Same for the Brother at work.  Under Linux, printing just works.  Under Windows, it might and it might not, and you may have to jump through lots of hoops.

---

### Post by Arup on 2009-03-16
I truly wish I had my old HP Photo printer back, Canon just wouldn't support Linux. Truly saddens me.

---

