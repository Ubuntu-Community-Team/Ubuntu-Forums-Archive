---
title: "script to turn touchpad off/on?"
date: 2015-08-13
forum: Desktop Environments
---

### Post by siggi2 on 2015-08-13
Hi,

It is about Lubuntu 14.04.2 LTS: I am pretty new to Lubuntu. With Ubuntu 14.04 on my notebook, it is easy to turn the touchpad off/on, just using "Preferences". 

How can I do that with Lubuntu 14.04?

And my co-users on the notebook do not mean to do the synclient stuff in a terminal. They insist on something like an app-script in the menu or on the desktop. Is this possible? And if so, how, please?

Thank you,

siggi

---

### Post by v3.xx on 2015-08-14
Maybe

[http://ubuntuforums.org/showthread.php?t=2263662](http://ubuntuforums.org/showthread.php?t=2263662)

---

### Post by CantankRus on 2015-08-14
If you find two commands which turn your touchpad off and on, you can
use this toggle script.
Don't use laptops so can't test any commands.
Save as **touchpad-toggle.sh** and make executable.
```
#!/bin/sh

TOGGLE=$HOME/.toggle

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    [COLOR="#FF0000"]<Insert your 1st command>[/COLOR]
else
    rm $TOGGLE
    [COLOR="#FF0000"]<Insert your 2nd command>[/COLOR]
fi

exit 0
```

The script will toggle the running of any 2 commands.

---

### Post by siggi2 on 2015-08-14
Thank you CantankRus, works great, this is my touchpad-toggle.sh script:

```
!/bin/sh

TOGGLE=$HOME/.toggle

if [ ! -e $TOGGLE ]; then
    touch $TOGGLE
    synclient MaxTapTime=0
else
    rm $TOGGLE
    synclient  MaxTapTime=180
fi

exit 0

```

Could I get this script somehow into the menu or as an app onto the desktop?

Thanks,

siggi

P.S.And thanks to v3.xx for directing me to the synclient stuff.

---

### Post by CantankRus on 2015-08-14
Create a .desktop file in **~/.local/share/applications**
Check the ~/.local/share/applications directory exists...
```
mkdir ~/.local/share/applications
```

Then create the .desktop file...
```
leafpad ~/.local/share/applications/touch-toggle.desktop
```
Copy and paste in the folllowing...
```
[Desktop Entry]
Name=Touch Toggle
Comment=Toggle touchpad off/on
Exec=[COLOR="#FF0000"]/path/to/touchpad-toggle.sh[/COLOR]
Icon=keyboard
Terminal=false
Type=Application
Categories=Settings;HardwareSettings;
```
Edit using [COLOR="#FF0000"]your path to touchpad-toggle.sh[/COLOR] and save.

Should show under "Preferences" in Applications menu.
Copy the **~/.local/share/applications/touch-toggle.desktop** file to your desktop
if you want an icon on your desktop .

---

### Post by siggi2 on 2015-08-15
Thank you, CantankRus, works great, too! I have learnt a lot.

Cheers, 

siggi

---

