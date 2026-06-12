---
title: "Keyboard issues,"
date: 2006-08-05
forum: Desktop Environments
---

### Post by pormogo on 2006-08-05
Recently I've been experiancing some keyboard issues on my computer. When I turn the numlock function on I am unable to use the */-+ keys on the 10 key :( The following is the keyboard section of my xorg.config 
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

```

I'm actually kinda lost as to why my keyboard is acting up like that. oh the right hand alt and cntrl keys not functioning properly either (however they are bound to other things). 

Another problem I have run into is that my VLC media players "Always on top" option does not work. I think this might have something to do with compiz, but I haven't been able to find anything about it googling around so I figured I would ask here. Any help is appreciated, thanks a lot in advance.

EDIT: I just thought I should add I am using the coordless keyboard included with the MX700 coordless duo.

[IMG]http://http://images.amazon.com/images/P/B000095ISG.01-A3PL85D94NQDOF._AA220_SCLZZZZZZZ_.jpg[/IMG]

---

### Post by pormogo on 2006-08-05
AHA fixed that by changing to a generic 104key in gnome, but I still can't get my VLC to always stay on top of my other windows :(

---

### Post by pormogo on 2006-08-05
hahahah maybe I should use the command to send the window to the top from the window manager rather then from the application ](*,)

---

