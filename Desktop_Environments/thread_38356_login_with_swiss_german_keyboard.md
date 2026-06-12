---
title: "login with swiss german keyboard"
date: 2005-05-31
forum: Desktop Environments
---

### Post by pinguino_italico on 2005-05-31
Hi Everybody,

I just installed Kubuntu 5.04 and I'm slowly slowly "commissioning" it,
installing packages and personalizing it.

I still have a small problem with the KDE login and the swiss keyboard.

Unfortunately I have to use a swiss german keyboard where the keys "y" and
"z" are just in the opposite positions of the "rest-of-the-world" keyboards.

I chose and tested the correct keyboard layout during the installation and
then of course I also changed the locale settings in the KDE control panel and
everything works fine except for the login: apparently the correct keyboard
layout is loaded only after the login and I'm smart enough to have a password
with "z" characters  ](*,)  Therefore everytime I login I have to force myself to
type y instead of z!

Is there any configuration file where I can force the keyboard to be swiss
before the login?

Thank you in advance for your help.

---

### Post by pinguino_italico on 2005-06-03
After digging around for a few days I found the solution and I hope it can
help somebody else.

For some unknown reason the keyboard layout in the file 
/etc/X11/xorg.conf was set to italian (maybe because I set italian as my
language during the installation? I know, I'm complicated... I have to use a 
swiss german keyboard even though I am italian and my OS is set to
italian)

Then in the file there's the following:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de_CH"
EndSection

I changed the option XkbLayout from "it" to "de_CH" and now the login
works fine. 
 \\:D/

---

