---
title: "how to use kprinter in the p-dialog?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by brannolte on 2005-05-11
Hi together

I'm using kde 3.2 on my other system and there is a printer "kprinter" in my printing dialogs.

On my laptop I'm using kubuntu with kde 3.4 and i cant install a printer kprinter to appear in my prininting dialog. 

The problem ist, that I often use different printer  and with the kprinter its easy, because i do not have to change the page size etc....

I found Kprinter on my laptop, but how do I tell KDE to use this as a printer ?

Need help please ... 

Greets matthias

---

### Post by Kurse on 2005-05-11
Are you talking about the print dialog in Mozilla/Firefox?

if so, you can change the print command from "lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}" to "kprinter --stdin", and this will enable Mozilla/Firefox to print using the kprinter interface.

---

### Post by brannolte on 2005-05-11
[QUOTE=Kurse]Are you talking about the print dialog in Mozilla/Firefox?

if so, you can change the print command from "lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}" to "kprinter --stdin", and this will enable Mozilla/Firefox to print using the kprinter interface.[/QUOTE]

Yes, but what is with the printer-dialog in OOO and other Programms. On my other maschine (suse) I can use Kprinter like a normal printer.

Can I install Kprinter like a printer in the KControlcenter or so?

edit: on 
[http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/I.LinuxKongress-2002-kdeprint/#startkprinter](http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/I.LinuxKongress-2002-kdeprint/#startkprinter)
i read that the kprinter normaly appears in the kde-print-dialog by default! but not on my system ;-(

---

