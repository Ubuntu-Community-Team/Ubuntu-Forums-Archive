---
title: "Printer Help for a HP 610CL"
date: 2005-08-04
forum: Desktop Environments
---

### Post by badboyz107 on 2005-08-04
Hey all, I know there are a hundred different printer threads but I cant find exactly what I need to know so thought I'd try another one....

I have a HP 610CL installed to my Ubuntu, and when I set it up it all seemed to go smoothly until I tried to print a test page.....then I get a page with about 2 symbols at the top and thats it.....

What do I need to do to resolve this issue, as the printer will be needed within the next week....

if anyone else knows a thread on here that addresses this issue please let me know!

---

### Post by mrcbrown on 2005-08-04
[QUOTE=badboyz107]Hey all, I know there are a hundred different printer threads but I cant find exactly what I need to know so thought I'd try another one....

I have a HP 610CL installed to my Ubuntu, and when I set it up it all seemed to go smoothly until I tried to print a test page.....then I get a page with about 2 symbols at the top and thats it.....

What do I need to do to resolve this issue, as the printer will be needed within the next week....

if anyone else knows a thread on here that addresses this issue please let me know![/QUOTE]
 I know some HP printers essientally get their programming at time of print, budget printers like mine (LaserJet 1000) require the instruction set to be sent to them FROM the OS shortly before - do check LinuxPrinting.org:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_610CL](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_610CL)

May not always be Ubuntu specific, but it definately gives some great pointers to possibly getting a step closer.

---

### Post by alastair lewis on 2005-08-04
HP have excellent linux support.

Use the HPLIP drivers from hpinkjet.sourceforge.net
The debian HOWTO will get you through the install process, but Ubuntu needs the libjpeg62-dev library as well (in stage 1) or configure will fail.
Also substitute cupsys for cups when you want to restart cups.

The tool box is excellent and the sourceforge forum will cover any other errors you run into.

---

