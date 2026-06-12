---
title: "Printer problems"
date: 2006-08-22
forum: Desktop Environments
---

### Post by someguyouknow on 2006-08-22
I have a HP printer that i had setup perfectly.  Its one of those print/scan/copy ones.  i have been able to scan previously but now i cannot.  I tried Kooka and XSANE Image Scanner.  Kooka doesnt respond when trying to scan and XSANE says i dont have a device to scan with.

---

### Post by ahaslam on 2006-08-22
Have you tried it under kde?
Kde has many more utils & options for printers.

Tony.

---

### Post by Mahyar on 2006-08-22
Some guy I know,

I am a complete novice at this Linux stuff, but I've spent hours on this and have worked it out.

I have a HP PSC 1315 and I couldn't find the drivers/software whatever anywhere.  Then I tried it in Picasa and it worked a miracle.

I set the printer up first as normal in System>Administration>Printing, but as you know, the scanner doesn't work there.  But after you've set it up there, turn the PSC on and Picasa will recognise it under Import>Select Device in the top left.  The printer has to be on first though.  Otherwise you'll cause a fatal error.

I've found it also works on my Canon Selphy photo printer, which I thought I was going to have to ditch.  It actually prints better than the Canon software, i find.

Good luck!

Mahyar

---

### Post by someguyouknow on 2006-08-22
Thanks for the advice but sadly it didnt work.
I am using Kubuntu so i do have a lot of options.
and Picasa didnt work.
It only sees a camera even though there isnt one connected.

---

### Post by someguyouknow on 2006-08-22
any advice or should i just give up for now?

---

### Post by llamakc on 2006-08-22
In a terminal what is the output of

hp-makeuri  -b<bus> or --bus=<bus>  
                                                     <bus>: cups*, usb*, net,
                                                    bt, fw, par*

With something like 

hp-makeuri --bus=usb*

if it's a usb printer. Mine is a network printer and looks like this:

```

ken@nola:~$ sudo hp-makeuri 192.168.0.102
 
 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5
 
 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.
 
 Creating URIs for '192.168.0.102':
CUPS URI: hp:/net/Officejet_7200_series?ip=192.168.0.102
SANE URI: hpaio:/net/Officejet_7200_series?ip=192.168.0.102
 

```

After I set this up, I didn't see the scanner functions until a reboot, even though I had restarted hplip and cupsys from /etc/init.d/

---

### Post by someguyouknow on 2006-08-22
not sure what i am suppose to be entering.....
i tried the usb one and it gives me an options list.....
its not a network printer so i dont have an ip for it.....
i am a noob so i dont quite know what i am doing.....

---

### Post by llamakc on 2006-08-22
What device node is your printer connected on? Is the package hplip installed?

---

### Post by someguyouknow on 2006-08-23
hplip is installed.  

the odd thing is that it was working at one point but now doesnt.  Not sure why though.

---

