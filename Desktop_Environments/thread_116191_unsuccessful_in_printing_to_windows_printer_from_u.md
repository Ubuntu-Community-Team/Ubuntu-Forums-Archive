---
title: "unsuccessful in printing to windows printer from ubuntu linux"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Nasir Amra on 2006-01-12
I have a puzzling problem with a windows shared printer ( an hp officejet 5110). I am able to setup via ubuntu printing wizard a printer queue to the windows shared printer (network printer using windows smb). However, when I print the document rom ubuntu linux, I see it in the printer queue on the windows machine , but nothing gets printed out. Does anyone have any ideas what to do next or how to troubleshoot this further?

---

### Post by SickTwist on 2006-01-12
Try disabling support for bidirectional printing on the Windows box.

To disable it, open up the printer properties on the Windows box (right click the printer and choose "Properties"), click the "Ports" tab and uncheck "Enable bidirectional support".

---

### Post by N8MAN1068 on 2006-01-12
Do you have the printer installed in Ubuntu under System-Administration-Printers?
What driver are you using? Try the driver for a 990c.

---

### Post by Nasir Amra on 2006-01-13
I've tried to disable bidirectional printing, but now when I try to print the test page, I don't even see the test page listed in the printer queue on the windows machine and no test page is printed. So I went back to enable bidirectional printing and switched my printer driver from officejet-5110 to deskjet 990c and still the same problem. 

Any other suggestions for me to try?

Thanks,

---

