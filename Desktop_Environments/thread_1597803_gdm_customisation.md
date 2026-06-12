---
title: "gdm customisation"
date: 2010-10-15
forum: Desktop Environments
---

### Post by slumbergod on 2010-10-15
After what has to be the smoothest install of xubuntu ever with maverick, I have set about setting my machine up the way I like it.

What I seem completely unable to do is to change anything to do with the gdm login screen. I absolutely HATE the maverick xubuntu login -- the wallpaper is so bright it burns my retinas and the icon for the bloated pig corpse is so tacky and unprofessional it has to go!

gdm2setup does not work. The lastest ubuntu-tweak doesn't allow changes to gdm setup in xubuntu (which I understand it normally does).

Has anyone managed to changed anything related to the login screen in xubuntu?????

---

### Post by slumbergod on 2010-10-16
An update for anyone who also gets stuck with customising the gdm login screen.

Amongst some system updates a newer version of Ubuntu-Tweak was installed and though it seemed to have the same version number it did allow me to access the login customisation options with Unlock.

Wallpaper changed without issue. I used the dark one from the last two versions of Xubuntu which is much nicer than the ghastly one they chose for Maverick.

The icon was more of an issue. In the end I had to put it in /usr/share/icons/ and "sudo chmod o+r icon-name.png" I'd assumed that when you selected the icon it was "copied" to the correct location to overwrite the original. It seems that it isn't so you can't have it in an encrypted home directory. 

Now it is all working perfectly.

---

