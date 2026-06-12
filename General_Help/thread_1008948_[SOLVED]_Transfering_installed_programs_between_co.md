---
title: "[SOLVED] Transfering installed programs between computers?"
date: 2008-12-12
forum: General Help
---

### Post by mahela007 on 2008-12-12
I have installed ubuntu 8.1 using wubi to just give it a spin. Now I would like to reinstall it without using wubi. Up till now I have downloaded many programs and application for the wubi installation of ubuntu. Is there anyway I could transfer these programs to the new installation of ubuntu? I am on a limited bandwith connection and I dont want to have to download the application again if I can avoid it. I dont have .bed files for any of the apps. I installed all of them using Synaptic. Can anyone help?

---

### Post by plucky on 2008-12-12
> I have installed ubuntu 8.1 using wubi to just give it a spin. Now I would like to reinstall it without using wubi. Up till now I have downloaded many programs and application for the wubi installation of ubuntu. Is there anyway I could transfer these programs to the new installation of ubuntu? I am on a limited bandwith connection and I dont want to have to download the application again if I can avoid it. I dont have .bed files for any of the apps. I installed all of them using Synaptic. Can anyone help?


I do not use WUBI so I am not sure this will work but:

All your downloaded .deb files are stored in **/var/cache/apt/archives** directory.You could save them to CD or external drive and copy them back after the new install.

Or use a program in Synaptic called **AptonCD** which will create a .iso of all your applications and burn them to a CD ready for re-installation.


Good Luck

---

### Post by meson2439 on 2008-12-12
Try [LVPM]("http://lubi.sourceforge.net/lvpm.html"). The deb file is small enough I think.

---

### Post by abrussak on 2008-12-12
I would suggest using [Remastersys]("http://www.remastersys.klikit-linux.com/") to make a backup of your install and just burn that to DVD and install with that.

---

