---
title: "Add to list of programs to run when Removable media is inserted"
date: 2014-02-01
forum: Desktop Environments
---

### Post by mike134 on 2014-02-01
I am running Lubuntu 13.10 and when I insert a USB flash drive I get a "Removable medium is inserted" dialog box asking me to "Select the action you want to perform", but there is only one option "Open in File Manager" - how can I add to these options so that I have a choice of what to open USB drive with.  

I can use PCManFM - Preferences - Volume Manager - "Show available options for removable media when they are inserted" to determine if the "Removable medium is inserted" dialog box is shown or not, but I don't how to add to the options.

Mike

---

### Post by mike134 on 2014-02-06
I have made a little progress on this:
I have shotwell installed and if I insert a USB flash drive or memory card which contains images in a DCIM directory, then Shotwell is added to the dialog box asking me to "Select the action you want to perform".  This seems to be controlled in part by the shotwell.desktop file as if I change the "Name" field in this file, this is reflected in the dialog box and if I delete shotwell.desktop, then I don't get the additional option in the dialog, however if I rename the shotwell.desktop file, so it still has a desktop extension, then I don't get the additional option in the dialog box (even after a reboot), but I see it on the main menu.  So there must be something else that controls this.
Also the "Open in File Manager" option seems to be hard-coded as if I remove pcmanfm.desktop files, then this option still comes up.

I want to run a custom script for ANY USB flash drive or memory card as I want to provide an option to format or label the drive as I am setting up this system for my wife and she is not going to want to use the command line to label or format a USB drive.

So still investigating ...

---

### Post by info-csizma on 2014-03-06
Keep up the good work - I'm interested as I've a Rockbox'ed iPod which I want to run a custom script everytime it connects

---

