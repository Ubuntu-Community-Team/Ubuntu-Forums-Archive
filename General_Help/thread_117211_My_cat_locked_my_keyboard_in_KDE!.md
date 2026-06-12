---
title: "My cat locked my keyboard in KDE!"
date: 2006-01-14
forum: General Help
---

### Post by chromguy on 2006-01-14
Yesterday, I found my cat sitting on my warm keyboard of my Notebook. After that the keyboard was nonresponsive in KDE but was fine in Gnome. I found a file /home/xxx/.kde/share/config/kaccessrc

[Keyboard]
GestureConfirmation=true
Gestures=true
SlowKeys=true

I deleted the file and I'm back in business. It appears my problem was the "SlowKeys=true".  I could not find a reference to this problem on the net until I found my problem was SlowKeys... It appears that if a key is pressed for an extended period, a popup with ask if you want to enable slowkeys, apparently my cat answered YES !!

Regards,
Chromguy

---

### Post by Gowator on 2006-01-14
[QUOTE=chromguy]Yesterday, I found my cat sitting on my warm keyboard of my Notebook. After that the keyboard was nonresponsive in KDE but was fine in Gnome. I found a file /home/xxx/.kde/share/config/kaccessrc

[Keyboard]
GestureConfirmation=true
Gestures=true
SlowKeys=true

I deleted the file and I'm back in business. It appears my problem was the "SlowKeys=true".  I could not find a reference to this problem on the net until I found my problem was SlowKeys... It appears that if a key is pressed for an extended period, a popup with ask if you want to enable slowkeys, apparently my cat answered YES !!

Regards,
Chromguy[/QUOTE]


My old cat once defragged a disk ....

---

### Post by Lord Illidan on 2006-01-14
That does it. Now I know who installed Windows when I was not looking. *gets out chainsaw*

---

