---
title: "Location of thunar user settings"
date: 2009-08-25
forum: Desktop Environments
---

### Post by ugm6hr on 2009-08-25
I use Xfce on my laptop and netbook, and would like to be able to copy my settings from one to the other, specifically with regard to the "Custom Actions" without having to manually re-enter them from the GUI.

According to [http://thunar.xfce.org/pwiki/documentation/faq](http://thunar.xfce.org/pwiki/documentation/faq)

> Thunar stores the user configurable preferences (and hidden settings) in an .ini file, which is located at $XDG_CONFIG_HOME/Thunar/thunarrc and can be examined using a text editor. See docs/README.thunarrc for an overview of the various preferences. 

Where is Ubuntu's xfce4 XDG_CONFIG_HOME located?  Or if it is a non-standard install, where can I find the text file to copy across?

---

### Post by kerry_s on 2009-08-25
did you look in ~/.config ?

---

### Post by prshah on 2009-08-25
> **ugm6hr said:**
> where can I find the text file to copy across?

According to the linked content, it is a .ini file, but the filename itself is not a .ini, so maybe you need to search with```
locate thunarrc
#or
find ~ -iname thunarrc*
```

---

### Post by VCoolio on 2009-08-25
With thunar 1.0.0 installed on ubuntu 9.04 custom actions are in:
/home/<user>/.config/Thunar/uca.xml

I wouldn't know why this would be different on xfce, so I hope it helps.

---

