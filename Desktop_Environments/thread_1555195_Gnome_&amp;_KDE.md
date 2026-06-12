---
title: "Gnome &amp; KDE?"
date: 2010-08-17
forum: Desktop Environments
---

### Post by binarylife on 2010-08-17
so I'm having ubuntu 10.04 amd64 installed and as I know it uses Gnome environment ,then I've installed Kubuntu desktop system (KDE Environment),and whenever I log in KDE Session ,the Cairo dock and avant dock and screenlets appears on my KDE ,so is there anyway to separate KDE settings  from Gnome settings as what I've understood because I'm new to ubuntu and Kubuntu , so please help ? 
and thanks

---

### Post by ankspo71 on 2010-08-18
Hi,
I didn't realize it until now, but apparently the KDE desktop can run both Gnome's startup applications (located at /home/yourname/.config/autostart/) and KDE's startup applcations (located at /home/yourname/.kde/Autostart/)

Try starting KDE then go to Settings > System Settings > then Advanced Tab > Autostart. Now uncheck each of the applications you don't want to automatically start with KDE. Don't delete them though, because they will be deleted from your Gnomes startup applications too.

Hope this helps.

---

### Post by binarylife on 2010-08-18
> **ankspo71 said:**
> Hi,
I didn't realize it until now, but apparently the KDE desktop can run both Gnome's startup applications (located at /home/yourname/.config/autostart/) and KDE's startup applcations (located at /home/yourname/.kde/Autostart/)

Try starting KDE then go to Settings > System Settings > then Advanced Tab > Autostart. Now uncheck each of the applications you don't want to automatically start with KDE. Don't delete them though, because they will be deleted from your Gnomes startup applications too.

Hope this helps.

Thanks it works , and another solution is to make a new user !

---

