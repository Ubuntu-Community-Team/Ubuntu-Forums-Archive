---
title: "No &quot;Custom&quot; option in Visual Effects"
date: 2009-04-06
forum: Desktop Environments
---

### Post by Volt9000 on 2009-04-06
I've seen in several threads that if you go to System > Preferences > Appearance and into the Visual Effects tab there should be four options: None, Normal, Extra and Custom. Well I only have the first three, and no "Custom" anywhere.

I have Compiz installed and when I changed from the default settings and go into the Visual Effects tab, none of the radio buttons have a dot in them. So I assume that "Custom" is checked, but the item itself is invisible??? :confused:

Or am I missing something obvious? This is the second install that's done this.

---

### Post by UbuntuNerd on 2009-04-06
do you have  "compiz configuration manager" install if not do this in a terminal:
```
 sudo apt-get install compiz config-settings-manager 
```
only after that you will get the custom option

---

### Post by drs305 on 2009-04-06
Volt9000,

I have the same experience. I never can get any of the three buttons selected. There is no "Custom" option, but everything seems to work fine. 

After a few attempts at reinstalling the nvidia drivers (to get the button again) I resigned myself to the fact that everything was working and I could select any of the compiz features.

I have ccsm installed and use it daily.

---

### Post by UbuntuNerd on 2009-04-06
this is exactly what says in "The Great Desktop Effects FAQ of 2009" 
How can I get Custom to appear in the Visual Effects dialog?

    Custom only appears if the package simple-ccsm is installed. When you install simple-ccsm, a new selection will be available in Visual Effects, which allows you to customize what effects are active on your desktop. You can also customize the effects from System > Preferences > Simple CompizConfig Settings Manager.

[http://ubuntuforums.org/showthread.php?t=809695]("http://ubuntuforums.org/showthread.php?t=809695")

---

### Post by Volt9000 on 2009-04-06
UbuntuNerd, thanks a million, that certainly did the trick! :D

---

