---
title: "Help with Printer"
date: 2009-03-27
forum: General Help
---

### Post by luke0927 on 2009-03-27
Hello, running ubuntu 8.10 and need to hook up my printer its just a cannon inkjet...i go to the printing under accessories and run the wizzard for new but it does not pop up a printer and it gives all the option that it could be connected but i do not see USB any idea on what to do? It is connected via USB and is powered on etc...

---

### Post by HermanAB on 2009-03-27
The printing wizard is shared by most Linux distributions.  It was a joint effort between Redhat and Mandriva Linux and is called system-config-printer:
[http://fedoraproject.org/wiki/Printing/AdminToolOutline](http://fedoraproject.org/wiki/Printing/AdminToolOutline)

Here is some more printing fun:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by luke0927 on 2009-03-27
> **HermanAB said:**
> The printing wizard is shared by most Linux distributions.  It was a joint effort between Redhat and Mandriva Linux and is called system-config-printer:
[http://fedoraproject.org/wiki/Printing/AdminToolOutline](http://fedoraproject.org/wiki/Printing/AdminToolOutline)

Here is some more printing fun:
[http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Thanks i power cycled the printer and got the wizzard to pick it up but it only sees a default driver and my printer is not list one model up is and the driver doesnt seem to work with it...guess I'll have to keep playing with it.

---

### Post by coffeecat on 2009-03-27
What model is it? Canon are notoriously bad for not providing Linux drivers. Which is odd, because Apple users seem to like Canon, and MacOS uses the same CUPS system as Linux. In fact Apple owns CUPS now.

Have a look here for your printer:

[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

It might tell you more, whether you can use it under Linux, what driver (if any) you need to use, and so on.

---

### Post by luke0927 on 2009-03-27
> **coffeecat said:**
> What model is it? Canon are notoriously bad for not providing Linux drivers. Which is odd, because Apple users seem to like Canon, and MacOS uses the same CUPS system as Linux. In fact Apple owns CUPS now.

Have a look here for your printer:

[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)

It might tell you more, whether you can use it under Linux, what driver (if any) you need to use, and so on.

Cannon Pixma MP130...the mp150 is in there but it will never print a test page.

---

### Post by coffeecat on 2009-03-27
> **luke0927 said:**
> Cannon Pixma MP130...the mp150 is in there

Well - [the MP130 is in there as well]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP130"). :wink: And you're in luck. It's one of the Canon models that does work with Linux.

I'm not clear exactly what you've done to try to get it to work, so try this. Open firefox and type localhost:631 in the address bar and you'll get the CUPS configuration utility. Delete whatever you've tried to set up before (if any printers show under the 'Printers' tab). Make sure the printer is switched on and plugged into a USB port and try to reinstall under Home > Add Printer. At some point you'll be prompted for your name and password. You can try a test page somewhere from in that utility.

---

### Post by luke0927 on 2009-03-31
> **coffeecat said:**
> Well - [the MP130 is in there as well]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP130"). :wink: And you're in luck. It's one of the Canon models that does work with Linux.

I'm not clear exactly what you've done to try to get it to work, so try this. Open firefox and type localhost:631 in the address bar and you'll get the CUPS configuration utility. Delete whatever you've tried to set up before (if any printers show under the 'Printers' tab). Make sure the printer is switched on and plugged into a USB port and try to reinstall under Home > Add Printer. At some point you'll be prompted for your name and password. You can try a test page somewhere from in that utility.

Thank you for your help i will try this out!

---

### Post by 3Miro on 2009-03-31
I had to jump some hoops to get my printer working. Officially Cannon provided Linux drivers, bout only .rpm format. Some people on this forum had repackaged the driver to run on Ubuntu (i.e. .deb) However, when I tried to move to 64-bit, even that did not help. I couldn't find a driver to use for my printer under 64-bit. However, there is still a way (somewhat ugly, but it works well enough).

I have set up a Virtual Box Ubuntu 32-bit that is actually connected to my printer. I can print from within Virtual Box (you have to download the version form [http://www.virtualbox.org/](http://www.virtualbox.org/)). The the obvious way is: every time you want to print, just start VB and move your files there. That is bad, what I did was, I shared the printer overt the network. Now when I need to print from either my desktop or my laptop, I simply select print and as long as I have VB running minimized, it prints. I have enough memory so I don't mind if VB runs most of the time, when I need to do something serious, I just shut it off for a while.

I suppose you can do the same with windows. I can give you some advice, however, I have never shared printers between Linux/Windows so my help might be insufficient.

---

