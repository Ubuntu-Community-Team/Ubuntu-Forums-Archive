---
title: "Promblem with printing pdf files"
date: 2005-12-29
forum: Desktop Environments
---

### Post by foxy123 on 2005-12-29
I've got Epson Stylus Photo 790. I noticed that if I try to print a pdf file from kpdf or evince, nothing happens. However I can print them ok with arcoread. I wonder why?

---

### Post by Sef on 2006-01-04
I would say that acroread prints and the others don't because only acroread has the drivers for your printer.

From Dictionary.com:

> Computer Science. A piece of software that enables a computer to communicate with a peripheral device.

---

### Post by dcstar on 2006-01-05
[QUOTE=foxy123]I've got Epson Stylus Photo 790. I noticed that if I try to print a pdf file from kpdf or evince, nothing happens. However I can print them ok with arcoread. I wonder why?[/QUOTE]
Assuming your printer is installed, Evince should show it selected as the printer to use, does it?

---

### Post by foxy123 on 2006-01-05
[QUOTE=dcstar]Assuming your printer is installed, Evince should show it selected as the printer to use, does it?[/QUOTE]

yes, it definitely does. As I understand, a printer driiver is system wide, not programme specific, isn't it?

---

### Post by dcstar on 2006-01-06
[QUOTE=foxy123]yes, it definitely does. As I understand, a printer driiver is system wide, not programme specific, isn't it?[/QUOTE]
Yes, there is no real reason why it shouldn't work.

---

### Post by Gustav on 2006-01-06
I think that acroread uses the command lp to print.

I've experienced differences in how gnome apps and commandline printing works (mainly in if it uses the color cartridge or not to paint black).

---

### Post by foxy123 on 2006-01-06
[QUOTE=Gustav]I think that acroread uses the command lp to print.

I've experienced differences in how gnome apps and commandline printing works (mainly in if it uses the color cartridge or not to paint black).[/QUOTE]

as a matter of fact it does. So is there a way to print pdf with other then acroread programme?

---

### Post by Gustav on 2006-01-06
The lp command prints postscript files so you can do this in a terminal
```
pdf2ps <yourfile.pdf>
lp output.ps
```

---

### Post by foxy123 on 2006-01-06
[QUOTE=Gustav]The lp command prints postscript files so you can do this in a terminal
```
pdf2ps <yourfile.pdf>
lp output.ps
```[/QUOTE]

you mean that acroread converts pdf to postscript before printing?

---

### Post by Gustav on 2006-01-06
I think so

---

### Post by Bluebird on 2006-01-06
Hi!

I am not sure if this belongs here, since I have the exact _opposite_ problem... could be related, though. I have a few printers set up, all HP (2100M, 4L and 8120 I think). I can print pdf files from kpdf, but not from acroread (version 7.0). I tried lp, lpr, kprinter as print command for acroread, to no avail:

* Usually, there is no output at all.
* printer LED blinks for a while when using PS driver, nothing happens for hpjis or ljet4 drivers
* If I set the output to PS lvl3, I get a printout error that I should use PS lvl2 (as expected)
* If I activate pre-filtering to PS lvl1 or 2, it prints the first page of the document, and large, random parts of the page are missing
* Testpages come out great for all printers
* Problem is reproducible on another computer, running Breezy with Gnome (I have Breezy with KDE)
* Removal and reinstall of cups and foomatic did not help

The error logs show nothing helpful, even though I set the log level to "debug". In some cases I could find a problem when closing the renderer. I really someone can help me, this is really annoying, and I have spent quite some time with by best friend google already...

---

### Post by coaxx on 2006-01-18
[QUOTE=foxy123]I've got Epson Stylus Photo 790. I noticed that if I try to print a pdf file from kpdf or evince, nothing happens. However I can print them ok with arcoread. I wonder why?[/QUOTE]

Puhh exactly the same error here using Dapper Drake. I can not believe that it is just a bug :( I tried days long to solve this...

Well I am really wondering why this is, because I can print without Problems in other K Programs using the K typical printerdialog, just in KPDF it does not work. The print job reaches my printer and Cups says it is proceeding to print, but it never will start.

---

### Post by coaxx on 2006-01-18
can anyone move this to the Kubuntu forum?

---

### Post by el3ktro on 2006-01-30
I have the exact same problem, my Kyocera FS-1010 works fine EVERYWHERE, except Evince just won't print any PDFs. This really sucks because I need to print this stuff right now. Just discovered this today. Any solution yet?

Tom

---

### Post by iced-tux on 2006-03-08
I have exactly the same problem.
My log tells me this:
```
I [08/Mar/2006:09:29:56 +0100] Adding start banner page "none" to job 50.
I [08/Mar/2006:09:29:56 +0100] Adding end banner page "none" to job 50.
I [08/Mar/2006:09:29:56 +0100] Job 50 queued on 'LaserJet-Series-PCL-6' by 'chri
stian'.
I [08/Mar/2006:09:29:56 +0100] Started filter /usr/lib/cups/filter/pstops (PID 1
1407) for job 50.
I [08/Mar/2006:09:29:56 +0100] Started filter /usr/lib/cups/filter/pstoraster (P
ID 11408) for job 50.
I [08/Mar/2006:09:29:56 +0100] Started filter /usr/lib/cups/filter/rastertoprint
er (PID 11410) for job 50.
I [08/Mar/2006:09:29:56 +0100] Started backend /usr/lib/cups/backend/parallel (P
ID 11411) for job 50.
E [08/Mar/2006:09:29:56 +0100] [Job 50] No pages found!
E [08/Mar/2006:09:29:56 +0100] PID 11408 stopped with status 1!
I [08/Mar/2006:09:29:56 +0100] Hint: Try setting the LogLevel to "debug" to find
 out more.
E [08/Mar/2006:09:29:56 +0100] PID 11410 stopped with status 1!
I [08/Mar/2006:09:29:56 +0100] Hint: Try setting the LogLevel to "debug" to find
 out more.
```

When I do lp/lpr from any shell, its working like expected :(

---

### Post by bryanl on 2006-08-16
when printing from acrobat or lp, you probably need to open system->printers and set a default printer. Otherwise you'd need to name the printer with a command line option in the lp command string.

---

### Post by Ruth Lazkoz on 2006-12-05
> **bryanl said:**
> when printing from acrobat or lp, you probably need to open system->printers and set a default printer. Otherwise you'd need to name the printer with a command line option in the lp command string.

Indeed, I set a default printer and the problem got solved. Thanks for the hint

---

