---
title: "Command for running OpenOffice applications"
date: 2009-01-17
forum: General Help
---

### Post by jac0117 on 2009-01-17
Hi, I'm trying to customize my cairo dock. I created a subdock just for openOffice.  I want to add launchers to it.  I can't find what the commands are to run writer, presentation, dictionary, spreadsheet, word processor.  THe command openoffice will launch a general openOffice application.  I would like to launch each application within openOffice individually.  What are the commands?  Thanks.

---

### Post by taurus on 2009-01-17
The OpenOffice programs should be in /usr/lib/openoffice/program.

---

### Post by mbeach on 2009-01-17
if they are in your applications menu already, you should be able to right click on "Applications", click "Edit menus", navigate down to the menu item, and click "Properties" to see the command.

I have:
writer: ooffice -writer %U
calc: ooffice -calc %U
impress: ooffice -impress %U

```
man ooffice
``` gives some more options for arguments.

---

### Post by gettinoriginal on 2009-01-17
Database = ooffice -base %U
Presentation = ooffice -impress %U
Spreadsheet = ooffice -calc %U
Formula = ooffice -math %U
Word Processor = ooffice -writer %U
Dictionary = gnome-dictionary

---

### Post by jac0117 on 2009-01-17
wow Gracias everybody.... all your comments worked... 

thanks again.

---

