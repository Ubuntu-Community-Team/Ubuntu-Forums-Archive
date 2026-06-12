---
title: "Opening items in Konqueror"
date: 2005-06-25
forum: Desktop Environments
---

### Post by LittleLebowski on 2005-06-25
For some reason I screwed up and had everything in Konqueror opening up in MPlayer.  Couldn't see a way to change it back to Default so I changed it to Konqueror.  Now every time I open up a folder in Konqueror, it opens up a whole new window like that ridiculous "spatial browsing" in Gnome.  Any ideas?  How do I set the File Associations back to default?

---

### Post by Xian on 2005-06-25
I would suspect the config for this is located somewhere in the /home/username/.kde/share/ path. If you are unable to find the right profile file then you might just rename the folder and see if Konq will default to its initial settings.

---

### Post by LittleLebowski on 2005-06-25
Thanks, that led me down the right path.  Ran sudo rm-rf .kde/* and logged out and logged back in.

---

### Post by ltmon on 2005-06-25
[QUOTE=LittleLebowski]Thanks, that led me down the right path.  Ran sudo rm-rf .kde/* and logged out and logged back in.[/QUOTE]

Woah... that would have nuked just about all your KDE settings.

For future reference, just delete the file ~/.kde/share/config/profilerc

L.

---

### Post by Xian on 2005-06-26
[QUOTE=ltmon]For future reference, just delete the file ~/.kde/share/config/profilerc[/QUOTE]
No such file found.
```
$ locate profilerc
$
```

---

### Post by ltmon on 2005-06-26
[QUOTE=Xian]No such file found.
```
$ locate profilerc
$
```[/QUOTE]

I think it only appears once you have changed some file associations from the default.  As such, removing it takes you back to default :)

L.

---

### Post by Xian on 2005-06-26
[QUOTE=ltmon]I think it only appears once you have changed some file associations from the default.[/QUOTE]
Confirmed. KDE is weird. :)

---

