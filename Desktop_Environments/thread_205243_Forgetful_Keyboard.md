---
title: "Forgetful Keyboard"
date: 2006-06-28
forum: Desktop Environments
---

### Post by drspangle on 2006-06-28
I installed KDE, the removed it with some hassle. After installing it my keyboard shorcuts in gnome under XGL all broke, the numlock key stays off and some keys don`t work. Normal gaim has no problems. I can fix it every boot b changing the keyboard to another type and then back to mine (ms internet keyboard). It all works fine then until the next boot.

KDE started the problem, but I think there could be some issue with the modmap being called by the startup script for my XGL session.

A symptom I that occurs is when I press my extra keys (back forwards, email etc) they show the hex(?) values until I take the above steps - then they show the XFMail or whatever they are.

Any suggestions on how to fix this up?

---

### Post by woedend on 2006-06-28
have you removed the startup script?

---

### Post by drspangle on 2006-06-28
That leaves me with the normal gnome desktop which works fine.

The script
```
killall gnome-window-decorator 
wait
gnome-window-decorator & DISPLAY=:1
compiz --replace gconf
#fixes the shift-backspace bug
xmodmap /usr/share/xmodmap/xmodmap.us
```

---

### Post by woedend on 2006-06-28
xmodmap /usr/share/xmodmap/xmodmap.us   is the offending line.  Try replacing the last line with this instead
setxkbmap -model pc105 -layout us -variant basic

edit -
before you replace it with this line, run this line from the terminal or the run box using copy and paste...if your keyboard works fine afterwords, then replace it.

---

### Post by drspangle on 2006-06-28
Thanksm that`s the kind of thing I was looking for. I`ll give it a whirl.

---

### Post by drspangle on 2006-06-28
That seems to fix the general XGL shortcut key problems, thanks.

Only 1 little niggle- my back and forward keys. Assigning them to next/previous track for audio behaves strangely, I will press once and it will be the hex then next time the X86previous then again it`s hex then hex then xf86 - it`s pretty random. Whatever I leave it on it doesn`t work with Listen or Rythmbox. All the other keys work.

---

