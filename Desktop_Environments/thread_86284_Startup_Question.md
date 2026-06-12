---
title: "Startup Question"
date: 2005-11-04
forum: Desktop Environments
---

### Post by OtubrabNad on 2005-11-04
Every time I log onto Ubuntu the Evolution Setup Assistant loads up. How do I disable this? If this were Windows all I would have to do is run msconfig and take Evolution off the Startup menu. How do I do the Linux equivilant of this?

---

### Post by Kapre on 2005-11-04
[QUOTE=OtubrabNad]Every time I log onto Ubuntu the Evolution Setup Assistant loads up. How do I disable this? If this were Windows all I would have to do is run msconfig and take Evolution off the Startup menu. How do I do the Linux equivilant of this?[/QUOTE]

OtubrabNad - Go to System-----Preferences------Sessions----Look into the folders (most probably on the current session folder) for the Evolution app.

K

---

### Post by OtubrabNad on 2005-11-04
I removed them and applied the changes but it didn't work. The Evolution Startup Assistant still appeared when I logged back on after logging off.

---

### Post by arnieboy on 2005-11-04
[QUOTE=OtubrabNad]I removed them and applied the changes but it didn't work. The Evolution Startup Assistant still appeared when I logged back on after logging off.[/QUOTE]
u cud try the following:
```
rm -rf $HOME/.evolution
```
if u dont want evolution at all:
```
sudo apt-get remove evolution
```

---

### Post by felix_stegerman on 2005-11-04
[QUOTE=OtubrabNad]I removed them and applied the changes but it didn't work. The Evolution Startup Assistant still appeared when I logged back on after logging off.[/QUOTE]

Did you remember to save your session (after making those changes) when logging out?


Felix

---

### Post by OtubrabNad on 2005-11-04
[QUOTE=felix_stegerman]Did you remember to save your session (after making those changes) when logging out? [/QUOTE]

That did it, thanks.

---

