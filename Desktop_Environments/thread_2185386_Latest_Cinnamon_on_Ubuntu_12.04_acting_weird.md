---
title: "Latest Cinnamon on Ubuntu 12.04 acting weird"
date: 2013-11-02
forum: Desktop Environments
---

### Post by uzumakifahim on 2013-11-02
Hi everyone,
I've installed latest cinnamon on Ubuntu 12.04 by adding official ppa ([http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu)). The installation is successful, but it is acting weird. First of all touch pad is malfunctioning, but in unity it works perfectly. Moreover, most of the icons are missing. System setting window is completely blank.

Please take a look of the screenshot attached. 

Please give your valuable comments to solve this problem.

Thanks in advance.

---

### Post by Frogs Hair on 2013-11-02
The latest Cinnamon is it own desktop environment and not a modified Gnome Shell like previous versions  , so  be sure to use the Cinnamon system settings . The Gnome Tweak Tool will no longer work for changing themes or icons in 2.0.

---

### Post by kracheck on 2013-11-02
Same problem here running Ubuntu 12.04. As for the system settings window that is blank there is a workaround :
[https://github.com/linuxmint/Cinnamon/commit/c4eac2e3ab88a2264faedf09f026432522bbe18e](https://github.com/linuxmint/Cinnamon/commit/c4eac2e3ab88a2264faedf09f026432522bbe18e)
You will have to edit the file and add "widget.set_item_width(105)" after line 325. I haven't found a solution for the missing icons.

---

### Post by uzumakifahim on 2013-11-02
Thanks to all for your reply.

@Frogs Hair, I know that, latest Cinnamon is no more dependent on Gnome. I'm using "System Settings" from the "Menu", I think it's system setting panel for Cinnamon, not Gnome Tweak Tool. Now, the icons in "System Settings" window is back after doing the change according @kracheck, but still categories and some other icons are missing are missing. Moreover, touch pad is still not working. :(

@kracheck, thanks for your help, according to your instruction "System Settings" icons are back now, but still facing other problems along with touch pad. :(

---

### Post by uzumakifahim on 2013-11-02
Oh!!! Touch pad problem is solved!!! It was disabled by default. Now the only problem is missing icons.

---

### Post by Frogs Hair on 2013-11-02
> I know that, latest Cinnamon is no more dependent on Gnome. I'm using "System Settings" from the "Menu"

Just checking because the windows look similar and there were others that were not aware of the changes and having difficulty with theme and icon changes.

---

### Post by uzumakifahim on 2013-11-02
@Frogs Hair, you are right my theme looks alike Gnome, it was activated by default since cinnamon installation.

---

### Post by Frogs Hair on 2013-11-02
In case you didn't find the theme settings check Themes > Other Settings in Cinnamon 2.0 for icons and GTK settings.

---

### Post by uzumakifahim on 2013-11-04
I have no problem with themes. I've downloaded new themes and using successfully, but still facing the missing icons problem on menu, just as the screenshot. :(

---

### Post by kracheck on 2013-11-05
Missing icons problem...anyone ?

---

### Post by SuperFreak on 2013-11-05
I had problems with missing desktop icons. I uninstalled Cinnamon and reinstalled it and they came back

I used ```
sudo apt-get remove cinnamon
```in terminal to remove Cinnamon

---

### Post by uzumakifahim on 2013-11-06
> **SuperFreak said:**
> I had problems with missing desktop icons. I uninstalled Cinnamon and reinstalled it and they came back

I used ```
sudo apt-get remove cinnamon
```in terminal to remove Cinnamon


I've done that, but still facing same problem.

---

### Post by Frogs Hair on 2013-11-06
Make sure the file manger is set to handle the desktop in the gnome-tweak-tool > desktop.

---

### Post by galan55 on 2013-11-18
Just to save anyone else the pain I went through this weekend. Was happily running Ubuntu 12.04 with Cinnamon 1.8 up until last week. Foolishly upgraded to Cinnamon 2.0, and immediately was unable to tap-to-click using Synaptic Touchpad on my aging Lenovo T61, along with other performance issues. When switching back to Unity desktop, the touchpad worked fine. I could not find any way to go back to Cinnamon 1.8 (poor backup methods), and the fixes I tried (based on forum suggestions) to repair the Synaptic problem using synclient ultimately led to black-screen of death on bootup. Ultimately, I ended up installing Mint 15 with Cinnamon 1.8, which is working noticeably faster than my Precise with 1.8. My suggestion to anyone running 12.04 is NOT to upgrade Cinnamon desktop to 2.0 until it is proven to be stable on 12.04, or there is a reliable fallback to 1.8.

---

### Post by funkoolow on 2014-01-09
i've solved the missing icons problem with

```
sudo apt-get install gnome-icon-theme-full
```

---

### Post by buzzingrobot on 2014-01-10
The Mint backport of Cinnamon to Mint 13 -- based on 12.04 -- was released a week or so ago.  I don't know if that's the case for the version at the PPA, but perhaps it might be worth a look.

Sometimes missing icons are, in fact, just not there.  I.e., an incomplete icon set is installed.

---

### Post by bittmann on 2014-02-02
> **funkoolow said:**
> i've solved the missing icons problem with

```
sudo apt-get install gnome-icon-theme-full
```

Worked for me as well.

---

