---
title: "ERROR : Brother LPD filter is not installed"
date: 2006-09-26
forum: Desktop Environments
---

### Post by hibernatus on 2006-09-26
Hi, 

I try to install my brother MFC5840CN, but when i follow the install instruction from site [http://solutions.brother.com/]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html")

I receved somme error :

> root@hibern:/home/john/Desktop# dpkg -i --force-all cupswrappermfc5840cn_1.0.0-1_i386.deb
dpkg - avertissement, problème contourné à cause de --force :
 l'architecture du paquet (i386) ne correspond pas à celle du système (amd64)
Sélection du paquet cupswrappermfc5840cn précédemment désélectionné.
(Lecture de la base de données... 87002 fichiers et répertoires déjà installés.)Dépaquetage de cupswrappermfc5840cn (à partir de cupswrappermfc5840cn_1.0.0-1_i386.deb) ...
Paramétrage de cupswrappermfc5840cn (1.0.0-1) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC5840CN
chmod: cannot access `/usr/local/Brother/inf/brMFC5840CNrc': No such file or directory
/etc/init.d/cups: Command not found.

root@hibern:/home/john/Desktop#


does anny one know how can i install and configue my MFC?

Thanks
John

---

### Post by bigken on 2006-09-26
Take a look [here]("http://www.ubuntuforums.org/showthread.php?t=105703") ;)

---

### Post by hibernatus on 2006-09-26
Hi, 
I have done all like you until the step 4 (but my printer is not connected by usb, it's by Ethernet)

unfortunatly i have retry all and i still have an issue

> root@hibern:/home/john/Desktop# dpkg -i --force-all cupswrappermfc5840cn_1.0.0-1_i386.deb
dpkg - avertissement, problème contourné à cause de --force :
 l'architecture du paquet (i386) ne correspond pas à celle du système (amd64)
(Lecture de la base de données... 87020 fichiers et répertoires déjà installés.)Préparation du remplacement de cupswrappermfc5840cn 1.0.0-1 (en utilisant cupswrappermfc5840cn_1.0.0-1_i386.deb) ...
/etc/init.d/cups: Command not found.
Dépaquetage de la mise à jour de cupswrappermfc5840cn ...
Paramétrage de cupswrappermfc5840cn (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC5840CN
/etc/init.d/cups: Command not found.

root@hibern:/home/john/Desktop# 


/etc/init.d/cups: Command not found. and it's true when i look in the directory /etc/init.d/ their is no cpus

John

---

### Post by bigken on 2006-09-27
you have to give your printer a static ip address

---

### Post by bigken on 2006-09-27
also there are two sets of drivers [lpd ]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")and [cups]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html") also have you installed csh
if you use bobsongs tutorial you must follow it word for word ;)

---

### Post by hibernatus on 2006-09-27
Hi, 
thanks for your help, i have create a symbolic link : 

> root@hibern:~# ln -s /etc/init.d/cupsys /etc/init.d/cups


and then retry the installation, and now it's ok.

but when i look my printer configuration in the file /etc/cups/printers.conf i see :

> <Printer MFC5840CN>
Info MFC5840CN
DeviceURI usb:/dev/usb/lp0
State Idle
StateTime 1159307126
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>



but my printer is not connected true the usb port but buy ethernet 

How can i update coorectly my configuration now?

John

---

### Post by bigken on 2006-09-27
easy in the printer properties click the conection tab and select unix printer (lpd) and network printer in host type the ip address of the printer you can manually asign a ip address to printer using the printer interface ;)

---

### Post by hibernatus on 2006-09-27
Hi ,

thanks for your answer, what's i have to enter in the queue filed?

---

### Post by bigken on 2006-09-27
nothing just leave it blank or if u want u could use the name the printer gives it self which would be something like BRN_XXXX ;)

---

### Post by hibernatus on 2006-09-27
I have put the ip adresse off the printer, but when i send a a test page to the printer nothing append

I have ping the printer and it's ok

How can i see if the printer is correct? is their somme where somme logs where i can see the status and if their is some error in the communication?

---

### Post by bigken on 2006-09-27
in a terminal type sudo gedit /var/log/cups/error_log

---

### Post by bigken on 2006-09-27
also try this sudo cp /usr/share/cups/model/brmfc5840cn_cups.ppd /usr/share/ppd/

---

### Post by hibernatus on 2006-09-27
Hi 
here is the message that i have in my log

> E [27/Sep/2006:22:02:16 +0200] [Job 15] No %%BoundingBox: comment in header!
E [27/Sep/2006:22:05:36 +0200] [Job 16] No %%BoundingBox: comment in header!
E [27/Sep/2006:22:06:30 +0200] [Job 17] No %%BoundingBox: comment in header!
E [27/Sep/2006:22:14:43 +0200] [Job 18] No %%BoundingBox: comment in header!
E [27/Sep/2006:22:15:00 +0200] [Job 19] No %%BoundingBox: comment in header!


---

### Post by bigken on 2006-09-27
take a look [here]("http://ubuntuforums.org/showthread.php?t=256964&highlight=brother+mfc+fax") this might help ;)

---

