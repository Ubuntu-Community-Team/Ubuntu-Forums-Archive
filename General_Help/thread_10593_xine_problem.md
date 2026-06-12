---
title: "xine problem"
date: 2005-01-09
forum: General Help
---

### Post by Markus78 on 2005-01-09
hi!

i'm running gxine for dvds but i only have sound when i start the programm form the terminal. if i start it form the menu i don't have the sound. strange for me because as i said it works perfecly the other way. anyone the same problem?

---

### Post by Mumra on 2005-02-06
I figured this one out - it's because the sound server, by default, can only play one sound. When you click the button in a menu, you get a little "pock" sound which occupies the sound server, denying it to your application (in this case Xine). A workaround is to just disable sounds for events (in Computer -> Desktop Prefs -> Sound).

---

