---
title: "how to hide some icons in Gnome Application Overview (show applications)?"
date: 2017-11-06
forum: Desktop Environments
---

### Post by horizonbrave on 2017-11-06
I'd like to please hide some icons from the list of applications that  appear in Gnome when clicking on the Show Application 4-dots icon in the  dock. This is for preventing my parents to click on admin/system  application that may eventually mess their computer. I could avoid making their user account of the admin type but I have  anyway to provide them the password eventually so I prefer this "hiding  tweak". I've also read somewhere else then the hiding of the icons may  eventually be overwritten when applications get updated. If possible I'd  like to avoid that. Many thanks! :)

---

### Post by again? on 2017-11-06
You can copy the desktop file from /usr/share/applications to ~/.local/share/applications
The desktop file same named in ~/.local/share/applications will override the /usr/share/applications one.

Edit the relevant ~/.local/share/applications file by dragging and dropping into gedit, adding the line 
```
NoDisplay=true
```

To revert, just delete the ~/.local/share/applications file.

---

### Post by shag00 on 2017-11-06
@guber2,

you wouldn't happen to know how to turn off each individual disk icon that appears. I have looked in usr/share/applications but cannot find which one it is, if it is indeed there. There must be a better way than just making the mount points hidden folders... I have a lot of disks... Just get them off the desktop is what I'm after.

---

### Post by again? on 2017-11-06
Not sure what you mean.
By default mounted volumes aren't shown on the desktop.
Do you mean choose which ones to show?
Which release and desktop session are you using?

---

### Post by shag00 on 2017-11-06
Ah sorry, forgot to mention I am on 17.10 (Xorg/Gnome) where, annoyingly, they are all shown on the desktop.

---

### Post by again? on 2017-11-06
You can turn off showing of all mounted volumes with the command
```
dconf write /org/gnome/nautilus/desktop/volumes-visible false
```

---

### Post by shag00 on 2017-11-06
That does the trick nicely, thank you.

---

### Post by again? on 2017-11-06
I suggest you install gnome-tweak-tool where this and may other settings are available.

---

### Post by shag00 on 2017-11-06
Done, again thanks.

---

