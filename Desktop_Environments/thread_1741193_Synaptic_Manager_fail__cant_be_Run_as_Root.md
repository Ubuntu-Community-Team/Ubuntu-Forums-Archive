---
title: "Synaptic Manager fail :: cant be Run as Root"
date: 2011-04-27
forum: Desktop Environments
---

### Post by phnet1111 on 2011-04-27
When trying to run Synaptic it does not run at all but when running software center everything seams to work nice. trying to fix synaptic i used the commandline using the commands of ::

sudo aptitude update 
sudo dpkg --configure -f install 

then also ran 
sudo synaptic  and it gave me this error

[ERROR]
sh: kde-config: not found
sh: kde-config: not found
Segmentation fault

this is what i dont understand it that why it is showing kde-config but i am running Gnome.

i have google and scan the forums for the solution but have found nothing that could help me thats why i am posting here.

please help

---

### Post by Krytarik on 2011-04-27
First, you shouldn't run it with "sudo", but with "gksu" instead:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Launching it through its menu item doesn't work?
"System -> Administration -> Synaptic"

Its *.desktop file for Gnome states this command:
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```
Whereas those for KDE states only "synaptic".

---

### Post by Yellow Pasque on 2011-04-27
I see a few solutions to the error, most involving gtk-qt theme packages: [http://search.yahoo.com/search?p=%22sh%3A+kde-config%3A+not+found%22&ei=UTF-8](http://search.yahoo.com/search?p=%22sh%3A+kde-config%3A+not+found%22&ei=UTF-8)

---

