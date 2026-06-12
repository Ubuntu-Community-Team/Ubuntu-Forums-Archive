---
title: "Create menu items for non-repo apps"
date: 2013-01-11
forum: Desktop Environments
---

### Post by toniocus on 2013-01-11
I installed eclipse in /opt directory, not from repository (and I have a lot more applications in /opt not from the repository).

So UNITY does not find them !!!!!!!!!!!!, how can I have a menu for them ?

Remember free software is about free software not about bundled applications
inside a given distribution.

And of course don't tell me add it to the DASH bar, I'll need to use a 2 meters height
 monitor for it

Please tell me

---

### Post by oldos2er on 2013-01-11
Post moved to its own thread.

---

### Post by ibjsb4 on 2013-01-11
> And of course don't tell me add it to the DASH bar, I'll need to use a 2 meters height

six and a half feet  :confused:

---

### Post by stinkeye on 2013-01-11
> **toniocus said:**
> I installed eclipse in /opt directory, not from repository (and I have a lot more applications in /opt not from the repository).

So UNITY does not find them !!!!!!!!!!!!, how can I have a menu for them ?

Remember free software is about free software not about bundled applications
inside a given distribution.

And of course don't tell me add it to the DASH bar, I'll need to use a 2 meters height
 monitor for it

Please tell me
Create a **.desktop** file in **~/.local/share/applications**
and the dash will pick it up.
Other launchers like Kupfer will also pick it up.

eg My **GuitarScaleExpert.desktop** file...
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=/opt/GuitarScaleExpert/GuitarScaleExpert
Name=GuitarScaleExpert
Icon=/home/glen/Pictures/guitar.png
```

---

