---
title: "Unity Showing &quot;Ubuntu Desktop&quot; on Upper Left Corner"
date: 2012-06-29
forum: Desktop Environments
---

### Post by eyeprotocol on 2012-06-29
Hello all. As you are propably aware, a default installation of 12.04 results in the standard desktop environment, which shows the phrase "Ubuntu Desktop" at the left side of the upper panel (or, to put it otherwise, the upper left corner of the screen). I find it annoying and wish i could replace it with something more meaningfull, say.. the name of the machine, or any other phrase. Can it be done?

Thank you in advance.

---

### Post by stinkeye on 2012-06-29
Not that I am aware of but it can be removed by using **gnome-tweak-tool**
to disable nautilus drawing the desktop.
or in the terminal...
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
You will lose right click desktop menu and desktop icons.


Set back to defaults...
```
gsettings reset org.gnome.desktop.background show-desktop-icons
```

---

### Post by tahseen on 2012-07-21
But this method would also remove nice shadow effect under the panel.


Point is to remove the text coming and not disabling file manager from handling panel

File Manager is reading from somewhere the text Ubuntu Desktop. That has to be changed with spaces or another text

---

### Post by phpJoel on 2012-11-29
Also currently looking for a proper solution for this.

---

### Post by mc4man on 2012-11-30
> **phpJoel said:**
> Also currently looking for a proper solution for this.
This is hard-coded into the unity source so to change one would have to rebuild unity with a source code edit.
In the case of this thread (12.04, unity 5.16) you'd find in 
unity-5.16.0/plugins/unityshell/src/PanelMenuView.cpp @ line 78 - 
see screen

---

### Post by phpJoel on 2012-11-30
> **mc4man said:**
> This is hard-coded into the unity source

Indeed it is.
Really wish this was an option somewhere or something.. Doubt they would make branding optional.

Perhaps I will edit and build mine.. I saw [instructions at askUbuntu.com]("http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source").

Thanks for replying.

---

### Post by kostkon on 2012-11-30
> **phpJoel said:**
> Indeed it is.
Really wish this was an option somewhere or something.. Doubt they would make branding optional.

Perhaps I will edit and build mine.. I saw [instructions at askUbuntu.com]("http://askubuntu.com/questions/28470/how-do-i-build-unity-from-source").

Thanks for replying.
Or instead of rebuilding unity yourself, and since it is a translatable string (_() is the usual name given to gettext.gettext() in the local namespace) then you could edit or create a new translation for that string for the language you have set in ubuntu? I mean edit the translation files for that part of unity or create them (if necessary).

---

