---
title: "Google earth works with wine 0.9"
date: 2005-11-17
forum: Desktop Environments
---

### Post by suoko on 2005-11-17
add following line to your /etc/apt/sources.list 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
and do a
sudo apt-get update && sudo apt-get upgrade

Follow the instructions in 
[http://gentoo-wiki.com/HOWTO_Install_GoogleEarth_with_wine](http://gentoo-wiki.com/HOWTO_Install_GoogleEarth_with_wine)

In case of problems here is the forum:
[http://appdb.winehq.org/appview.php?versionId=3254](http://appdb.winehq.org/appview.php?versionId=3254)
Good luck !!

---

### Post by adwait on 2005-11-17
Yay!!! I am gonna try that later.......

---

### Post by Hairy_Palms on 2005-11-18
when i run wine GoogleEarthsetup.exe i get an error and it crashes.
> err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:CoGetClassObject class {00020424-0000-0000-c000-000000000046} not registered
err:ole:marshal_object couldn't get IPSFactory buffer for interface {6494206f-23ea-11d3-88b0-00c04f72f303}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040154err:ole:CoMarshalInterface Failed to marshal the interface {6494206f-23ea-11d3-88b0-00c04f72f303}, 80040154


---

### Post by jlx on 2005-11-18
Just wait. Google confirmed that they are developing Google Earth for Linux. It will be soon running native in every linux machine.

---

### Post by suoko on 2005-11-18
[QUOTE=Hairy_Palms]when i run wine GoogleEarthsetup.exe i get an error and it crashes.[/QUOTE]

Try removing your .wine directory, reboot and retry following the instructions.
I had to do that to have it running.
make a backup of your current .wine directory if you are using wine for other apps

---

