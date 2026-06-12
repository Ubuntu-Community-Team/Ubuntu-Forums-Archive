---
title: "[New to linux] screen goes white when enabling desktop effects!"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by Gurkamal on 2008-01-30
Hey i'm new to ubuntu linux and i really like it but i have a problem  with my desktop effects.

When i enable my desktop effects my screen turns white for approx. 30 seconds or so.




please help..


When i type lspci |grep VGA,  i get:
> 
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)



Please help me resolve my white screen issue so i can finally enable the desktop effects.

---

### Post by overdrank on 2008-01-30
> **Gurkamal said:**
> Hey i'm new to ubuntu linux and i really like it but i have a problem  with my desktop effects.

When i enable my desktop effects my screen turns white for approx. 30 seconds or so.




please help..


When i type lspci |grep VGA,  i get:




Please help me resolve my white screen issue so i can finally enable the desktop effects.

HI and unichrome is not the best for 3d graphics you may look at this link
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by Gurkamal on 2008-02-02
I followed the installation instructions from your link, but when I type 

"sudo sh VIA_Ubuntu704_UniChrome_GFX_v40072d.run" into the terminal i get:

computer@computer-desktop:~/Desktop$ sudo sh VIA_Ubuntu704_UniChrome_GFX_v40072d.run
Password:
Verifying archive integrity... All good.
Uncompressing VIA UniChrome(Pro) Family Linux Graphics Driver for Ubuntu 7.04 v4.1.00.72......................................................................................................................................................................................

Please choose the job you want to do:
1. Install driver
2. Uninstall driver
1
====== VIA UniChrome (Pro) Family Display Driver for Ubuntu 7.04 ======
====== Installation Program ======
Error:
  This driver package is only support the default kernel
  "2.6.20-15-generic" for Ubuntu 7.04


Any help would be GREATLY appreciated.

---

### Post by arvindenrique on 2008-02-02
go to system--->administration--->restricted drivers manager

it may solve ur prob

---

### Post by Gurkamal on 2008-02-03
When i go to restricted drivers manager it says:

"Your hardware does not need any restricted drivers"

---

