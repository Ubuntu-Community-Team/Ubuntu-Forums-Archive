---
title: "Startup Applications not Starting Up"
date: 2011-08-10
forum: Desktop Environments
---

### Post by schein123 on 2011-08-10
On Ubuntu 10.04, I have been trying to add some Gnome startup applications via the menu system without success.  How can I debug/trace this process?

---

### Post by Tamlynmac on 2011-08-10
Just a quick thought. Have you tried adding the apps to "system/preferences/startup applications"? Are they checked in the startup applications window? If unchecked they will not start.

If you've done that, please list a few of these apps and where your trying to start them from in the file system. For example: if you were trying to start gnome-dictionary it would be located here, "file system/user/bin/gnome-dictionary". As an executable.

Good Luck and hope this helps. Don't forget to explain which apps and the procedure your using to perform this task, if you need more help.

---

### Post by schein123 on 2011-08-11
Hello Tamlynmac - 

My executables are set in the menu item you described and are checked.

Currently, I am having trouble starting workrave (installed via synaptic).  Until recently, I have been having trouble starting a tool called davmail.

Thanks

---

### Post by whatthefunk on 2011-08-11
Check ~/.config/autostart
Do your programs have files there?

---

### Post by Tamlynmac on 2011-08-11
After investigating workrave, apparently it opens in the panel as an  applet and should open from "file system/usr/bin/workrave". This should  place 3 separate boxes in your panel. Not certain which panel, if your  using both top & bottom. Can you open it manually by double clicking  on it the Nautilus file browser "places/home folder/file  system/usr/bin/workrave"?

Also, check to see how many workrave executables are listed. You may  have multiple files named workrave. One for the setup &  configuration and one for the panel applet, etc.

One last thing, have you checked your "Add To Panel" (right click on an  empty space in your panel and select Add To Panel). The applet may  already be listed in there and all you need do is select and add it to  you panel. It would then start up in the panel each time you logged on.  If it's not listed in the "Add To Panel" listing, left click one time on  "Create Application Launcher" then select the "Add" button at the  bottom. A launcher window will open and simply complete it like you do  in apps menu. Once created, close the launcher window and find it in the  "Add To Panel" listing, select it and click on the "Add" button at the  bottom. This should add it to your panel.

Good Luck and once again I hope this helps.

---

### Post by schein123 on 2011-08-12
Hi Tamlynmac - 

After several reboots it seems my programs began starting up.  I can't be sure if/what I changed that may have helped this process, as I was configuring the machine to get actual work done during this time.

I'll continue the thread if things start breaking.

Thanks for the help!

Andy

---

### Post by Tamlynmac on 2011-08-12
Amazing. Don't you just love it when things start working all by themselves? :)

Good Luck and hope you continue with the success.

Mac

---

