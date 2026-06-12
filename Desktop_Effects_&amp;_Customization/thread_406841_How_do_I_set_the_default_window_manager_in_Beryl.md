---
title: "How do I set the default window manager in Beryl?"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by miggols99 on 2007-04-11
Whenever I log in, Beryl starts up, but doesn't change from Kwin to the Emerald window manager. I have to choose it by right clicking on the Beryl icon and selecting the Beryl window manager. How do I make Beryl start up with it's own window manager?

---

### Post by sirbats on 2007-04-11
> **miggols99 said:**
> Whenever I log in, Beryl starts up, but doesn't change from Kwin to the Emerald window manager. I have to choose it by right clicking on the Beryl icon and selecting the Beryl window manager. How do I make Beryl start up with it's own window manager?

Hi Miggols,

Have your set up the beryl properly, please follow tutorial at the following [LINKS]("http://howtoforge.org/ubuntu_feisty_beryl_ati_radeon_p3")

Have your created beryl start file :
```

sudo gedit /usr/bin/startberyl.sh

```
since you use KDE "gedit" should be changed to kwrite
```

#!/bin/sh
beryl-manager
sleep 4
exec gnome-session

```
Please modify according to your desktop. copy/paste above and change "gnome" with "kde", and save the file
and make it executable
```

sudo chmod a+x /usr/bin/startberyl.sh

```
Afterwards, we create the file /usr/share/xsessions/Beryl.desktop:
```

sudo gedit /usr/share/xsessions/Beryl.desktop

```
```

[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application

```
Then we log out of our current desktop session. On the login screen, go to Options > Select Session..., choose Beryl and click on the Change Session button. Then log in with your username and password. You will then be asked:

Do you wish to make Beryl the default for future sessions?

You can choose between Just For This Session and Make Default. If this is your first try, I recommend to select Just For This Session to see if Beryl really starts automatically. If it works, you can select Make Default at the next login.

Please visit above link.

thanks
sir Bats

---

### Post by miggols99 on 2007-04-11
Beryl starts up ok, but still starts with kwin. Is there a setting I can change in Beryl?

---

### Post by theredcross on 2007-04-11
did you try
```
emerald --replace
```

---

### Post by miggols99 on 2007-04-12
I tried that, but it did nothing...

---

### Post by miggols99 on 2007-04-13
Anyone?

By the way, I use an autostart for Beryl manager in ~/.kde/Autostart/beryl-manager

---

