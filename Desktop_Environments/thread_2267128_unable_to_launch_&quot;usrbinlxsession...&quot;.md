---
title: "unable to launch &quot;/usr/bin/lxsession...&quot;"
date: 2015-02-27
forum: Desktop Environments
---

### Post by Jordan_Schleif on 2015-02-27
Hi there,

After logging into Lubuntu, I get this message before the desktop appears:

```
unable to launch "/usr/bin/lxsession -s Lubuntu -e LXDE" X session --- "/usr/bin/lxsession -s Lubuntu -e LXDE" not found; falling back to default session.
```

The desktop loads normally after that, and everything seems to work fine, but it's annoying to have to click to dismiss this message every login.

I've done some searching and have come across similar issues, some involve reinstalling the environment, e.g. xfce4.  But I don't know the equivalent command for Lubuntu.

Does anyone know what might be going on here?

---

### Post by steeldriver on 2015-02-27
Hello and welcome to the forums

Can you have a look in the the /usr/share/xsessions directory and report back its contents - e.g. open a terminal and use

```

ls /usr/share/xsessions

```

Also, can you clarify whether the message says usr/bin/lxsession or **/**usr/bin/lxsession?

---

### Post by Jordan_Schleif on 2015-02-27
Yeah,  that was a typo, it is "/usr/bin/lxsession".

Here is what I have in that directory.  "Lubuntu.desktop" is the session I attempt to use upon login.
```
Lubuntu.desktop  Lubuntu-Netbook.desktop  openbox.desktop
```

Here is the contents of Lubuntu.desktop:

```
[Desktop Entry]
# The names/descriptions should really be better
Name=Lubuntu
Comment=Lubuntu - Lightweight X11 desktop environment based on LXDE
Comment[zh_TW]=Lubuntu - &#36629;&#37327;&#32026;&#30340; X11 &#26700;&#38754;&#29872;&#22659;
Comment[fi]=Lubuntu - kevyt X11-työpöytäympäristö
Comment[ja]=Lubuntu - &#36605;&#37327;&#12394; X11 &#12487;&#12473;&#12463;&#12488;&#12483;&#12503;&#29872;&#22659;
Exec=/usr/bin/lxsession -s Lubuntu -e LXDE
# Icon=
Type=Application

```

---

### Post by steph.schie on 2015-05-22
/usr/bin/lxsession was missing.

```
[COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall lxsession[/FONT][/COLOR]
``` 

[COLOR=#111111][FONT=Consolas]helped me to log back in and start Lubuntu.


[/FONT][/COLOR]

---

