---
title: "Moving Buttons To Left - Keep Moving Back!"
date: 2011-03-27
forum: Desktop Environments
---

### Post by fullmoonguru on 2011-03-27
I like the buttons on the left.  I'm running 10.04 & I know how to move them.  The problem is that changing themes will move them back right.  OK, if the new theme has them on the right that's OK.  But going back to the other theme doesn't change them back.  They don't seem to be controlled by the theme, or I'm just not doing it right.  Anyway, I'm wondering how to make them stay there.

---

### Post by Krytarik on 2011-03-27
If you want to make the chosen button layout "mandatory", see this earlier post:
[http://ubuntuforums.org/showthread.php?p=10602275](http://ubuntuforums.org/showthread.php?p=10602275)

If you want to change the button layout of the themes independendly, modify its "index.theme" file, located at the toplevel of the theme's directory. You need to open it from within the text editor!
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Ambiance
Comment=Ubuntu Ambiance theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Ambiance
MetacityTheme=Ambiance
IconTheme=ubuntu-mono-dark
CursorTheme=DMZ-White
[COLOR=Red]**ButtonLayout=close,minimize,maximize:**[/COLOR]
```
Greetings.

---

### Post by tgm4883 on 2011-03-27
> **fullmoonguru said:**
> I like the buttons on the left.  I'm running 10.04 & I know how to move them.  The problem is that changing themes will move them back right.  OK, if the new theme has them on the right that's OK.  But going back to the other theme doesn't change them back.  They don't seem to be controlled by the theme, or I'm just not doing it right.  Anyway, I'm wondering how to make them stay there.

The change you are making isn't for the theme. It's for the enviroment. When you change themes it changes whatever setting you made in gconf-editor. Thats why when you switch away then switch back it reverts to the other side.

---

