---
title: "Photo Printer is Hung"
date: 2009-06-04
forum: Desktop Environments
---

### Post by pwaldo on 2009-06-04
Hi all,

I have two printers attached to my 64-bit system
[LIST]
[*]HP Laserjet 5L (parallel port)
[*]Epson Stylus Photo 1280 (USB)
[/LIST]
Under Intrepid, both printers worked well.  I upgraded to Jaunty and I'm having a tough time with the Epson.  The HP continues to work fine.

Print jobs to the Epson are just stuck processing.  I see no CPU activity, and nothing ever gets printed, even if I wait overnight.

I've looked in the Cups access_log and error_log and see nothing out of the ordinary.  I know that I am communicating with the printer, as the activity light on the printer blinks when I start a job.  Also, mtink works fine.

Any thoughts would be greatly appreciated!

---

### Post by pwaldo on 2009-06-07
Woo hoo!  I solved the problem by using the CUPS admin tool at [http://localhost:631](http://localhost:631).  I simply edited the printer and accepted all of the options that were already selected (port, manufacturer, type, etc.).  Now the printer works.  Maybe a bug in the printer detection code that tells CUPS about a new printer....?

---

