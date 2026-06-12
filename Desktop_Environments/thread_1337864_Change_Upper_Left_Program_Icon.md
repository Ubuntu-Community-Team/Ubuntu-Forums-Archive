---
title: "Change Upper Left Program Icon"
date: 2009-11-25
forum: Desktop Environments
---

### Post by Paleo_Limno on 2009-11-25
Hi All,

I am trying to figure out how to change the icon displayed in the top left hand corner of an application window.  

I know how to change the icon for the program launcher (desktop and menu) and can even change the icon in the top left hand corner for some programs (firefox). 

My main problem is with OpenOffice.  I have the Sun version of OpenOffice 3.1 installed and am trying to change the icons associated with it in Cairo dock.  I have tried changing the icon name in the cairo dock icons folder to the WM Class for OpenOffice (ie. OpenOffice.org 3.1 -writer and other variants) but this does not work.  It seems as though cairo is displaying the icon that is located in the upper right hand corner of openoffice which is a rather pixilated version of a spreadsheet, word document, or presentation.  I figure if I can find the location of this icon I can change it and thus the cairo icon will be updated?  

Any ideas on how to change the cairo dock icons that I may have over looked?

---

### Post by supermelon928 on 2009-11-25
I wish I was on my ubuntu computer right now, because I'm not quite sure what you're talking about. What other programs have you been able to change that icon for, and can you describe the process when you did it successfully?

---

### Post by Mahngiel on 2009-11-26
$/.config/cairo-dock/current_theme

the icon needs to be overwritten in here

---

### Post by Paleo_Limno on 2009-11-26
I was able to change the icon in the upper left corner of a firefox window by changing the icon in the /usr/lib/firefox-3.5.5/icons folder.  The problem is I can't find a similar folder for OpenOffice.org.  

I have tried changing the icon in .config/cairo-dock/current-theme/icons to the appropriate WM Class which in this case is "OpenOffice.org 3.1"  I tried every variation of "OpenOffice.org 3.1" (ie. OpenOffice.org 3.1 -Writer, OpenOffice.org 3.1 -writer, openoffice.org 3.1 -writer, openoffice.org3 -Writer, and so on) but the icons are never recognized in cairo dock.  

I used the command: xprop | grep WM_CLASS  to find the WM Class for openoffice.  It comes out as OpenOffice.org 3.1 regardless of which application is running (Writer, Calc, Impress) so i'm not sure how to name the icons in .config/cairo-dock/current-theme/icons folder to reference a particular open office application.

---

### Post by fabounet on 2009-11-27
Do you use the option "overwrite X icons" ?
with it, the dock will not take the pixellised icon from X, but an icon in the current icon theme.

if you already use it, and if you still want to change the openoffice icon, you can put an icon in ~/.config/cairo-dock/current_theme, with the name "openoffice.org 3.1.png" (or .svg), the icon name is the class in lower case.

---

### Post by Paleo_Limno on 2009-11-27
I have tried it with and without the "overwrite X icons" option checked and have named the icon "openoffice.org 3.1"

---

### Post by Paleo_Limno on 2009-11-27
Another though/question:

How is the class of one OpenOffice program different from another.  For instance, no matter which OpenOffice program I look at the WM Class always comes up as "OpenOffice.org 3.1" regardless of whether or not it is Impress, Clac, or Writer.

---

### Post by miesogeno on 2010-02-23
i'm having the exact same problem, and i was wondering if by now you have already found the programs different classes.

for instance, i have writer and impress on the dock, i have enabled the option to merge launcher and application, so, if i use the same class for both programs, the indicators show up in both launchers icons.

really anoying.

---

