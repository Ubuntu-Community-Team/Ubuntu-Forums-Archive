---
title: "Dell Laptop  E1505 Screen Brightness control"
date: 2007-12-25
forum: Dell  Ubuntu Support
---

### Post by LarryJ2 on 2007-12-25
Somehow I missed this.  If you have KDE 3.5.8 installed, you either have installed  or can install Power Manager 0.8.0 by jriddel.   When this is running, there is a battery icon in the lower right kicker panel.  Left Click on this icon will pop a dialog form in which you can set the screen brightness for when your laptop is  on battery power and a different brightness setting  when you are plugged into the  AC mains.

Works perfectly on my Dell Inspirion 1505 Laptop with  Gutsy 7.10 installed from Kubuntu CD.

If your kicker panel is lacking the battery cell icon,  try installing  **kde-guidance-powermanager **  It's in the KDE section. **sudo apt-get install kde-guidance-powermanager**      After installation, a reboot is required. More info from here Homepage: [http://www.simonzone.com/software/guidance](http://www.simonzone.com/software/guidance)

If you want brightness control from the key combination  Fn+Up Fn+Down,  try **gnome-power-manager**.  That puts yet another battery icon in the lower right kickerpanel,  but after reboot  Fn+CursorPadUp/Down key controls brightness.

---

### Post by biodiesel-bri on 2008-01-09
Thanks for posting this.  For whatever reason, KDE decided to dim my screen last night.  kde-guidance-manager fixed it.

---

