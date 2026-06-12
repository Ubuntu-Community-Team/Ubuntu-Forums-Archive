---
title: "I Can't Print!!!"
date: 2008-12-10
forum: General Help
---

### Post by DizzyEwok on 2008-12-10
Hi,
I have been using ubuntu for about 10 months now and have had no problems whatsoever apart from that I have never been able to print!
So far I have coped by transferring the files by e-mail and printing them on one of the computer's that is connected to my printer.
It has now come to the stage where I have a file which is "ubuntu-only" and I cannot print it!!!
Any ideas on how I can connect to my printer?
I have a hp-deskjet and it is connected to 2 windows computers on the network. They can both print via the network but I cannot.
About 6 months ago I tried to connect and it seemed to work but when it came to printing it simply said "Processing" and never printed.
I have tried many times since then to no avail...

---

### Post by cariboo on 2008-12-10
If you have your printer setup for sharing and the computers are all in the same workgroup, the printer should show up automagically during printer setup.

Go to System-->Administration-->Printing and click New, the result should be the similar to the printer1.png screenshot, click forward and you should see something like screenshot.png, click Apply and you should see something like screesnot-1.png.

Jim

---

### Post by Peter09 on 2008-12-10
Try using the CUPS interface.

using your browser go to 
[http://localhost:631](http://localhost:631)

Try configuring the printer from there.

---

