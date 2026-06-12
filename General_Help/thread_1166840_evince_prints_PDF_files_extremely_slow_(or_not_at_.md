---
title: "evince prints PDF files extremely slow (or not at all)"
date: 2009-05-22
forum: General Help
---

### Post by cleric23 on 2009-05-22
Hey everybody,

I am having some problems with evince. I used evince for some years now, and it always worked fine. However, since the last ubuntu upgrade, it is VERY slow printing PDF files.

If I print a PDF file, I see a progress bar, which fills very slowly. After that, I see the item in the printer queue for some minutes. Then the printer starts to print some pages very slowly (waiting for 10 seconds after each page, sometimes just printing the first few pages).

I can use xpdf (which uses lpr) to print the file in normal speed and without problems. Also, other printing stuff works fine.

Some specs:
* Ubuntu 9.04 (64 bit)
* Kernel 2.6.28-11-generic x86_64
* evince version 2.26.0-0ubuntu1
* cups version 1.3.9-17ubuntu1
* Printer Brother HL-5250DN (using LAN)

Any hints?

Thanks!
Flo

---

### Post by cleric23 on 2009-05-22
By the way, the file I am trying to print is only about 20 pages (~300 KB) and this also happens with other files.

I just tried epdfview instead of evince, which is a bit faster (but can not do duplex), but not as fast as evince used to be :-(

---

### Post by Astenorh on 2009-05-22
Is the actual printing slow, or the process of the sending it to the printer?

---

### Post by ukripper on 2009-05-22
Have you tried Adobe reader?

---

### Post by cleric23 on 2009-05-22
> **Astenorh said:**
> Is the actual printing slow, or the process of the sending it to the printer?

Well, I think both. Before the upgrade, the data was sent to the printer immediatelly and the printer started printing it immediatelly. Now, the sending takes long (I never saw a progress bar before!) and the printing is slow too. I looks like the printer receives one or two pages, prints them.. Then waits for new pages.. Prints them.. waits.. etc. There was no waiting before (the printer has enough RAM and its a laser printer)

---

### Post by cleric23 on 2009-05-24
nobody? :-(

---

### Post by tomas.splatch on 2009-05-24
I have the exactly same problem. Printing 20 pages takes roughly 20 minutes to send to the printer, then prints alright.

---

### Post by pmorton on 2009-05-29
> **tomas.splatch said:**
> I have the exactly same problem. Printing 20 pages takes roughly 20 minutes to send to the printer, then prints alright.

So have I. Plain text pdf pages each takes about a minute of processing before printing out on a Dell 3110cn colour laser printer.

Personally I'd rather not use closed source Acrobat, particularly as pdf-shuffler does all the simple pdf manipulation I need.

I don't know if the problem has already been reported on launchpad. If not, I'll do so.

---

### Post by emaxx on 2009-06-02
Same here. Unacceptable delays when printing (not using evince). Depending on illustration-grade four pages of a pdf-file take 10 Minutes and even longer to print. Never had this problem before.

Kubuntu 9.04
Printer: Dell 3115cn (laserprinter, postcript)
CUPS 1.3.9
gs 8.84
acroread 9.1.0 02/27/2009

Problem doesn't seem to be related to evince.

---

### Post by Wilburight on 2009-06-03
I don't use my printer very often, but cleric23's description fits my observations precisely. Printing was much quicker in previous Ubuntu releases and, dare I admit it, the printer lights up almost immediately when I'm forced to run XP. For a while I thought the printer wasn't working at all and I was pulling plugs and my hair way before it actually started the task.

---

### Post by tomas.splatch on 2009-06-03
For me PDF reader from Adobe works perfectly well.

---

### Post by mdswendsen on 2009-06-05
When I first installed Jackalope, printing was OK, then it gradually slowed on all apps until it now takes literally an hour to print a picture to a Brother MFC-8840D laser. 

Does anybody have a fix?

---

### Post by marmuta on 2009-06-06
There was a posting about regressions for CUPS and postscript printing on the mailing list recently.
[https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028291.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028291.html)
 
Also check out bug [LPbug]289852[/LPbug], particularly Till Kamppeters workaround script(s) to return to printing with libpoppler. It looks like he could use more people help testing it.

> Please replace your file /usr/lib/cups/filter/pdftops by the attached one and make sure that the new file is executable ("sudo chmod 755 /usr/lib/cups/filter/pdftops"). Then try to print the job again. Is it faster now?

If there are any problems, you can return to the previous state by

sudo apt-get install --reinstall cups

---

### Post by mdswendsen on 2009-06-06
This seems to be true of any heavy graphical file, such as GIMP. At first, printing with Jaunty was quick; now it's slowed down to glacial speed. The fix in [https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028291.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028291.html) seems to be on the money.

---

### Post by FMaz008 on 2009-09-24
The linked report have been published the Jun 4.
Can we expect an official fix by the regular update soon ?

Because I'm experiencing the very same problem right now with an updated version of Ubuntu and a Brother HL-2070.

I'm trying to print a 16mb 13 pages PDF, and it took 28 minutes to print the first page.

---

### Post by roberthr on 2009-10-29
PDF printing is useless.
I had to print some 2 page PDF reports during a meeting. It took 15 minutes and meeting ended before first page came out!!! It was so embarrassing in front of people that seemed interested on what they've seen in Ubuntu.

Come on Linux people. Can't this be fixed after so many years???

---

### Post by jcpeart on 2009-11-02
I also have had this problem.  I switched to using Okular as my default PDF viewer/printer and do not have those problems with it.  Evince was taking 30 to 40 minutes to print my 4 page bank statement after upgrading to Karmic.

---

### Post by bayvista on 2009-12-22
I've switched to 'xpdf' and it works fine. It prints using LPR. I think there is a bug in CUPS and believe it has been logged.

---

### Post by Chough39 on 2011-03-17
I have had a problem printing pdf files through “Evince”, pdf files will not print in colour, only black.  System running Ubuntu 10.10, Kernel Linux 2.6.35-27-generic.
 

 Use Adobe Reader 9 which is available from Synaptic Package Manager or Ubuntu Software Centre this works well.

---

