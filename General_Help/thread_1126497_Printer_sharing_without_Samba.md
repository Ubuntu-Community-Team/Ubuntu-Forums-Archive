---
title: "Printer sharing without Samba?"
date: 2009-04-15
forum: General Help
---

### Post by paradigm2 on 2009-04-15
I have two Ubuntu 9.04 beta machines on the same network.  I would like to hook up my HP Deskjet 1420 so that my other computer can also print to it.

I would like to avoid using Samba if at all possible because I have no need whatsoever for windows connectivity and in fact I am probably more secure without that (my wireless router is shared in the complex).  I currently use sshfs to share my files between my two Ubuntu computers.

What other options besides Samba are there for network printing on my basic Deskjet 1420 printer?  The printer is already detected on the local Ubuntu machine and works perfectly.

Thank you.

---

### Post by craig100 on 2009-05-09
I have exactly the same problem and can't find any simple, straight forward answers.  I have one machine with Ubuntu 9.04 on it which has an HP Photosmart C5200 connected and shared. My laptop is on the wired network and also has Ubuntu 9.04 on it but I can't it to find or connect to the printer. The two machines can see eacho thers file shares so there's definitely a connection. Why is this so hard, it's only printing for Gods sake?!  If the printer is on one machine and is SHARED why can't the other machine see it?  What hoops do I need to jump through?  Any advice will be appreciated.  Have been Googling for over an hour so this is last resort.

Thanks

---

### Post by HermanAB on 2009-05-09
Howdy,

You don't need Samba to share a printer.  CUPS works on its own.  CUPS doesn't need Samba - Samba needs CUPS.  So if you don't need Samba, don't install it.

See this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

---

### Post by paradigm2 on 2009-05-09
> **HermanAB said:**
> Howdy,

You don't need Samba to share a printer.  CUPS works on its own.  CUPS doesn't need Samba - Samba needs CUPS.  So if you don't need Samba, don't install it.

See this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Nice, I thank you as well. :)

---

### Post by Chuq on 2009-11-01
> **HermanAB said:**
> Howdy,

You don't need Samba to share a printer.  CUPS works on its own.  CUPS doesn't need Samba - Samba needs CUPS.  So if you don't need Samba, don't install it.

See this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

I'm having a similar problem with two 9.10 machines.  That page, while useful, doesn't help with the issue of installing it as a network printer and being accessible in the GUI.

I've done the following things:

Under 'Server' -> 'Settings', ticked 'Published shared printers connected to this system' and 'Allow printing from the internet'

On the client machine I have installed the drivers for the printer the same as I did originally on the server; it points to a local queue which of course won't work.

My question:
Should I select IPP or LPR?
What should I enter the queue as?
  Properties dialog box shows the URI as: usb://Brother/DCP-330C
  CUPS web interface shows queue as just DCP330C
  Default queue on client shows the prefix '/printers', do I need to prepend the queue with this?

I even did a search and it came up with the sole Windows machine on the network, and the NAS, but none of the Ubuntu machines!

I think I've tried most combinations but I can't find a definite HOWTO on google or ubuntuforums.  

Any advice appreciated!

- Charles

---

