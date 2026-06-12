---
title: "Ubuntuzilla firefox icons not showing in window list in Ubuntu 23.04"
date: 2023-06-11
forum: Desktop Environments
---

### Post by plenaerts on 2023-06-11
Hi, I use the packaged firefox mozilla build from Ubuntuzilla on Ubuntu 23.04. I noticed that the launcher in the dock shows the firefox icon correctly, but the icon in the dock when the application is running and the icon in the window switcher are missing.

I posted a question with screenshots to Ubuntuzilla's support here: [https://sourceforge.net/p/ubuntuzilla/discussion/723516/thread/21d86db8f7/](https://sourceforge.net/p/ubuntuzilla/discussion/723516/thread/21d86db8f7/) but the packager doesn't use regular ubuntu, community seems to small to help.

I tried to put the icon png in some locations, in different sizes, but nothing has worked so far. I used this page as source of info: [https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)

This is the relevant part of the package (I think):

```

&#10140;  ~ dpkg -L firefox-mozilla-build| grep png                        
/opt/firefox/browser/chrome/icons/default/default128.png
/opt/firefox/browser/chrome/icons/default/default16.png
/opt/firefox/browser/chrome/icons/default/default32.png
/opt/firefox/browser/chrome/icons/default/default48.png
/opt/firefox/browser/chrome/icons/default/default64.png
/opt/firefox/icons/updater.png
/usr/share/pixmaps/firefox-mozilla-build.png
&#10140;  ~ dpkg -L firefox-mozilla-build| grep desktop                    
/usr/share/applications/firefox-mozilla-build.desktop
&#10140;  ~ grep Icon /usr/share/applications/firefox-mozilla-build.desktop
Icon=firefox-mozilla-build

```

Comparing that to the default firefox snap doesn't inspire me either...
```

&#10140;  ~ grep Icon /snap/firefox/current/firefox.desktop
Icon=/default256.png
&#10140;  ~ ls /snap/firefox/current/*.png   
/snap/firefox/current/default256.png

```

Does anyone have a clue what may be wrong? What other info should I provide to investigate this?

---

### Post by plenaerts on 2023-07-03
Based on IRC conversation I checked for old lingering desktop files and  there is no memory shortage. Also changed the Icon= line to contain the  full path including .png extension. Also ran ```sudo  gtk-update-icon-cache`` command. Logged off and back on after every  change.

```

&#10140;  ~ free -h
               total        used        free      shared  buff/cache   available
Mem:            14Gi       1,4Gi        11Gi        39Mi       1,7Gi        13Gi
Swap:          4,0Gi          0B       4,0Gi
&#10140;  ~ grep firefox ~/.local/**/*.desktop -R                                               
/home/user/.local/share/applications/userapp-Firefox-MTQM71.desktop:Exec=/opt/firefox/firefox-bin %u
/home/user/.local/share/xfce4/helpers/custom-WebBrowser.desktop:X-XFCE-CommandsWithParameter=/usr/bin/firefox-developer-edition  "%s"
/home/user/.local/share/xfce4/helpers/custom-WebBrowser.desktop:Icon=firefox-developer-edition
/home/user/.local/share/xfce4/helpers/custom-WebBrowser.desktop:Name=firefox-developer-edition
/home/user/.local/share/xfce4/helpers/custom-WebBrowser.desktop:X-XFCE-Commands=/usr/bin/firefox-developer-edition
&#10140;  ~ grep firefox /usr/share/applications/**/*.desktop -R
/usr/share/applications/firefox-mozilla-build.desktop:Exec=firefox %u
/usr/share/applications/firefox-mozilla-build.desktop:Icon=/usr/share/pixmaps/firefox-mozilla-build.png
&#10140;  ~ 

```

---

