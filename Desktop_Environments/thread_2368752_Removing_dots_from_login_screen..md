---
title: "Removing dots from login screen."
date: 2017-08-14
forum: Desktop Environments
---

### Post by Hewjr100 on 2017-08-14
Trying to remove dots from login screen, this command doesn't seem to work:

```
gsettings set com.canonical.unity-greeter draw-grid false
```

Henry

---

### Post by again? on 2017-08-14
For 17.04 create a custom unity-greeter override file.
```
gksudo gedit /usr/share/glib-2.0/schemas/10_unity_greeter_background.gschema.override
```

Copy and paste this into the file.
```
[com.canonical.unity-greeter]
draw-grid=false
```

If you want a static greeter image for all users you can also add
```
draw-user-backgrounds=false
background='[COLOR="#0000CD"]/usr/share/backgrounds/Passion_by_Vilia_Majere.jpg[/COLOR]'
```
Use your [COLOR="#0000CD"]own path to image[/COLOR]. Default backgrounds are in /usr/share/backgrounds.

Save and close file.
Run
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```

---

### Post by Hewjr100 on 2017-08-15
Just got your reply, will workon it now.

Henry

---

