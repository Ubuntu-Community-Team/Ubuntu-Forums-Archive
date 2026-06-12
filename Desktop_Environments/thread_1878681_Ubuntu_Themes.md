---
title: "Ubuntu Themes"
date: 2011-11-10
forum: Desktop Environments
---

### Post by zainlodhi on 2011-11-10
How can I change Ubuntu themes in my Ubuntu 11.10 (Oneiric Ocelot) ? I have no past experience of changing themes in Ubuntu so guys  please tell me the way to change themes and to get stunning themes? looking for the replies?

---

### Post by BillyBoa on 2011-11-10
You should try the gnome tweak
```
sudo apt-get install gnome-tweak-tool
```
after the installation you search it as advanced tools

---

### Post by BillyBoa on 2011-11-10
To add new themes you have to download them usually from 
[http://art.gnome.org/themes](http://art.gnome.org/themes)
and after that you copy them to this directory
/usr/share/themes
Of course to do that you need to do it through extended privileges
```
sudo nautilus
```

---

### Post by BillyBoa on 2011-11-10
For the icons you download them, usually from
[http://art.gnome.org/themes](http://art.gnome.org/themes)
and just copy them to the folder ./icons in /home
If it's not existing you have to create the folder.

---

### Post by zainlodhi on 2011-11-10
> **BillyBoa said:**
> You should try the gnome tweak
```
sudo apt-get install gnome-tweak-tool
```after the installation you search it as advanced tools

I installed gnome tweak but Shell extension option is not working even i installed the user-theme-extension using terminal. "Shell theme" button in 'theme' menu in 'gnome tweak' is still freezed

---

### Post by BillyBoa on 2011-11-10
> **zainlodhi said:**
> I installed gnome tweak but Shell extension option is not working even i installed the user-theme-extension using terminal. "Shell theme" button in 'theme' menu in 'gnome tweak' is still freezed
Those 2 options are not working so far. But you can change the theme using the other Theme options.

---

### Post by Copper Bezel on 2011-11-10
Should note that there are also some nice GTK and Shell themes at [Gnome Look]("http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=6f9d3cdf14bd4432edd966651ae3bee4") and [Deviantart]("http://browse.deviantart.com/?qh=&section=&q=gtk3").

If you don't want to muddle with elevated privileges, you can also copy the themes to the hidden .themes directory in your home folder, but they won't be applied to windows run by root. That way, you can try a few of them out, then copy the ones you want to keep to /usr/share/themes.

My shell theme button works, but it was broken for a while. I ended up uninstalling and reinstalling my extensions (as well as the gnome-shell-extensions-common base) and it seemed to fix it.

---

