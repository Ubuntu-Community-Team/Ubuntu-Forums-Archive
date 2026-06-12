---
title: "Printer support?"
date: 2024-08-02
forum: Desktop Environments
---

### Post by lawrence-joy on 2024-08-02
Hello, I am moving this to Desktop Environments, hopefully to get a bit more visibility, as I have received only a little help when I posted to General Help. I have a new Epson ET-15000 all-in-one inkjet printer that I have direct connection via USB cable to my Ubuntu 22.04 OS on my desktop PC. I have downloaded CUPS a bunch of times but when I go to Settings > Printers the system states "Sorry! The system printing service doesn't seem to be available." Yes the printer is on. Would like some help in resolving this. Further I have downloaded "TurboPrint" from Germany for a 30 d free trial but when I try to run it the program comes back with "Can't connect to CUPS server". I am lost. Need help, thank you.

---

### Post by TheFu on 2024-08-02
Splitting into 2 threads for this issue seems like a mistake to me.  

If you are using TurboPrint from a commercial company, you should ask them for help. I bet they provide excellent support.

If you don't have CUPd running, did you try to enable it?  That is the obvious answer to the "can't connect to CUPS server" error.

If the Ubuntu Desktop Guide doesn't provide sufficient information, there's [https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint](https://www.linuxbabe.com/ubuntu/set-up-cups-print-server-ubuntu-bonjour-ipp-samba-airprint) for "server" instructions. It is a reputable instructions website.  I'd strongly suggest you stick with the Ubuntu Desktop Guide instructions, since those will have more GUI point-n-click steps, unlike the link I provided which is for servers (no GUI).

The printer you have selected isn't too popular, it seems, so few will have exact instructions and even fewer will be posting here.  I use an $80 laser printer from 2008 myself.  Connected via USB and it "just works". Drivers are handled automatically and it has an IPP:// URL for printing.  Also, my print server runs 20.04. None of my important systems runs 22.04. Sorry.   Setup for other systems to print through my cups server, were handled. I don't remember any difficulties, but that could just mean it just worked or it took nothing to fix based on the error shown to me. It has been a few years, so I don't remember.

**system-config-printer** is the program I use on a desktop.

But I really think you should be doing whatever TurboPrint suggests or what their support team says.

---

### Post by deadflowr on 2024-08-02
closed
no duplicates.
original thread here: [https://ubuntuforums.org/showthread.php?t=2499158](https://ubuntuforums.org/showthread.php?t=2499158)

---

