---
title: "Issues adding network printers in Ubuntu"
date: 2009-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mysticdragon on 2009-11-16
Hello;

I am currently taking a course in Linux in school, but we have not gotten very far in our course, so I opted to do some research and experimenting on my own.  All the work we do with Linux is done using the VMWare Workstation (as the school is using Windows Vista, and soon Windows 7 as the main school image).

While the GUI makes it possible to add printers, etc., I prefer the idea of doing things through the command line.  Anyone can add things with a good GUI, but the real talent (and sense of achievement) comes from being able to do things via command line.

I managed to add one network printer via the GUI, and after some research managed to add a second one via command-line.  The second printer was a Dell Laser printer (5000 series I believe).  To test my coding, I opened a document in Open Office and attempted to print it from the Dell printer.  Unfortunately, when it printed, I ended up getting machine code instead of the document I had typed in Open Office.

My question is this:  Is this a common problem?  If so, what work arounds are there?  Could it have been something I did when I wrote the command line, or is it related to an Open Office issue?

Any input would be appreciated.:)

---

### Post by teward on 2009-11-17
I can't add any network printers in Ubuntu, partly because the network I use doesn't support Linux computers printing via the network.  Perhaps your network doesn't support printing through Ubuntu.

---

### Post by efflandt on 2009-11-17
It does not really make any sense that a network would not support Linux printing, since any network print server I have ever seen supports lpr/lpd (port 515) type printing (which cups can do), and usually raw JetDirect type printing on port 9100, and probably even ipp (cups) type printing on port 631.

And if it is a Windows shared printer not directly on the network, that can be done too, unless it is a brain dead Windows only raster printer that probably would not work over a network from another Windows box.  So all that matters is whether Linux has a driver to convert the output to a language the printer understands.

[http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html)

Many years ago, I used to manually configure /etc/printcap for lpr/lpd network printing.  Basically you had to run the input through a filter or converter to convert whatever input you had to the printer language.  Many printers from major manufacturers are backwards compatible so I used hplj3 before hplj4l was available specifically for my printer.  In fact DOS WordPerfect was able to print to our HP LJ 2200dtn at work using its HP LJ3 driver.  Or an old WinNT box was able to lpr print to our OfficeJet 85xi using an old DeskJet driver.

But I have not really dug into configuring cups from the command line.  Even before I got the ppd file from Lexmark for my C543dn, that printer worked with the C534dn driver that came with Ubuntu.  But it either understands common postscript or common HP PCL.

---

### Post by jamesrico on 2009-11-18
Hello, I have a Dell 1600N network printer. I finally got it to work using a different Dell model in the Ubuntu set up screen. How can I set up the printer correctly? I have a network printer card test page from the printer. From what I gather it is an IPP printer. The port number says it is 631. The PDL is postscript. I can live with it just working but would like to know how to set it up correctly.

thanks
James Rico

---

