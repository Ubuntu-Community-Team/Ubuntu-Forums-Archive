---
title: "Macbuntu Help!!!"
date: 2010-12-31
forum: Desktop Environments
---

### Post by chenry on 2010-12-31
I installed Macbuntu from the lifehacker post [here]("http://lifehacker.com/5665765/macbuntu-makes-your-linux-desktop-look-like-mac-os-x").  However, I decided that I don't want the theme.  It says to just replace ./install.sh with ./uninstall.sh instead.  I tried that in terminal and here is what happened:
```
connor@connor-Dell-DE051:~$ wget https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz -O /tmp/Macbuntu-10.10.tar.gz tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp cd /tmp/Macbuntu-10.10/ ./uninstall.sh
wget: invalid option -- 'C'
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
connor@connor-Dell-DE051:~$
```I really want to uninstall this theme.  All help is greatly appreciated. Thanks!

---

### Post by chenry on 2010-12-31
Okay so I rebooted my computer and tried to uninstall again.  Here is what showed up at the end:

---

### Post by chenry on 2010-12-31
```
Checking currently installed version of Macbuntu-10.10...
Failed. The script is not able to determine what version is currently installed
Exiting...
connor@connor-Dell-DE051:/tmp/Macbuntu-10.10$
```

---

### Post by Kalimol on 2010-12-31
I wonder why the LifeHacker folks had you download to a temp directory. It'd be easier to save it to home in case you needed to uninstall.

Anyway, "installing" isn't exactly what it's doing - there's no "Macbuntu" application installed on your machine. The script installs some extras and tweaks those, along with your theme, to imitate Mac OSX as much as possible. It doesn't save your original settings, and the uninstall script will revert your desktop to default settings. If the "uninstall" script won't work, you can change everything back manually by loading your Compiz Config Settings Manager (in Preferences), your theme manager (right click the desktop and select the "Appearance" tab), Panel properties (right-click an empty space on the panel), and Docky (which you can uninstall using sudo apt-get purge docky, but really, why would you want to?)

---

