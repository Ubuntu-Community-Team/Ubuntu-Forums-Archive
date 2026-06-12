---
title: "printing thru a print server"
date: 2005-08-09
forum: Desktop Environments
---

### Post by chazworth on 2005-08-09
Hi ya'll
I recently installed Kubuntu and love most everything about it. My only problem is that I have an old 3COM 4port router with a built in print server that I use with my three computers (windows98,Mandrake10.1,Kubuntu), and both the other computers will print with out problems but the Kubuntu system will not. I have tried almost every combination in Cups. I should be able to select TCP/IP and input my routers IP address and port number for the printer , select my print driver (HP Deskjet 895C), and print. Nothing happens. Its like the computer is waiting for a ready signal from the printer, but can't get it because of the print server not being able to pass the signal. If this is a correct assumption, is there a way to tell Cups to not look for that two way communication? Thanks.

---

### Post by rosslaird on 2005-08-09
Look for the various threads on the forum about the cups "browse" settings.
Look in /etc/cups/cupsd-browsing.conf and make sure browsing is turned on.
Make sure the settings for browsing and receiving across the network are set up properly in /etc/cups/cupsd.conf

Cups is arcane and messy and very difficult to figure out, in my experience.

Ross

---

### Post by chazworth on 2005-08-12
After reading many more of the threads, I found the answer. In cups, added printer, selected lpd printer, input the print server address and port number, and put "lp" as the queue name. That did the trick. I had forgotten about  using 'lp' as the queue name. Thanks.
Charles

---

