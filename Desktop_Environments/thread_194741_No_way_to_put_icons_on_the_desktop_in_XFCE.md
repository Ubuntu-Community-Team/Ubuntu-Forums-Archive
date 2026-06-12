---
title: "No way to put icons on the desktop in XFCE??"
date: 2006-06-11
forum: Desktop Environments
---

### Post by skelooth on 2006-06-11
I set up xubuntu on an old computer for my mother to basically just use email and maybe gaim. xubuntu it's self runs GREAT on the computer, but there does not seem to be a way to put things on the desktop?

My mom doesn't know ANYTHING about computers.....

I would really like to be able to put a link to her email on her desktop (not on a panel), and it is going to confuse the hell out of her if she can't save things to the desktop, b/c she won't be able to find them.

---

### Post by psychicdragon on 2006-06-11
If I remember correctly desktop file icons are turned on by default in Xubuntu.

You can turn them on in the Desktop Preferences applet in the Xfce Settings Manager. The option is in the Behaviour tab.

---

### Post by MetalMusicAddict on 2006-06-11
Fo me I just cant see how to create a new launcher.:-?

EDIT - I figured it out.

In your "Desktop" folder create a new document and end it with .desktop like: UT2004.desktop. Then within the document add these lines:

```
[Desktop Entry]
Encoding=
Name=
Comment=
Exec=
Icon=
Terminal=
StartupNotify=
Type=
```

Heres mine for UT2004
```

[Desktop Entry]
Encoding=[COLOR="Red"]UFT-8[/COLOR]
Name=[COLOR="Red"]UT2004[/COLOR]
Comment=[COLOR="Red"]FPS[/COLOR]
Exec=[COLOR="Red"]/home/atm/.ut2004/ut2004[/COLOR]
Icon=[COLOR="Red"]/home/atm/UT2k3.png[/COLOR]
Terminal=[COLOR="Red"]False[/COLOR]
StartupNotify=[COLOR="Red"]true[/COLOR] <-dont know if this one makes a difference.
Type=[COLOR="Red"]Application[/COLOR]
```

Heres the screen I based this on.

[IMG]http://static.flickr.com/47/127157613_4350ecbd04.jpg?v=0[/IMG]

I wonder if I can add custom font and icon sizes to the config?

---

### Post by skelooth on 2006-06-11
awesome, thanks psychic

Metal, right click on a panel, choose add to panel, select new launcher.... then you have to manually set the icon (icons are in /usr/share/pixmaps) and you have to write the command

---

### Post by MetalMusicAddict on 2006-06-11
skelooth I was going for Desktop icons. Not on a panel. I edited my above post. ;)

---

