---
title: "lightdm wallpaper question"
date: 2013-08-19
forum: Desktop Environments
---

### Post by r_avital on 2013-08-19
Hello all,

I've successfully installed the MATE desktop 1.6 on Ubuntu 13.04 64Bit.  When I log on to my system, I have only two sessions to choose from:  Ubuntu, and Mate (Ubuntu includes the Unity launcher).  All is well, including Compiz (pleasantly surprised to find out it maintains separate settings for each session).

I have the Variety wallpaper changer running in both sessions, all running well.  Tiny glich:

1. I'm logged in to Ubuntu/Unity, log out, and the login screen has the last active wallpaper as a background, as expected, since that's how I set up Variety to work.
2. Log in to MATE.  Log out.  Now the login screen has the default Ubuntu ugly purple/orange smear.
3. Log in again, to Ubuntu/Unity.  Log out.  Now the login screen has, again, the last active wallpaper as background.
4. Repeat #2 above, same result.

It appears the last active wallpaper is preserved as login-screen wallpaper only after coming out of an Ubuntu/Unity session, but not after coming out of a MATE session.

For what it's worth, I know exactly how Variety saves that last active wallpaper - in the /Home/Pictures folder, as something like "copied-variety-etc-etc-xxx" where xxx is in fact a 32-character hex value.

I also found out, that MATE also saves the last active wallpaper, in /home/.cache/mate/background, but it doesn't use it for the login screen where I log out of a MATE session.

If I could enter a setting in lightdm.conf to put a specific wallpaper on the lightdm greeter, that would be peachy.  I don't need it to cycle, I could disable that feature in Variety.  

Note however, that when I lock the screen, whether under gnome or mate, THAT login screen gets the last active wallpaper ok.  But not the lightdm greeter when logging out of mate.

I should note, **I've already tried the lightdm wiki,** it's either out of date or talking about a different flavor of Ubuntu (Lubuntu perhaps?), because it refers to /etc/lightdm/lightdm-gtk-greeter.conf which doesn't exist on my system (here it's /etc/lightdm/lightdm.conf) and the setting they give simply had no effect.

Any ideas?  No offense to anyone, but that orange-purple-the-sixties-just-called atrocity is making my eyes bleed.

TIA :)

---

### Post by r_avital on 2013-08-19
Nevermind, solved the problem.

/etc/lightdm/lightdm.conf, added the following in the [SeatDefaults] section:```
[SeatDefaults]

session-cleanup-script=/etc/lightdm/setuploginwall.sh
```

The script will execute with root privileges.  So I created a script:
```
#!/bin/bash
cp /home/xyzyaddayadda/Pictures/variety-copied-wallpaper-*.* /usr/share/backgrounds/warty-final-ubuntu.png
```

The change will take effect only after lightdm is restarted.

Note, that even though the original image is a *.jpg, renaming it to a *.png still works (AFAIK, they're the same format but jpg=proprietary, png=open).

Best of all, I'll never again see that orange/purple ugliness!

---

