---
title: "printing a .ps file"
date: 2005-02-01
forum: Desktop Environments
---

### Post by Poldi on 2005-02-01
ok, this should be the easiest task on earth, but I am too stupid to get it right by intuition and to lasy to read a lot.

I have a .ps [Postscript]-file that I canread and view just fine with the Gnome-PS-Viewer application but there is no printing command setup and I don't know Ghostscript syntax by heart.

I want to print on a locally attatched (lpt1) HP LaserJet 1100 that is setup with CUPS and can print from Gnome, OO, Firefox just fine.

now, given a default Warty setup, how am I as a stupid end-user supposed to print a .PS-file given the Warty toolset?

there are a lot of tools that output .ps - in my case GnuCash, this is the HBCI-INI-letter to my bank - so this must be a common task even for a GUI-only user.

any help will be greatly appreciated.

kind regards,
Carsten

---

### Post by m4ng0 on 2005-02-01
I think the easiest thing to do is, from terminal,
lpr yourfile.ps
if you have only one printer, or
lpr -P"printername" yourfile.ps
if you want to choose the queue where the file will be sent.

---

### Post by Poldi on 2005-02-01
will this work on a non-Postscript printer?

[QUOTE=m4ng0]I think the easiest thing to do is, from terminal,
lpr yourfile.ps
if you have only one printer, or
lpr -P"printername" yourfile.ps
if you want to choose the queue where the file will be sent.[/QUOTE]

---

### Post by mirtux on 2005-02-01
[QUOTE=Poldi]will this work on a non-Postscript printer?[/QUOTE]
   Definitely yes using **hpijs **drivers, but for more information you can have a look here:  [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1100]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1100")
   The site is full of interesting notes!
 
 Regards,
 MC

---

### Post by Poldi on 2005-02-01
thanks a lot.

---

