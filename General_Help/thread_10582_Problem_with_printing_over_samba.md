---
title: "Problem with printing over samba"
date: 2005-01-09
forum: General Help
---

### Post by anund on 2005-01-09
Setup: Ubuntu 4.10. No local printer. HP PSC1310 connected to WinXP box in LAN. LAN and samba is working, I can use smbclient -L xpbox to see that the printer is available as a share.

I use the gnome-cups-manager to set up the remote printer. Everything seems fine. Of course using a working username and password on the xp box.

The problem is that when I try to send a test page to the printer (or write to the printer through another program), a print job is added on the xp box, but no printing is started. The printer makes some noise, and the online light starts blinking. But no actual printing. It also screws up the whole print queue on the xp box, forcing me to restart it in safe mode and kill the queue to make printing available again.

Any idea? I've got everything else to work with Ubuntu now, but I'd really like to have printing available... Moving the printer to local setup is not possible, unfortunately.

Regards,
Anund Rannestad

---

### Post by anund on 2005-01-10
Sort of solved, that is it's unsolvable ;)

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?&cc=us&docname=bpu04830#](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?&cc=us&docname=bpu04830#)

This means it just will not work to use this printer over a samba network. It will only work from other XP boxes in the Windows Network.

anund

---

### Post by hardcandy on 2005-01-10
Is this a usb printer? Is it possible to use a usb kvm switch with a printer? You know, the ones with the usb hookups for the mice and keyboard?

---

### Post by anund on 2005-01-10
Yes, the HP PSC 1315 is a (multifunction) usb printer. As far as I know, there should be no problem connecting it to a usb kvm. I haven't tried it myself, so I can't guarantee it, but I see no reason why it should not work.

Unfortunataly, I can't use that solution myself, as the printer is in the other end of the house, compared to my Ubuntu workstation ;)

anund

---

### Post by hardcandy on 2005-01-11
Any chance of a wireless usb print server working? One of those $60 on sale jobbies from linksys or dlink?

---

### Post by anund on 2005-01-13
Nope, an USB print server won't work. The problem is that this is a low-cost printer that doesn't support any kind of network printing, except between similar Windows OS's.

Too bad :( But a good excuse to buy myself a laser printer, too :)

anund

---

### Post by JackDog on 2005-01-13
For small to medium sized networks, a print server is the way to go. Just make sure you get one that is bi-directional so that your clients can get messages back about jams or paper reloads.

---

### Post by SickTwist on 2005-05-15
[QUOTE=anund]Setup: Ubuntu 4.10. No local printer. HP PSC1310 connected to WinXP box in LAN. LAN and samba is working, I can use smbclient -L xpbox to see that the printer is available as a share.

I use the gnome-cups-manager to set up the remote printer. Everything seems fine. Of course using a working username and password on the xp box.

The problem is that when I try to send a test page to the printer (or write to the printer through another program), a print job is added on the xp box, but no printing is started. The printer makes some noise, and the online light starts blinking. But no actual printing. It also screws up the whole print queue on the xp box, forcing me to restart it in safe mode and kill the queue to make printing available again.

Any idea? I've got everything else to work with Ubuntu now, but I'd really like to have printing available... Moving the printer to local setup is not possible, unfortunately.

Regards,
Anund Rannestad[/QUOTE]

I had a similiar problem trying to print from Ubuntu Hoary over a network to a Windows 2000 box sharing an HP PSC 1315.  It caused me a lot of fustration but I finally discovered how to fix it.  I assume this solution works for Windows XP as well but I'm not sure about 95/98/ME.

On the Windows box:
[list]
[*]Start->Settings->Printers
[*]right click on the shared printer
[*]click properties
[*]click on the Ports tab
[*]uncheck the box next to "enable bidirectional support"
[/list]

Hopefully that will clear up any issues.

---

### Post by jjross on 2005-06-03
[QUOTE=SickTwist]I had a similiar problem trying to print from Ubuntu Hoary over a network to a Windows 2000 box sharing an HP PSC 1315.  It caused me a lot of fustration but I finally discovered how to fix it.  I assume this solution works for Windows XP as well but I'm not sure about 95/98/ME.

On the Windows box:
[list]
[*]Start->Settings->Printers
[*]right click on the shared printer
[*]click properties
[*]click on the Ports tab
[*]uncheck the box next to "enable bidirectional support"
[/list]

Hopefully that will clear up any issues.[/QUOTE]

THANKS this worked for me, I have been trying for a week to figure this out and all I needed to do was disable bidirectional support on the win. 98 machine to enable me to print on the hp psc 950 that is hooked to it. it turns out the problem was not on my ubuntu machine ,but on the windows machine .
Thanks Again

---

### Post by annex on 2005-09-21
[QUOTE=SickTwist]I had a similiar problem trying to print from Ubuntu Hoary over a network to a Windows 2000 box sharing an HP PSC 1315.  It caused me a lot of fustration but I finally discovered how to fix it.  I assume this solution works for Windows XP as well but I'm not sure about 95/98/ME.

On the Windows box:
[list]
[*]Start->Settings->Printers
[*]right click on the shared printer
[*]click properties
[*]click on the Ports tab
[*]uncheck the box next to "enable bidirectional support"
[/list]

Hopefully that will clear up any issues.[/QUOTE]

Fantastic!  That worked beautifully for Ubuntu.  I have a Windows XP Home PC with a HP PSC 1310 / 1315 printer installed.

Thanks!

---

### Post by SimpleSi on 2005-09-23
[QUOTE] I had a similiar problem trying to print from Ubuntu Hoary over a network to a Windows 2000 box sharing an HP PSC 1315. It caused me a lot of fustration but I finally discovered how to fix it. I assume this solution works for Windows XP as well but I'm not sure about 95/98/ME.

On the Windows box:

    * Start->Settings->Printers
    * right click on the shared printer
    * click properties
    * click on the Ports tab
    * uncheck the box next to "enable bidirectional support"
[UNQUOTE]

I have a PSC1110 on a Win98SE machine and this also did the trick for me- thanks.

regards
Simon

---

### Post by sapperlite on 2006-02-24
SickTwist You are brilliant!!! I had the same printer with the same problem and now it works like a charm.
Thank You very much!!!

---

### Post by dannystaple on 2008-03-15
Just so people know that in the world of 2008 and Gutsy with Vista, this fix still works! I spent ages trying to get this to work, and finding this fix was very handy.

HP have unhelpfully removed their original article however. That fix needs to be in an FAQ for Ubuntu Linux, Samba and the PC1317 (or 1310 series) multifunction printer.

---

### Post by dannystaple on 2008-03-21
Hmm - however, if I am not mistaken - that has appeared to disable the scan button in Windows. Has anyone else had the same problem with this fix?

(EDIT: SOLVED - It was just the HP software being a pain)

---

