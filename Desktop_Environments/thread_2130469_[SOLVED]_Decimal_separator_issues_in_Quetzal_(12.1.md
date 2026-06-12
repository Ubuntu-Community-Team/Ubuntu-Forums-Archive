---
title: "[SOLVED] Decimal separator issues in Quetzal (12.10, Unity Ubuntu)"
date: 2013-03-29
forum: Desktop Environments
---

### Post by pietrucha23 on 2013-03-29
I have US English as the default language of the system and also of my user account, but I've set a Polish keyboard layout exclusively (I'm writing in both and standard English alphabet is just a subset of the Polish alphabet, but English is missing like 20% of Polish letters: &#261;&#263;&#281;&#322;&#324;ó&#378;&#380;). When I'm using Numerical Keyboard and press decimal separator (little 'Del' key) I get a coma (,) instead of a dot (.). The dot is a decimal separator in English, coma is used for this in Polish. That happens in native GNOME 3 apps (e.g. Gedit, Empathy), Chromium, Thunderbird, Firefox, Mendeley but NOT in LibreOffice (if I remember correct, LibreOffice has it's own setup of this feature).

I suspect it is keyboard setup problem, as it is the only non-English thing set in my system. In KDE you can change decimal separator arbitrary. 
**How one can arbitrary change decimal separator in Unity flavored Ubuntu?**

Just in case my locale:
```
~$ locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_US.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_ALL=
```

A bit on the side. When using Kubuntu derivative distro I had some issues with locale too. Some apps used my user settings to account for the language they displayed (KDE native apps), some other (Chromium, Thunderbird) used the system settings. if you set them the same, you don't notice that, but when they are different you have a bad time.

---

### Post by Krytarik on 2013-03-29
Set the option "System Settings -> Keyboard Layout -> Options -> Numeric keypad delete key behaviour" to "Four-level key with dot". Also, choosing that, as opposed to the "Legacy" one also offered there, gives you the additional option to also type the Comma if you want to, by holding down the AltGr key on pressing it.

Regards.

---

### Post by pietrucha23 on 2013-03-30
Well, I was there in that menu. Only it sounded to me a bit enigmatic to recognize a link with decimal separator.Works! Cheers!

---

