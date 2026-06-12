---
title: "problems with keyboard using kubuntu 7.04"
date: 2007-05-09
forum: Desktop Environments
---

### Post by rullator on 2007-05-09
hey there,

i have a strange problem with my keyboard (PS2). last week i installed kubuntu 7.04 and since two days i have the problem that some of my keys do not work anymore. here are the keys, which i cannot type:
§ @ | ß ~ ä ö ü ° \ { } [ ] 

my xorg.conf looks like this:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection 
```

locale says:

```
LANG=de_DE.UTF-8
LANGUAGE=de_DE:de:en_GB:en
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC="de_DE.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
LC_MESSAGES="de_DE.UTF-8"
LC_PAPER="de_DE.UTF-8"
LC_NAME="de_DE.UTF-8"
LC_ADDRESS="de_DE.UTF-8"
LC_TELEPHONE="de_DE.UTF-8"
LC_MEASUREMENT="de_DE.UTF-8"
LC_IDENTIFICATION="de_DE.UTF-8"
LC_ALL=


```

the problem not only occures in multi user mode, also in the single user mode. so it does not seem to be caused by KDE. i also tried to use another keyboard (USB), which did not help. 
when logging in to the pc from another via ssh, i can type all characters without any problems. so it seems to be a local problem. also in windows (via vmware), the problem does not occure.

where else can i configure the keyboard-settings in (k)ubuntu?

does anyone can help me somehow? any hints? want some more information?

thanks.

---

### Post by JohanL on 2007-05-09
Not sure about KDE since I use gnome and Fluxbox, but my xorg looks like this. I think I edited this manually since I had the same problem as you.

Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "AutoRepeat" "500 30"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
    Option         "XkbVariant" "nodeadkeys"
    Option         "CoreKeyboard"
EndSection

The XkbLayout option sets the locale

---

### Post by rullator on 2007-05-10
i also tried that before, but it did not help, since it does not seem to be a problem of KDE..
where else can i adapt the keyboard settings? so that these settings affect the bash (single user mode)?

---

### Post by Memory.Dump on 2007-05-10
just looking at the keys that aren't working....could it be your layout it might be for the layout you have selected the locale for those keys don't have the options...or at least not on those keys

---

### Post by james.wilde on 2007-05-11
I have exactly the reverse problem, Rullator.  I get missing Alt-Gr symbols when I log in to my workbox via vpn (but get them on the local machine).  This is new under Feisty.  Under Edgy it was exactly the reverse over the vpn.

I discovered that I did not have language support enabled - installed and enabled it, without success - I changed various Keyboard Layout options in respect of level 3 - no effect - and now I'll try Johan L's suggestion for the extra nodeadkey option in xorg.conf.  I'll report back when I've had a chance to reboot.

Hope you find a solution, because that could point me in the right direction also.

//James

---

### Post by rullator on 2007-05-21
after reinstalling, i checked my keyboard malfunction after installing some additional packages and found out, which one causes the malfunction. it is a non-public debian package. i sent them a bug report. even removing of the suspicious package, didn't remove the malfunction. really strange...
so i don't know, what exactly was the reason, maybe they know.

---

