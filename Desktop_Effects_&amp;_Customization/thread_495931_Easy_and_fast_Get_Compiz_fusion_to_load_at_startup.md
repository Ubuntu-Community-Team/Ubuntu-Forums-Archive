---
title: "Easy and fast: Get Compiz fusion to load at startup"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Ekeluo on 2007-07-08
I got this from [http://suseforums.net/index.php?showtopic=26192](http://suseforums.net/index.php?showtopic=26192). Worked like a dream. Might want to shorten the sleep time though. Just changed all "beryl" to "Compiz".
[COLOR="Lime"]
"Howt o install Compiz as a normal xsession option in the KDE login manager, assuming you are using KDE and kdm is your display manager (and you have successfully installed Compiz)

In /usr/share/xsessions create a text file called beryl.desktop with the following content:

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Name=Compiz
Exec=/usr/bin/compiz.sh
Icon=
Type=Application


In /usr/bin create a text file called compiz.sh with the following content:

#!/bin/sh
#
# KDE with AIXGL startup script
#
compiz &
sleep 10
startkde


Make compiz.sh executable (right click in konq>properties>permissions>is executable.

Disable your kde splash screen in kcontrol.

The above will place an option called "Compiz" in the session options of the KDE login manager.

To enable Compiz log out>end current session, select Copmiz from the session options and then login. The script will start Copmiz before kde so you should see a nice Copmiz splash screen and KDE launched as though Copmiz is the default dm.

???Other tips:
Install the compiz desktop preview and pager applet if you want the kicker pager to work properly. Disable gui effects in the kcontrol>appearance & themes>style>effects tab. Use Beryl effects instead.???
[/COLOR]

Worked flawlessly on 1.6Ghz Pentium M with only 256mb ram. Reduced my sleep to 5.

+ I found it didn't load customized plugins and settings, made the ff changes:
Changes **compiz &** in compiz.sh to **/usr/bin/compiz**, then exported profile (from compizconfig settings manager) as **Default.ini** to ~/.compizconfig/. (be sure to change the permissions on it since ccsm exports it as executable (deactivate exec and enable read/write for user). Should work fine then. Works on my system. (Intel GMA 915, 256mb ram). Hope 2 upgrade my ram soon though.

---

### Post by gimfred on 2007-07-24
> "Howto install Compiz as a normal xsession option in the KDE login manager, assuming you are using KDE and kdm is your display manager (and you have successfully installed Compiz)

In /usr/share/xsessions create a text file called compiz.desktop with the following content:

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Name=Compiz
Exec=/usr/bin/compiz.sh
Icon=
Type=Application


In /usr/bin create a text file called compiz.sh with the following content:

#!/bin/sh
#
# KDE with AIXGL startup script
#
compiz &
sleep 10
startkde


Make compiz.sh executable (right click in konq>properties>permissions>is executable.

Disable your kde splash screen in kcontrol.

The above will place an option called "Compiz" in the session options of the KDE login manager.

To enable Compiz log out>end current session, select Copmiz from the session options and then login. The script will start Copmiz before kde so you should see a nice Copmiz splash screen and KDE launched as though Copmiz is the default dm.

???Other tips:
Install the compiz desktop preview and pager applet if you want the kicker pager to work properly. Disable gui effects in the kcontrol>appearance & themes>style>effects tab. Use compiz effects instead.???

Just to get away from that horrible colour & and I did the beryl -> compiz swap. Much easier to read; thank you though.

---

### Post by BDNiner on 2007-07-25
How do i disable the splash screen in kcontrol? I have looked all over the place and must be missing something. Nevermind, i found the option.

---

### Post by BDNiner on 2007-07-25
All i get when i try this is a blank screen. I still have a mouse pointer and can move it, but the screen stays black. How long does it take for you guys to log in?

---

