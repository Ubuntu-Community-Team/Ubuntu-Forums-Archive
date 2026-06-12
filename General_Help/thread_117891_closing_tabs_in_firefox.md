---
title: "closing tabs in firefox"
date: 2006-01-15
forum: General Help
---

### Post by aznmodder on 2006-01-15
i remember in windows i could close tabs by using the middle click button on my mouse...for some reason it doesnt work in ubuntu..any ideas?

---

### Post by amohanty on 2006-01-15
Does your mouse emulate 3 buttons?
If you look in your /etc/X11/xorg .conf does your mouse section look kind of like this... some strings may be different:
> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        **Option          "Emulate3Buttons"       "true"**
        Option          "ZAxisMapping"          "4 5"
EndSection


The section in bold could be the solution. For some reason without that the middle click close tab did not work for me, even though middle click pase worked fine.

HTH
AM

---

### Post by pertti on 2006-01-15
[QUOTE=aznmodder]i remember in windows i could close tabs by using the middle click button on my mouse...for some reason it doesnt work in ubuntu..any ideas?[/QUOTE]

I have the same problem with Firefox 1.5, which I installed manually using the binaries from mozilla.com, but the version that cames with Ubuntu works perfectly. If you're using Firefox 1.5 you should take a look at these extensions: [Tabbrowser Preferences]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Tabbed%20Browsing&numpg=10&id=158"), [Tab Mix Plus]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Tabbed%20Browsing&numpg=10&id=1122").

---

### Post by aznmodder on 2006-01-15
[QUOTE=pertti]I have the same problem with Firefox 1.5, which I installed manually using the binaries from mozilla.com, but the version that cames with Ubuntu works perfectly. If you're using Firefox 1.5 you should take a look at these extensions: [Tabbrowser Preferences]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Tabbed%20Browsing&numpg=10&id=158"), [Tab Mix Plus]("https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Tabbed%20Browsing&numpg=10&id=1122").[/QUOTE]

that solved it...thanks

---

### Post by TomPreuss on 2006-01-16
[QUOTE=aznmodder]i remember in windows i could close tabs by using the middle click button on my mouse...for some reason it doesnt work in ubuntu..any ideas?[/QUOTE]
The exact fix for this one is to set [middlemouse.contentLoadURL](http://kb.mozillazine.org/Middlemouse.contentLoadURL) to false in about:config.

---

### Post by LycoLoco on 2006-02-19
> The exact fix for this one is to set middlemouse.contentLoadURL to false in about:config. That worked for me!

---

