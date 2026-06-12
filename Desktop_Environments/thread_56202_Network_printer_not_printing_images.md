---
title: "Network printer not printing images"
date: 2005-08-11
forum: Desktop Environments
---

### Post by spin on 2005-08-11
Hi,

I've recently installed Ubuntu on my stationary computer, and everything seems to be working fine, except the network printer. The printer is connected directly to my network on a constand IP adress and is installed as a HP JetDirect printer (which was the only option in the GNOME Add Printer Dialog with which my printer would work) under Host: 192.168.x.x , Port: 9100. The driver is the Generic PostScript Printer one, and the printer's name is Ricoh Aficio CL3000DN.

Now, printing a test page or a plain text document goes just fine, but when I try to print images from the web or OOo documents, the printer just prints this small text on a blank page:

"""
ERROR: configurationerror
OFFENDING COMMAND: setpagedevice

STACK:

-dictionary-
"""

I've tried googling around a bit, but since I'm mostly a complede newbie to Linux printing, I didn't really know where to start.

Could someone help me out? Thanks,
spin

---

### Post by kassetra on 2005-08-11
[QUOTE=spin]ERROR: configurationerror
OFFENDING COMMAND: setpagedevice

STACK:

-dictionary-
[/QUOTE]

Your printer thinks you've requested something that it cannot do - it's saying that it's a "device mismatch" (which comes from configurationerror) ... because the setpagedevice calls in order to output graphics are unable to communicate with your printer (i.e. your printer speaks XYZ, and the printer calls as specificed by your driver are speaking ABC.)  

Have you attempted to use any of the Ricoh drivers?  It sounds very much like the driver you're using cannot speak graphics correctly to your printer.  (Have you tried using the Aficio AP2000 driver?  Have you tried any of the commercial drivers?)

---

### Post by spin on 2005-08-21
Hm. It seems I forgot to post a reply to this helpful comment. Thank you for your response! And please forgive my forgetfulness!

Anyway, I think I've solved the problem now. Really, the solution was quite simple: the programs that didn't print correctly all seem to default to the US letter paper size. Since I'm a European, my printer defaults to the A4 size (i don't even think it can handle the Letter size at all), and by changing this simple setting (and widening the margins to 0.5 inches, although I'm not sure if that affected the end outcome) in the programs and the print manager, I managed to print from both Openoffice and Mozilla.

---

