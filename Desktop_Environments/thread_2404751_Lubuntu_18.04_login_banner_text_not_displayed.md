---
title: "Lubuntu 18.04 login banner text not displayed"
date: 2018-10-28
forum: Desktop Environments
---

### Post by nadrach on 2018-10-28
On upgrading to Lubuntu 18.04 (fresh install) I could not see either the date/time (RH side) or system name (LH side) in the banner on the login screen. Only the icons and the keyboard ID.
Until I viewed my screen at a narrow angle.
The text is displayed, but not in a dark font on the light colour banner as with 16.04, but in a font colour so close to the banner background colour that only a shadow effect is visible.
Nothing I have tried in configuration in the "LightDM + Greeter" settings will change the font colour.
This is not hardware related, I have it on three systems of wholly different age.
This remains with 18.04.01.
The only solution at the moment is to change from "lubuntu-default" to "lubuntu-dark-panel" as the theme.
This has a problem in that the dark banner size has no space above and below the white text, nor any spacing between the icons and their adjacent text, which does not look good typographically.
Is there any way I can fix this in a config file?
Alternatively, are there any other Greeter themes available that I can load, and if so, how? I have not been able to find any help on the configuration of this.

---

### Post by nadrach on 2018-11-08
OK, found it.
Bug [https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1689398](https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/1689398)
C'est la vie.

---

### Post by nadrach on 2018-11-08
Solution is to install another GTK theme and switch to it.
Best two I found so far for display and typography are blackbird-gtk-theme and numix-blue-gtk-theme from the lubuntu repository.
My preference is the Numix Blue theme.

---

