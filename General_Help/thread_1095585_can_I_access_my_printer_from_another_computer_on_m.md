---
title: "can I access my printer from another computer on my home network?"
date: 2009-03-13
forum: General Help
---

### Post by jon.reeve on 2009-03-13
I share an internet connection with my three roommates, and I had an idea recently to try to make my new printer available to everyone in the house. It's not a networked printer, just a USB printer, but I'm hoping there's a way to put the printer and an ubuntu laptop in the living room and somehow make this available to everyone else (i.e. three windows machines and two ubuntu boxes) through the network. Does anyone know how I might go about doing such a thing?

---

### Post by masterkoppa on 2009-03-13
Depending on the machine connected to the printer is the approach that you'll need to take. If its windows then just select share printer, in the printers section, inside control panel. If its an Ubuntu Box you'll need to set up samba to share the printer with the other networks.

I haven't really tried this but I think that if you have a fully working Samba setup you should be able to share installed printers automatically.

---

### Post by HermanAB on 2009-03-13
You need to install CUPS to share a printer with the rest of the network.  If you install Samba as well, then it will be easier for Windows users, but it is not essential.  

You need to run the system-config-printer wizard to install CUPS.  Maybe have a look at this: [http://aeronetworks.ca/print-howto.html](http://aeronetworks.ca/print-howto.html)

Cheers,

Herman

---

