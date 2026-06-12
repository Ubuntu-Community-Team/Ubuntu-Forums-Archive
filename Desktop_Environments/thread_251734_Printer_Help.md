---
title: "Printer Help"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Dcastle on 2006-09-05
Hi, I am trying to setup my networked printer. It is a lexmark z615. I followed this guide: [http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+z600](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+z600)   
 I know it is for hoary but I couldn't find anything else. I also used [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)   The driver seems to be working, how ever when I getto step 3 of "Add a printer I am not sure what to enter in the fields of "Description" and "Location" Help is appreciated. Thanks

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-05
I don't believe those two fields during the third step are imperative in terms of sending a print job to the printer and successfully printing...! 

In other words, try leaving them blank. I having no value that identifies the  location of my printer, however, the description I use is just the name of the printer itself. 

Let me know if you experience any hang-ups with the process! 

~b-Dub!

---

### Post by Dcastle on 2006-09-06
Well did as you said. Clicked print on a document and nothing happend at the printers end. Any ideas?

---

### Post by bigken on 2006-09-06
is this print hooked upto a router if so the location is the ip address of the printer if so you would be better off giving it a static ip address ;)

---

### Post by Dcastle on 2006-09-06
Its not hooked up to a router. I am using the windows pc as the host

---

### Post by bigken on 2006-09-06
sorry I cant help you anymore but have you considered using the ubuntu pc as the host and following one of the guides

---

### Post by funkydan2 on 2006-09-06
It's my understanding that currently there is a bug in Ubuntu dapper when it comes to printing **from** a Ubuntu machine **to** a printer connected to a Windows machine.

The bug has been reported through launchpad, but no progress on it so far.  I've read else where that downgrading to an earlier version of cupsys may fix the problem, or alternatively live on the wildside and see if the bug exists in edgy (the next version of Ubuntu, currently under development).

---

### Post by mgmiller on 2006-09-06
I have not had any problems connecting from a dapper machine to a windows XP functioning as print server.  FIrst, make sure the windowsXP machine is running and on your network and is sharing the printer you want.  Then, on the Dapper box, in the System>Administration>Printing dialog, just click on new printer and tell it windows SMB printer, it will prompt you for the login info for your XP box. then click on the drop down for the location and select the windows XP box.  Then click on the printer drop down and the hosted printers should be there, just select it.  Make sure you specify the correct paper types and Etc in the other tabs and it should "just work".

---

### Post by Xanthus on 2006-09-06
I followed the same thread and I got as far as It recognizing the printer but it won't print.

---

### Post by Xanthus on 2006-09-06
I'm new to this whole linux thing though I do roughly understand the basics and whatnot, but I have no idea where or what System-->Administration-->Printing Diolog
is, i can't find it, does the package need to be installed?

---

