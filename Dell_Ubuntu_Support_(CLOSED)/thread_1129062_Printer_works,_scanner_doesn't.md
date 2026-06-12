---
title: "Printer works, scanner doesn't"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jawolfejr on 2009-04-18
I'm new to linux and have figured out some basics, but when online instructions don't work I sometimes get stuck.

I have a Brothers MFC490CW (print/scan/fax/copy).  I have successfully loaded the print drivers and used the printer.  However, when I tried to do the same with the scanner and give all users permission to use I followed the Brothers instructions and entered this into terminal:

/etc/udev/rules.d/40-basic-permissions.rules

This is the response I got:

bash: /etc/udev/rules.d/40-basic-permissions.rules: Permission denied

I also tried typing "sudo" before the command, but it simply said no such file.

So does anyone know how to get "permission"?  And also, what about all of the other features on the printer, like the card reader and fax?  Will I be able to utilize them or am I just stuck with printing and scanning?

Thanks any help.

---

### Post by desertdog on 2009-04-24
The file /etc/udev/rules.d/40-basic-permissions.rules is a text file, not an executable program. 

If you just want to read the file, you can type 
$cat /etc/udev/rules.d/40-basic-permissions.rules. 

If you want to edit the file, you can open a text editor $gedit /etc/udev/rules.d/40-basic-permissions.rules or $sudo gedit /etc/udev/rules.d/40-basic-permissions.rules.

---

