---
title: "Printer Config Icon MIA in KDE"
date: 2011-11-16
forum: Desktop Environments
---

### Post by invenit on 2011-11-16
I just installed KDE 4.7.2 in an Ubuntu 11.10 derivative distro and the KDE DE is superb! However, somehow the printer configuration icon in System Settings went MIA. Any way to get it back (or, possibly, any way to change the default printer without the icon)?

---

### Post by McNils on 2011-11-16
You can use the printer applet in the systray.
I think the  printer applet is hidden in the systray. Click on the arrow (triangle) to see hidden entries. From the settings menu you can configure printers.

I dont know how to restore kparts to systemsettings, but I find the problem interesting, I will take a look at it.

---

### Post by McNils on 2011-11-16
I found an other way 
kcmshell4 system-config-printer-kde
List all
kcmshell4 --list

Maybe you uninstalled system-config-printer-kde?

---

### Post by invenit on 2011-11-16
> You can use the printer applet in the systray.

Thanks for replying. No printer applet is showing. I see four applets (AkonadiTray, Device Notifier, KOrganixer Reminder Daemon and Nepomuk File Indexing). OTOH, I can print just fine. The system just defaults to PDF so I have to manually change the print setting back to my Samsung printer.

---

### Post by invenit on 2011-11-16
The printer icon now appears in System Settings (thanks!), but it does not work. In the terminal 

"kcmshell(2406)/python (plugin): Failed to import module 
kcmshell(2406)/kcontrol KCModuleLoader::loadModule: This module has no valid entry symbol at all. The reason could be that it's still using K_EXPORT_COMPONENT_FACTORY with a custom X-KDE-FactoryName which is not supported anymore"

And, when I click the icon: "The service 'Printer Configuration' does not provide an interface 'KCModule' with keyword 'system-config-printer-kde/system-config-printer-kde.py' The factory does not support creating components of the specified type."

---

### Post by SeijiSensei on 2011-11-16
As an alternative, you can use the web-based configuration tool that comes with CUPS.  Point a browser at [http://localhost:631/](http://localhost:631/).  If you need to make changes that require root privileges, like adding a printer, you'll be prompted for your username and password at that time.

---

### Post by invenit on 2011-11-16
Thanks SeijiSensei! Your solution solves my problem and I can now change the printer default.:p

---

### Post by McNils on 2011-11-16
An other alternative is to use lpadmin to set the default printer. 
sudo lpadmin -d printName
List all installed printers
lpstat -a

---

### Post by invenit on 2011-11-16
Thanks McNils! You folks are great.

---

