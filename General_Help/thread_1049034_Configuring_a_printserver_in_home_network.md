---
title: "Configuring a printserver in home network"
date: 2009-01-24
forum: General Help
---

### Post by pimparello on 2009-01-24
Dear friends, 
I have a rather general question:

I want to enable to print from my laptop (ubuntu 8.10, in the net using wifi) on the printer connected via usb to my desktop-pc (Kubuntu 8.10, in the net over lan). They are connected over an hardware-router. How do I do this? The printer does not yet have an networking interface, therefore the desktop-pc should serve as print-server, or?

How do I configure this? 

Thanks in advance!

---

### Post by jimv on 2009-01-24
[http://www.kubuntu.org/doc/7.10/printing/C/print.html](http://www.kubuntu.org/doc/7.10/printing/C/print.html)

Sharing a Printer

[LIST=1]
[*]Select Printers from KMenu &#8594; System Settings.
[*]Highlight or select the printer that you want to share.
[*]Once highlighted go to Print Server &#8594; Share Printers on Local Network.
[*]At the Share Printers on Local Network dialog, press the Enable Sharing button.
[*]At the Run as root - KDE su dialog, enter your user password and press the OK button.
[/LIST]

---

### Post by pimparello on 2009-01-24
Thanks, but under KDE 4.1 the dialogues seem pretty different. I made it to the printer configuration, but I can't find the dialogue from your point 4.

---

### Post by pimparello on 2009-01-24
Thanks, I could solve it using [http://localhost:631](http://localhost:631)

---

