---
title: "Flash 8 Professional won't install in latest version of Wine"
date: 2008-09-06
forum: Desktop Environments
---

### Post by Flash Kid on 2008-09-06
Hello all. I am a Windows user running Ubuntu linux as a VM. My friend Max who is a true Ubuntu user was able to get Flash 8 up and running on Wine just by using the installer. Most of the tutorials I've found have told me I need to transfer the files from my Windows partition (which I have none). So I tried using the intstaller EXE and about half way into the install Flash gives me an error on InstallShield that says "Your system has not been modified. Please try re-installing later." Does anyone know how to fix this so I can get Flash running on here? :D

FK

---

### Post by azzamite on 2008-09-06
Just copy the directory where Flas 8 is installed in windows to a USB flash drive, then launch the VM and open the USB flahs drive from the VM, copy the folder to your home directory and execute it.

make shure wine is configured properly and try reinstalling it, in the worst scenario, delete the dir ~/.wine and try again.

You may also check this page
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3673](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3673)

---

### Post by Flash Kid on 2008-09-07
> **azzamite said:**
> Just copy the directory where Flas 8 is installed in windows to a USB flash drive, then launch the VM and open the USB flahs drive from the VM, copy the folder to your home directory and execute it.

make shure wine is configured properly and try reinstalling it, in the worst scenario, delete the dir ~/.wine and try again.

You may also check this page
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3673](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3673)
¿Es posible que se pueder instalar lo del EXE? Mi amigo puede hacerlo en su Xubuntu. Pero no podí en mi ubuntu.

Gracias,
FK

---

