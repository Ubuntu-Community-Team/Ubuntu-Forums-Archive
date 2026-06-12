---
title: "Unable to print to a shared printer"
date: 2009-09-10
forum: Desktop Environments
---

### Post by hawks1282 on 2009-09-10
Hello All,

I hope I'm posting this in the correct area . . . 

I just set up Ubuntu on my computer (haven't had to boot Vista in a week :-) ) and I'm trying to get the printer working.  

It's an HP Laserjet 1200 connected to the network with Netgear Mini Print Server that is working with windows.  

I've tried a couple of methods to connect to it, including the CUPS browser interface, and Printing in the System -> Administration menu.  The closest I've gotten it to working is setting it up as an smb share, with URI smb://PS0CA5D8/P1.  Once I set it up like this and select the driver, the Printer State displays as Idle.  When I try to print a test page, the Status changes to "Processing - Unable to connect to CIFS host, will retry in 60 seconds..." and nothing happens at the printer.  

Can anyone help me with this?  

Thanks

---

### Post by SoftwareExplorer on 2009-09-10
What version of ubuntu are you using? Jaunty has a bug with SMB priter sharing (which is what you would be using if the printer is shared from a windows printer) that takes an extra step to get around.

---

### Post by hawks1282 on 2009-09-12
I'm using Jaunty (9.04)

---

### Post by SoftwareExplorer on 2009-09-12
Not sure if this is the same problem, but try this:
[http://ubuntuforums.org/showpost.php?p=7214797&postcount=6]("http://ubuntuforums.org/showpost.php?p=7214797&postcount=6")

---

### Post by hawks1282 on 2009-09-13
It's a bit different than that, I've successfully installed the printer, but when I try to print nothing happens.  If I look at the printer properties it reads "Processing - Unable to connect to CIFS host, will retry in 60 seconds..." under the Printer State area.

---

### Post by hawks1282 on 2009-09-14
bump anyone? :confused:

---

### Post by Tux+ on 2009-09-14
Did you add the printer using the Gnome interface?

If you did make sure you enter the IP address only and not include the HTTP:// | SMB://

---

### Post by hawks1282 on 2009-09-14
Ok, I'll try clearing out the smb:// portion in the printer URI when I get back to that PC . . .Thanks

---

### Post by hawks1282 on 2009-09-14
I tried getting rid of smb:// that was placed automatically when I installed the printer, but when I apply, I get an error "There was an error during CUPS operation: 'client-error-not-possible'.

P.S.  I would suspect that client errors ARE possible :P

---

### Post by hawks1282 on 2009-09-14
Ok, I did a bit more searching tonight and dug deeper, and found the following page [http://ubuntuforums.org/archive/index.php/t-30288.html](http://ubuntuforums.org/archive/index.php/t-30288.html) which has the fix that worked for me.  Only difference is that in my queue I entered P1, as that's the share name of my printer.  

Thanks for the help.

---

### Post by rial_024 on 2010-10-27
i am printing to a network printer..! i can print to other printers  except to LQ680 which is also a network printer. error message unable to connect to CIFS host.  i tried to delete the printer and add again but the same problem occur  (oh when im adding printer driver only lq570+ there is no driver for  LQ680)  what should i do?.. can you help me please..

---

