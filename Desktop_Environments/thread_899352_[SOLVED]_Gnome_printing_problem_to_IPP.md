---
title: "[SOLVED] Gnome printing problem to IPP"
date: 2008-08-24
forum: Desktop Environments
---

### Post by CameO73 on 2008-08-24
I have a weird printing problem for a number of Gnome applications.

My setup is as follows: I have a desktop PC with the latest 8.04.1 (x86). Another PC runs on Ubuntu Server 8.04 (updated to latest packages). This server has a DeskJet 5550 attached and shares the printer using CUPS.

Things that work (on the desktop PC):

[LIST]
[*]Printing a test page from Printer configuration to the Remote Printer (ipp://ZEV:631/printers/deskjet_5550)
[*]Printing from OpenOffice Word to the remote printer
[*]Printing from Wine to the remote printer
[/LIST]
Things that fail (on the desktop PC):

[LIST]
[*]Printing from Firefox 3
[*]Printing from Evolution
[*]Printing from Evince
[*]Printing from Gedit
[/LIST]
So I'm guessing it's some kind of (Gnome) printing framework problem? Any ideas, since the workarounds drive me crazy (opening a PDF in Foxit Reader for Windows using Wine to print ...)?

Btw, what happens in case of failure is sometimes a notification ("Is this printer connected?"), but the jobs just wait in the queue (until I manually cancel them). I don't think the server recieves those jobs, but I'm not sure.

---

### Post by CameO73 on 2008-08-24
I've solved my problem! Just had to take the time to really dive into this one.

I noticed in the Printer Configuration that it said "Remote Printer" next to Make and Model. I used the Change button to change this into the exact make and model I used on my server (HP - Deskjet 5550 Gutenberg). After that every Gnome program (Evince, Evolution etc.) that previously failed, started working again!

---

### Post by hmich176 on 2008-11-17
Newbie here.  How do you change the printer configuration?

---

