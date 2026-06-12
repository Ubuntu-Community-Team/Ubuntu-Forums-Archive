---
title: "How to install all desktops environments in Ubuntu 12.04?"
date: 2012-08-21
forum: Desktop Environments
---

### Post by Martial-law on 2012-08-21
__Hello,


I wish to install all desktop environments in my Ubuntu 12.04 In addition to Unity, I wish to install Gnome 3, KDE, Xfce and LXDE. I also wish to give all desktops the default orange color theme of ubuntu so all DEs look original Ubuntu. Kindly inform how to do that. 


PS.: There is also a distribution based on Ubuntu 12.04 having all the desktop environments but its in French language and every DE has different color and I also don't know if its stable. Below is the link:


[http://distrowatch.com/table.php?distribution=hybryde](http://distrowatch.com/table.php?distribution=hybryde)

---

### Post by Frogs Hair on 2012-08-21
You can install the Kubuntu , Lubuntu, Gnome Shell and Xubuntu desktop environments from the software center or synaptic, but you will have to logout to use each of them unlike the distro you linked. Another thing you have to know is do you have the system resources to run all of them.  

Each desktop has its own default theme and applications so you would have to learn how to customize each them. I'm pretty sure that each desktop has an ambiance style theme available. I have tried all the environments listed plus E17 , but only one at a time. Get ready for a lot updates if you choose to do this. The splash and login screen will change also.

---

### Post by JRV on 2012-08-21
It can be done, but it gets messy. As pointed out above.
It would be best to install each in a seperate partition and multi-boot.

But to answer your question:```

sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop

```

---

### Post by black veils on 2012-08-21
for theming:

[lxde and xfce]("http://linux.softpedia.com/get/Desktop-Environment/Themes/Ambiance-and-Radiance-Themes-for-Xfce-LXDE-76029.shtml")

[kde]("http://maketecheasier.com/give-kde-desktop-ubuntu-makeover/2011/11/23")

[gnome shell]("http://www.webupd8.org/2011/05/ubuntu-ambiance-gnome-shell-theme.html")

---

### Post by mrreality13 on 2012-08-22
i prefer lxde as my daily user all i did was in synaptic search for  lxde and installed lxde and lxde core and system showed  me required pkgs i missed  and i know you can set it as default but 4get how I did it

---

### Post by zombifier25 on 2012-08-22
> **JRV said:**
> It can be done, but it gets messy. As pointed out above.
It would be best to install each in a seperate partition and multi-boot.

But to answer your question:```

sudo apt-get install kubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop

```

If you just want the environment and not the apps that come with it:
```
sudo apt-get install plasma-desktop
sudo apt-get install xfce4
sudo apt-get install lxde-core
```

---

### Post by mzaam on 2012-08-22
> **Frogs Hair said:**
>  I have tried all the environments listed plus E17 , but only one at a time. 

if u want to try full E17 try add this PPA to your repo
```
sudo add-apt-repository **ppa:hannes-janetzek/enlightenment-svn**
```
it will give you more E17 module than ubuntu repo.

or you can add* "deb* **packages.bodhilinux.com/bodhi **precise stable" to your repo list, it will also add more fresh packages to your list

---

### Post by Random20210831 on 2012-08-22
KDE, Xfce and LXDE work well on Ubuntu, but if you want to have a full KDE, Xfce or LXDE experience better istall Kubuntu, Xubuntu and Lubuntu. Only Gnome 3 works best on Ubuntu. You can get all desktop environments from the Ubuntu Software Center.

---

### Post by vasilbelarus on 2012-08-22
For gnome3 use next comand:
```
sudo apt-get install gnome-shell
```

---

### Post by EdforUB on 2013-02-17
The system boots showing Xubuntu 12.10.  Then the Ubuntu screen appears, but no  log in features show.  However, BleachBit opens.  Then a dialog asks for entry  of password for keyring 'default' to unlock.   There appears an alert message  regarding a crash report that " an application has crashed".  Among the numerous  additional details the following have been noted:
1) Ubuntu has experienced  an internal error
2) Executable Path: /usr/share/apport/apport  checkresume
3)Package linux-image-3.5.0-24-generic3.5.0-24.37
4) Problem  Type: Kernel Oops
6) Failurew Suspend/resume

I would be most grateful for your kind help. After booting from options in the Boot Device Menu, the Desk top Environment shows the wallpaper only  without any icons nor the Applications Menu, which usually appears along the  left of the screen. There is no notification tray with icons to  download available software updates nor icons regarding notification of crashed programs. All that is visible  after booting is the desktop wallpaper with none of the Desk top icons. I have  tried to access the CLI terminal with Ctrl+Alt+T hotkeys but there is no  response. Likewise no command prompt console is available, having unsuccessfully  tried Ctrl+Alt+F1 hotkeys.
Kindly help and advise.  Your kind help and advice  are most appreciated to help me with this problem.
Best regards

---

