---
title: "Ubuntu and my Lexmark X4650 wireless scanner, printer."
date: 2009-04-11
forum: General Help
---

### Post by urbeg on 2009-04-11
I was hoping someone could help me to get my printer working under Ubuntu.

I have been trying to figure out how to install my printer on Ubuntu for some time now, to no avail.

The printer is a Lexmark X4650. It is an all-in-one wireless printer, scanner.

I've been doing a bit of reading into this and noticed from this forum that Lexmark isn't the most Linux friendly hardware.

The only thing I have tried was this. System > Administration > Printing, then clicking on New. It does a search and then brings up a 'Select device' screen. I select 'Find network printer' and enter the host IP address but it comes back and says 'No printer was found at that address'.

Any suggestions would be greatly appreciated.

---

### Post by cmnorton on 2009-04-11
Given your Lexmark model number, you probably do indeed have a network printer. One of the ways I like to configure printers is through CUPS' native interface.

[http://locahost:631](http://locahost:631)

On Ubuntu distros, you need to add your user to the lpadmin group to be able to do this. 

Ubuntu's printer configuration is quite good as well; I just like the CUPS interface better.

Lexmark printers are able to be configured as -- socket://printer-address:9100.

You should also be able to reach them using an smb://string, especially if this printer is shared out on a Windows domain.

In CUPS interface they type is called AppSocket HP JetDirect. It might be called that in the Ubuntu interface as well, but that connection string should work. Lexmark tends to be proprietary, so you may have to use a generic driver.

---

### Post by urbeg on 2009-04-12
Thanks for the reply.

I tried what you suggested.

I went to [http://localhost:631](http://localhost:631) and added my printer using the following information.

Name: Lexmark-X4650
Location: Home
Description: Lexmark X4650 All-in-one
Device: AppSocket/HP JetDirect
Device URI: socket://192.168.0.102:9100
Make: Generic
Model: Generic PostScript Printer (en)

It then said it had been successfully added.

My Lexmark model was not listed under model so I chose generic.

Now when I tell it to print a test page or even any type of document it says 'Job 1 Completed on Lexmark-X4650" but the printer does not print any pages out.

I noticed that while setting up a printer in CUPS you could provide a .ppd file which I take to be some sort of driver.

I searched the disc that came with the printer for any sort off .ppd files but none were found.

Could you explain a little more on how to connect using the smb://string as I am not familiar with that.

---

### Post by sgbeamer on 2009-05-31
I followed urbeg's guidance and did this

> I went to [http://localhost:631](http://localhost:631) and added my printer using the following information.

Name: Lexmark-X4650
Location: Home
Description: Lexmark X4650 All-in-one
Device: AppSocket/HP JetDirect
Device URI: socket://192.168.0.102:9100

Then I tried each of the Lexmark drivers in CUPS starting with those model numbers nearest mine.  Several of the talked to the printer and the Lexmark 5000 Foomatic/lx5000 driver came closest to working.  The printer status screen said "Printing" and a piece of paper floated across it but when it finished, still nothing happened.  So it seems to be lack of driver.  The AppSocket/HP JetDirect device type and the :9100 port worked.

---

### Post by varney on 2009-08-12
Sorry to ask such a dumb question but I can't seem to find an answer anywhere. How do I print in grayscale with my Lexmark x4650? It's wirelessly connected to a Macbook. 

Any help gratefully received!

Mike..

---

### Post by jazzz337 on 2010-05-23
I just got the lexmark 4650 to print on my Ubuntu computer both wirlessly and usb I went to the Lexmark website Downloaded the Ubuntu driver opened it with ArchiveManager and then extracted it and ran it this allowed for USB printing 

forwireless Printing i used the Appsocket/hp injet and used the IP address as the host it worked great.

---

### Post by w2vy on 2010-12-25
Just installed X4650 with no problems, Thanks!

I actually already had the driver installed for my Wife's Z2420 WiFi printer.
I set it up and it was plug and play.

I did have to delete and re-add the printer to get a device name I liked.
It defaulted to the USB Description "3600-4600 Series"

But no big deal.

\\:D/

Much applause to Lexmark for their strong support of Linux!

Simple Scan works (USB) as does xsane (xsane seemed much faster)

tom

---

### Post by frogotronic on 2011-01-04
Hello,

  I've got this set-up, but the printing is VERY, VERY, VERY slow.

  Any suggestions?

- CH

---------------------------------------------------------

Rebooted & works perfectly now.

---

### Post by perpipon on 2011-02-11
driver not avalaible on french website. had to change location to USA to get it (thank you lexmark :s )

---

