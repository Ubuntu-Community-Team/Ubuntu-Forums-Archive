---
title: "Dell Photo 924 printer all in one"
date: 2009-04-22
forum: General Help
---

### Post by candtalan on 2009-04-22
(8.04)
I am trying to convert a charity office to ubuntu, and the existing printer is a problem. I just need it to be a simple printer.
I see that an entry in openprinting.org
is very hopeful - it says it works!
[http://www.openprinting.org/show_printer.cgi?recnum=Dell-photo_924](http://www.openprinting.org/show_printer.cgi?recnum=Dell-photo_924)

I am not clear what I now have to do, but I have tried the normal admin>printing add new printer whatever and then tried the suggested driver, also tried to use a ppd file generated from
[http://www.openprinting.org/show_driver.cgi?driver=deskjet&fromprinter=Dell-photo_924](http://www.openprinting.org/show_driver.cgi?driver=deskjet&fromprinter=Dell-photo_924)

I am well out of my depth here but I also have tried to install a filter foomatic-rip without obvious success although I see that a link to it resides in my
/usr/lib/cups/filter
but maybe it was hter eby default anyway.(?)

Any comments about directions to success here would be great....  ?

tia

---

### Post by StuartN on 2009-04-22
> **candtalan said:**
> http://www.openprinting.org/show_printer.cgi?recnum=Dell-photo_924[/url]

That page says that the Dell is not supported, but that you could install the driver for an HP Deskjet (the very first entry for Hewlett Packard Deskjets, not any of the numbered models). You will not get all the Dell 924 features, like photo printing.

---

### Post by candtalan on 2009-04-22
> **StuartN said:**
> That page says that the Dell is not supported 

I do not understand. I read it saying:
'Dell photo 924
Color inkjet printer, works Perfectly 	
Recommended driver: deskjet (Home page)
Generic instructions for: CUPS, LPD, LPRng, PPR, PDQ, no spooler'
Where is it saying it is not supported?

> 
but that you could install the driver for an HP Deskjet (the very first entry for Hewlett Packard Deskjets, not any of the numbered models). You will not get all the Dell 924 features, like photo printing.

If I could do that sucessfuly I would be very pleased, but I have not been successful so far.
By 'driver' is the 'pdd' file meant?
tia

---

### Post by StuartN on 2009-04-22
What happens if you go to System->Administration->Printing, select New and manually install an HP Deskjet?

---

### Post by candtalan on 2009-04-22
MMM. What I hav ebeen doing so far is accpeting it is a new  printer, shown at printer search refresh as a dell924 whatever, -then- choosing hp deskjet. 

So I will try your suggestion - and declare a new hp deskjet.
Thanks!

---

### Post by candtalan on 2009-04-23
> **StuartN said:**
> What happens if you go to System->Administration->Printing, select New and manually install an HP Deskjet?

The new printer choice starts a search process and the usb connected dell 924 is shown. This is the only printer on usb, so I seem to have to choose this. 
I do not know if I can add a URI manually, but would it not indicate the same printer(?)

I go Forward and a search for drivers occurs. I select a printer from the database:
HP (deskjet)
and use one of the three possible drivers (I tried all three)
completing - I get no response at the printer from asking for a test page nor if I use open office to print something.

If the comment I saw saying it works is not mistaken, then maybe dell have changed their manufacturer?

fwiw lsusb response includes
Bus 002 Device 004: ID 413c:5112 Dell Computer Corp. 
which seems to be the usb printer I think.

any other thoughts please?

---

