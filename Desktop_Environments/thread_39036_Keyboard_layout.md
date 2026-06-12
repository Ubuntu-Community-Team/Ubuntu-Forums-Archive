---
title: "Keyboard layout"
date: 2005-06-03
forum: Desktop Environments
---

### Post by xo310 on 2005-06-03
Hi this is my third question today_)
I have a turkish Q keyboard but I still have a US layout even when i change the layout in the settings.
I have been looking for a solution throught the internet for 3 hours now. tried a lot of things but none worked.
Any idea?

Second is the xfree86 in the last ubuntu release outdated. I saw 4.3 version somewhere. The one on my pc is 3.3
thanks

---

### Post by Hardi on 2005-06-03
Hy.
I have 5.03 (Hoary Hedgehog).
I hope the menu is the same.
Go to System>Preferences>Keyboard>Layouts tab
Add Turkish layout and remove any other in the list.
Then try if it worked.

---

### Post by xo310 on 2005-06-03
I tried this before several times with no success

---

### Post by Alexander Kirillov on 2005-06-03
[QUOTE=xo310]Hi this is my third question today_)
Second is the xfree86 in the last ubuntu release outdated. I saw 4.3 version somewhere. The one on my pc is 3.3
thanks[/QUOTE]
Which version of ubuntu are you using? In Hoary, they do not use xfree86 at all - instead, they use X server from X.org (it was forked from xfree86 some time ago). The version in Hoary is Xorg 6.8.2 -  which is much newer than Xfree86 4.3. 

Warty used Xfree86 4.3 

And, by the way, the latest version of XFree86 is 4.5.0, not 4.3

---

### Post by Juippisi on 2005-06-03
"sudo dpkg-reconfigure locales", find your layout, mark it and set it as default. Log out and log in and that should work. If you are using GDM/KDM/XDM, remember to set the "Language" to yours.

---

### Post by xo310 on 2005-06-03
thank you guys. Actually the only way it worked is by formatting the linux partition then reinstalling with Turkish as the default language of the desktop and all other applications which I am not used to since I have always used the english version of windows.
My version is 5.04

---

### Post by xo310 on 2005-06-03
hi Juippisi, I did what you said but still it did not work. Maybe I am doing something wrong as this is my second day with linux.
I chose my locale but how to set it as default. There was not such option

---

### Post by i-tech on 2005-06-03
did you tired to edit xorg.conf
 > Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "tr"
EndSection
 
it should be like this.

---

