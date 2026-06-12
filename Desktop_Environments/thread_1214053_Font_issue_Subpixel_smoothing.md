---
title: "Font issue: Subpixel smoothing"
date: 2009-07-15
forum: Desktop Environments
---

### Post by Aroll605 on 2009-07-15
Hello. 

Since Firefox 3.5 was not available from Ubuntu Update, I decided to install it manually in /opt/firefox-3.5
Unfortunately, it didn't have the proper font configuration (it didn't follow GNOME settings for subpixel smoothing) so I looked for a fix and found this one:

```

sudo rm /etc/fonts/conf.d/10-hinting-slight.conf
sudo rm /etc/fonts/conf.d/10-no-sub-pixel.conf
sudo ln -s /etc/fonts/conf.avail/10-hinting-medium.conf /etc/fonts/conf.d/.
sudo ln -s /etc/fonts/conf.avail/10-sub-pixel-rgb.conf /etc/fonts/conf.d/.
sudo dpkg-reconfigure fontconfig

```

After I restarted the computer, it set the anti-aliasing options for FireFox 3.5 to "Best Shapes" (by the look of it) and, that's where the real problem comes, for QT apps. So now all Qt apps (Skype, VirtualBox, Lyx, etc, etc) have different fonts from GNOME.

Can anyone recommend a fix for this? Is there any way to reset the font config to default (as on ubuntu install)?

Thank you in advance.

---

### Post by CatKiller on 2009-07-15
I've not fiddled with fonts very much, so I can't help you with the specific issue that you're experiencing, but

> **Aroll605 said:**
>  Since Firefox 3.5 was not available from Ubuntu Update

firefox-3.5 **is** in the Jaunty repositories. In the Universe repository, specifically.

For Jaunty it's branded as Shiretoko (Firefox 3.5's development codename) so that you can install it alongside Firefox 3.0 without getting horribly confused.

Perhaps installing the version from the repositories rather than manually installing it would avoid your configuration problem?

Re-installing whichever package created those font configuration files might restore them to how they were before you fiddled with them.

---

### Post by kpkeerthi on 2009-07-16
Installed [FF-3.5 from ubuntu repository ]("http://packages.ubuntu.com/jaunty/firefox-3.5"). The font was not any better than Shiretoko installed from mozilla daily-build PPA.

Then I found the same (ugly) font fixes somewhere in the forum and thought I'd be better off with FF3.0.11. 

> 
sudo rm /etc/fonts/conf.d/10-hinting-slight.conf
sudo rm /etc/fonts/conf.d/10-no-sub-pixel.conf
sudo ln -s /etc/fonts/conf.avail/10-hinting-medium.conf /etc/fonts/conf.d/.
sudo ln -s /etc/fonts/conf.avail/10-sub-pixel-rgb.conf /etc/fonts/conf.d/.
sudo dpkg-reconfigure fontconfig


---

