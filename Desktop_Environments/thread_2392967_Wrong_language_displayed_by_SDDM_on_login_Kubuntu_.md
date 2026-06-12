---
title: "Wrong language displayed by SDDM on login Kubuntu 18.04"
date: 2018-05-28
forum: Desktop Environments
---

### Post by linesma on 2018-05-28
I used Ubuntu for many years, and switched to another distro when they switched to Unity. Because I have always wanted to switch back to Ubuntu at some point, I give the new releases, especially the LTS, a spin. After hearing good things about KDE Plasma, I decided to give Kubuntu 18.04 a spin. For the most part, I was impressed. For the first time in a while, I did not have to run the Live environment with +nomodset argument. However, it seems that there is an issue with the "Login" screen. The language it displays does not match up with what is set in the regional settings.

I am an American Expat who lives in Thailand. Changing the regional settings from the installed defaults to something I am familiar with is part and parcel with installing and using an O/S for me. No matter what regional or language setting I changed on Kubuntu, it would always display the date and time in the Thai language and format on the login screen. Every possible setting in the "System Settings-Regional Settings-Language" and "System Settings-Regional Settings-Formats" is set to "American English". I have found with other distros, that these settings change what the "Login" screen displays. Unfortunately, this seems to not be the case with Kubuntu. I have ran ```
sudo dpkg-reconfigure locales
``` in the terminal and made sure the en_US.UTF-8 was chosen. Even after running that command, there was no change. The keyboard IS set to American QWERTY and I can login just fine. It is just the Date/ Time on the "Login" screen being displayed in the wrong language.

The only solution I found was to edit ```
/etc/default/locale
``` and change all entries from th_TH.UTF-8 to en_US.UTF-8. While I personally I do not mind having to dig into and manually edit some config files, the "average user" maybe put off by this. Because of this, I am asking two questions: 

1. Is there a way to have this all set-up properly during the install?
2. If not during the install, what does the user need to do to have the changes in "System Settings" to actually be applied?

Thank you all for your time and help with this matter.

---

