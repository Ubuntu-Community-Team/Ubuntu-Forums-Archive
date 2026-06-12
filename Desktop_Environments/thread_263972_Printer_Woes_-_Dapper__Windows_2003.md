---
title: "Printer Woes - Dapper / Windows 2003"
date: 2006-09-24
forum: Desktop Environments
---

### Post by htimst on 2006-09-24
Hi Folks,

I'm at my wits end with this...

I have an application running on Windows 2003 that our office rdp's to the win2003 server in order to run.  Our desktop enviroment is DD6.06.

We were having label printer woes so after some painstaking trial and error, decided to purchase a Citizen CLP-521Z.  The "Z" version emulates a Zerbra printer that is supported by the CUPS driver.  So, as our desktop enviroment is Ubuntu, and all our workstations are Ubuntu, we wanted to have the label printer accessible to the general work pool by being plugged into one of the ubuntu boxes and then sharing it so labels printed from the 2003 server application were printed out at our front desk.

This is good in theory.  The printer installs fine in Dapper.  It prints a nice test page and gives the impression that all is well!  The Windows Server recongnizes the printer share and there is a Windows 2003 driver for the CLP-521Z.  So adding the printer in 2003, installing the 2003 driver, installing the printer on the ubuntu box with CUPS driver, we only get gobbldy gook being printed out from the windows server.

As the printer emulates a Zebra printer, I have tried every Zebra printer model in an attempt to try and get something to print that isn't total garbage.  I have been unsuccessful so far.

Is there some concession that I'm failing to make when printing from windows 2003 to a shared printer on a Dapper box?  I mean, setting this thing up for sharing with CUPS is silly easy.  It's recognized, there is a driver for 2003, but the information being printed is three or four pages of test characters when I try and print a label.

I was just wondering if anyone else had issues or suggestions to stear me in the right direction.

Sorry for the long post.

Cheers!

---

### Post by Shay Stephens on 2006-09-24
I don't really have any help to offer other than to share the link I used to get my printer working in ubuntu:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by htimst on 2006-09-24
Thanks for the link, Shay.  Printing works, it's just printing from the Win Server to the printer attached to ubuntu is just a bunch of characters with no resemblance to what was actually printed.  I have my fingers crossed for a solution.

cheers!

---

### Post by mor on 2007-01-30
[http://www.ubuntuforums.org/showthread.php?t=97170&highlight=rdp+printing](http://www.ubuntuforums.org/showthread.php?t=97170&highlight=rdp+printing)

Did the trick for me. There's no way to do it using tsclient, the rdesktop gui.

I made a launcher on my desktop with this command:

rdesktop -g1280x800 -a24 -f -rsound -r 'printer:Stylus-CX6600' ip-address

Replace Stylus-CX6600 with the name of your printer. You can get this from System->Adminstration->Printing. Replace ip-address with the server's address.

---

