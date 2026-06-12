---
title: "LibreOffice 4.4 - Fatal Error"
date: 2015-05-19
forum: Desktop Environments
---

### Post by Jonners59 on 2015-05-19
After my upgrade to 15.04 and reinstalling LibreOffice I get the following message [HTML]The application cannot be started. 
User installation could not be completed.[/HTML] and I can not open it or any documents with it.  I have tried un-installing and reinstalling, but nothing works for me.

If I open a terminal and type either libreoffice or libreoffice U% it does the same, and no information in the terminal scripts.

---

### Post by Jonners59 on 2015-05-19
Found the answer:


[LIST=1]
[*]Press Ctrl+H in Nautilus (this also works in most other file browsers) to show files and folders whose name start with ..
[*]Go into the .config folder in your home folder.
[*]Find the folder (inside .config) named libreoffice.
[*]Make sure LibreOffice is not running. In this specific case it appears to be exiting completely after giving you the error, so you don't have to do anything for this step.
[*]Rename this libreoffice folder to libreoffice.old
[*]&#8203;Then just restart LibreOffice
[/LIST]

---

### Post by tomek7 on 2015-10-11
Thank you Jonners that worked as charm!!
Regards, Tomek

---

### Post by Jonners59 on 2015-10-12
> **tomek7 said:**
> Thank you Jonners that worked as charm!!
Regards, Tomek

A pleasure.  Pleased it helped you and saved you days of searching... :-)

---

