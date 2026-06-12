---
title: "Printing"
date: 2005-11-06
forum: Desktop Environments
---

### Post by 4plus2 on 2005-11-06
Hello,
Im very new to Linux (was having fun until now) and as a challenge I thought I would try and print from my Ubuntu Breezy GNOME laptop to my HP PSC 1210 USB printer attached to my WinXp Home desktop but its not easy!
I can ping the desktop from the laptop and have setup a Windows SMB printer using the IP of the desktop as the Host and the WinXP printer share name as the printer name. The username and password I assumed was for the desktop. But this spools the job to XP but nothing ever prints. I have to turn the printer off and remove the spool entry.
Ive tried various things since. Like installing HPlip (includes HPijs), Samba and the PPD driver file. Ive even tried removing Foomatic and installing the Linux printing service onto WinXP but unless Ive done something in doing so these methods did not work.
Does anyone have a proven method of getting this printing to work??

Thanks.

---

### Post by 4plus2 on 2005-11-06
Im using HPijs and Samba (which seems to work as I can see the XP shares) but I dont think the "Add Printer" dialog is building the correct DeviceURI in /etc/cups/printers.conf ie. smb://Guest:Printer@DESKTOP/Printer
What should the string be if I want to use XP login username "Guest" within the workgroup "WORKGROUP" with no password on a host Ive called DESKTOP (or should I use its IP) with an XP printer share name of "Printer"?
At present I can see the job being added to the Linux print queue then it appears in the XP print queue as "Remote downlevel document" but never prints. Documents print okay if I attach the printer directly to the Linux USB.

---

### Post by SickTwist on 2005-11-06
I had a similiar problem printing to an HP PSC 1310 on a Windows 2000 box from Ubuntu. This was my solution: Open up the printer settings on the Windows box, click on the "Ports" tab and turn off (uncheck) "Enable Bidirectional Support".

---

### Post by SickTwist on 2005-11-07
[QUOTE=4plus2]Im using HPijs and Samba (which seems to work as I can see the XP shares) but I dont think the "Add Printer" dialog is building the correct DeviceURI in /etc/cups/printers.conf ie. smb://Guest:Printer@DESKTOP/Printer
What should the string be if I want to use XP login username "Guest" within the workgroup "WORKGROUP" with no password on a host Ive called DESKTOP (or should I use its IP) with an XP printer share name of "Printer"?
At present I can see the job being added to the Linux print queue then it appears in the XP print queue as "Remote downlevel document" but never prints. Documents print okay if I attach the printer directly to the Linux USB.[/QUOTE]

I'm not sure if other ways are acceptable but this is the format I use and it works:

DeviceURI smb://W:X@Y/Z

where W is a valid username on the Windows box, X is W's password on the Windows box, Y is the (static) IP address of the Windows box and Z is the name of the printer being shared on the Windows box. e.g.:

DeviceURI smb://jsixpack:apasswd@192.168.1.10/hppsc

Since you are not using a password in your case I guess that field would just be blank. (I'm not sure if the colon should be kept or omitted).

---

### Post by 4plus2 on 2005-11-08
Turning off "Enable Bidirectional Support" fixes the problem alright!
Hope windows doesnt mind.  Thanks SickTwist.

---

### Post by 4plus2 on 2005-11-08
The DeviceURI I have working is smb://Guest@DESKTOP/HP-PSC 
ie. didnt need the colon as theres no password for Guest.
where the IP of DESKTOP I have in the hosts file.

---

### Post by SickTwist on 2005-11-08
I'm glad it worked for you too. :)

---

### Post by spiderbatdad on 2005-11-27
I haven't has problems printing web pages, but I cant print anything from the desktop help menu. Trying to print pages like "using ubuntu 5.10," Gnomemeeting help," etc. Print options not available on these help pages; <ctrl>p wont work. Please help.

---

### Post by optikburn on 2005-12-01
Here is another way to use your WIndows Printer in Ubuntu... it worked for me..


[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

---

