---
title: "Can't print to local HP printer"
date: 2009-05-10
forum: General Help
---

### Post by litlfrog on 2009-05-10
I'm tearing my hair out just trying to get the computer to print. After failing to connect to the network printer, I've connected that printer over to my computer. It installed fine and printed a test page--once. Now I can send jobs to the print queue or try printing a test page. I don't see any error messages; things just sit in the print queue saying that they're processing or pending. Printer is an HP Business Inkjet 2200. What can I do from here? It's not working, but I'm also not getting any messages saying where the failures are. Running Jaunty Jackalope on an old HP Pavilion 550n.

---

### Post by Tamlynmac on 2009-05-10
There is a new HP print driver (3.9.4b) available here:
[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

Hope it helps, as it solved all my printing and scanning issues in 9.04

---

### Post by litlfrog on 2009-05-12
Hmm, I installed the new printer, but the problem is exactly the same: the printer looks to be successfully installed and can print the test page, but I can't print a document to it. It just sits in the print queue. At this point I think I'm going to ask my boss to come by; he's an old hand at UNIX/Linux systems.

---

### Post by TheExplorer on 2009-05-12
I solved it the following way: 
 
1) installed the driver (Samsung printer) 
2) [http://localhost:631/ ]("http://localhost:631/")
3) Added this printer, chose VIA SAMBA, added its address like this:
socket://hostname:9100

Where is **hostname** is the IP of the printer.

---

