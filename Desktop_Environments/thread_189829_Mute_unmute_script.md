---
title: "Mute unmute script"
date: 2006-06-05
forum: Desktop Environments
---

### Post by chronusdark on 2006-06-05
i need help figureing out how to unmute my line in then launch tvtime then mute it when i kill the app im sure this is really easy can someone help me?

---

### Post by chronusdark on 2006-06-05
nvm i figured it out 

```
amixer set Line 0 100%,100% unmute
```

---

### Post by franganghi on 2008-05-06
I used it in blueproximity to deactivate audio when i am away from my station:
gnome-screensaver-command -l|amixer set Headphone mute -> in the lock command box
gnome-screensaver-command -l|amixer set Headphone unmute -> in the unlock command box

thank you for the hint!

joe

---

