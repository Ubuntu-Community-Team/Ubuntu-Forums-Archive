---
title: "Printing pages in reverse order - Kubuntu"
date: 2006-09-23
forum: Desktop Environments
---

### Post by srunni on 2006-09-23
Hey,

Does anyone know how I can make pages print in reverse order on Kubuntu 6.06? Is it something I have to configure in KJobViewer?

Thanks in advance for the help

---

### Post by srunni on 2006-09-23
Anyone?

---

### Post by starling on 2007-02-20
Ok, i saw this in another [thread]("http://www.ubuntuforums.org/showthread.php?t=196363&highlight=print+reverse+order"). The nice guys at brother actually halped a linux user! He wanted to stop printing in reverse orser but it seems to work both ways for any printer (at least it did for his brother and my canon)
go to /etc/cups/ppd and edit the .ppd file of your printer. Add the following line:
> *DefaultOutputOrder: Reverse

Do you think I can increase the printable area with this? I might try that another time.

---

### Post by srunni on 2007-02-21
Thanks for the help - I'll have to look into that. I don't think you can increase the printable area of your printer by editing driver files though - some of that depends on the hardware, and the other part of it depends on the settings in whatever program you're printing from. For example, in OpenOffice.org, you can set the margins for a page by going to Format -> Page. However, you may be able to reduce the default margins to a certain amount in the driver files so that by default any program will have those margins set up.

---

### Post by yesjoshyes on 2007-11-15
> **starling said:**
> Ok, i saw this in another [thread]("http://www.ubuntuforums.org/showthread.php?t=196363&highlight=print+reverse+order"). The nice guys at brother actually halped a linux user! He wanted to stop printing in reverse orser but it seems to work both ways for any printer (at least it did for his brother and my canon)
go to /etc/cups/ppd and edit the .ppd file of your printer. Add the following line:


Do you think I can increase the printable area with this? I might try that another time.


nice!  this worked for me!  thanks so much!

---

