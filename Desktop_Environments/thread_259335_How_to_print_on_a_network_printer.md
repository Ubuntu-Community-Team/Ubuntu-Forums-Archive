---
title: "How to print on a network printer?"
date: 2006-09-17
forum: Desktop Environments
---

### Post by burzum on 2006-09-17
The printer is a Canon i850, according to some post i found in the ubuntuforums it should be possible to install it and print on it. 

But how can i print on this printer over the network? It's aviliable as a shared printer on a windows pc.

---

### Post by wieman01 on 2006-09-17
I have a network printer of my own which is connected to one of my computers. Is that what you're looking for? The solution is **CUPS**. You'll find tons of howtos in there and anywhere else. :-)

---

### Post by mgmiller on 2006-09-17
If the printer is connected to a windows machine and is being shared, then in the System > Administration > Printing applet, select a new printer and tell it network printer and select windows printer (SMB).  Then just follow through with the ip address and printer name and such.  You should know that you will need to have a printer driver on your local Ubuntu machine that works with the Canon printer first.  I don't think there is native support for the canon i850.  I have a canon i960 and ended up buying the turboprint for linux driver to get it to work.  You can get a free download to try it out first.   [http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")

---

