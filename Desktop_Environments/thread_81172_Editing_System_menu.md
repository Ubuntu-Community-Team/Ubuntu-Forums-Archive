---
title: "Editing System menu?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by IanH on 2005-10-23
Hello,

Does anyone know how to add items to the System menu in Gnome? Smeg only handles the Applications menu. I've tried editing the .desktop files by hand, but I cannot find what I have to add to make them appear under the System menu.

Thanks.

---

### Post by Sutekh on 2005-10-23
[QUOTE=IanH]Hello,

Does anyone know how to add items to the System menu in Gnome? Smeg only handles the Applications menu. I've tried editing the .desktop files by hand, but I cannot find what I have to add to make them appear under the System menu.

Thanks.[/QUOTE]


Just checking out the ubuntuguide at the nvidia section [http://www.ubuntuguide.org/#installnvidiadriver]("http://www.ubuntuguide.org/#installnvidiadriver")
this is the .desktop file used for the nvidia-settings that you could use a template...

```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
**Categories=Application;System;**
```

The last line Categories puts the nvidia settings in the Applications -> System menu.

So for your app, try adding that line to your .desktop file.  I can't test it at the moment because I'm at work, but that should work.

---

### Post by IanH on 2005-10-24
Thanks, but I was trying to put it in the top-level System menu (the one to the  right of "Places"). Is there a way to do that?

---

### Post by Sutekh on 2005-10-25
Do you want the entry in the System Menu along with "Take Screenshot", "Help", etc?  Or in the Preferences or Administration menu?

I found that

Categories=GNOME;Application;Settings;

will put the entry into the System -> Preferences and

Categories=Application;System;Settings

will put the entry into the System -> Administration menu.

But not the main System menu. I just copied the entries from other applications. :( Perhaps a kind developer could help?

---

### Post by IanH on 2005-10-25
Yes, that's what I've been trying to do. I've been able to add them to the System -> Adminstration menu, but not the main one. I tried copying the Categories line from the 'Help' entry, but that didn't seem to work.

---

