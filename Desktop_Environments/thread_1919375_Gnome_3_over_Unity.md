---
title: "Gnome 3 over Unity"
date: 2012-02-02
forum: Desktop Environments
---

### Post by ssherwood on 2012-02-02
Hiya Ubuntu User,

I have an issue, I find the unity DE a little slow and sluggish and have installed Gnome 3 Shell but the DE doesnt appear. I can right click and a notification appears about my network and that is it.

Can anyone of you help me please.

Any and all help will be appreciated.

Thanks Stephen...

---

### Post by Supermouse on 2012-02-02
Are you using 10.10 or 11.10?

In 11.10 Gnome-Shell is in the repos, so if you install it there should be no problems.

In 10.10 you may need some wizardry to make it work, so I cannot help...

---

### Post by Frogs Hair on 2012-02-02
If using 11.10 select Gnome from the session list at login . The Gnome Shell may require a proprietary graphics driver on some computers .

---

### Post by ssherwood on 2012-02-03
Thanks guys,

Im running 11.10 and I've installed the gnome shell and logged in but nothing works other than right-click and the network notification.

stephen

---

### Post by Frogs Hair on 2012-02-03
Run the following command in the terminal and copy and paste the output in code tags using the # symbol on the reply tool bar . ```
lspci
```

---

### Post by moonport on 2012-02-03
BTW, If U're interested:

Return to Ubuntu Classic Desktop in Ubuntu 11.10
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)

---

### Post by ssherwood on 2012-02-04
Heres the output:

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
00:0a.0 USB Controller: NEC Corporation USB (rev 43)
00:0a.1 USB Controller: NEC Corporation USB (rev 43)
00:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


```

---

### Post by lolpenguin on 2012-02-04
If nothing appears then it's probably broken. This usually happens with extensions, but this is a fresh install right?
Try this
```
sudo apt-get install --reinstall gnome-shell
```
If that doesn't work then try this
```
sudo apt-get purge gnome-shell
sudo apt-get install gnome-shell
```
Otherwise it's a problem with your hardware.

---

