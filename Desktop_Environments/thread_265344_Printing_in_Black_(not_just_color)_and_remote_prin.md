---
title: "Printing in Black (not just color) and remote printing"
date: 2006-09-25
forum: Desktop Environments
---

### Post by wildutah on 2006-09-25
I installed my HP PSC 1350 on Dapper using the Administration|Printing tool and I had the following problems,

[LIST]
[*]I couldn't print remotely from my local network:-k 
[*]My printer printed using my very expensive, less dark, and imperfectly aligned color cartridge and refused to use the black cartridge:evil: 
[/LIST]

I found settings in the various printer configuration menus to activate the black cartridge but changing those settings didn't actually cause the printer to print in black.  In fact, those settings are just placeholders and don't affect the actual configuration at all.  It's pretty confusing to have printer settings there that don't do anything.](*,) 

I found out how to get the printing to work.:-D 

You have to use the CUPS interface instead of the impotent Administration|Printing tool.

Fire up a browser and head to [http://localhost:631/](http://localhost:631/) then you'll soon find the printer administration menu and be able to modify the printer settings.  Use "Set Printer Options" to activate the black printing cartridge.  (You'll probably need to set the printing to regular letter size paper also because the default nonstandard A4 paper isn't even available anywhere I know of.)

Then you'll find that CUPS isn't accepting your password.  That's because it can't read the password file.  you'll have to add cupsys into the shadow group or you won't be able to change any printer settings.  (This may be a security problem if all three of these are true:  you have weak passwords, untrusted malicious people use your computer, and CUPS has security bugs.)

~>  sudo adduser cupsys shadow

Now you should be able to change printer settings.  If not, do this too (you shouldn't have to),

~>  sudo adduser YourUserName lpadmin

Now you can print in black as well as in color. :-D Since 98% of your printing is probably text, that's a very good thing.

To use your printer remotely in your local network (assure you're on a secure, firewalled subnet first), set the admin setting to "share published printers connected to this system."  Then you can connect to the printer from a remote system by adding a printer to that system using CUPS.

add the printer as a "http" remote printer with the URL "http://Hostname_With_Printer_Attached:631/printers/Printername_On_Host" and then add it as a postscript printer.  ***Do not add the printer as its true hardware type.***  Just add it as generic postscript.

*Voila!*

---

