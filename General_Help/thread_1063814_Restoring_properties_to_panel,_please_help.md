---
title: "Restoring properties to panel, please help"
date: 2009-02-08
forum: General Help
---

### Post by philidox on 2009-02-08
I have delete my default bottom panel which I have restored. However getting it back to normal is a challenge.  Active programs/windows are not showing up in my panel.  I have restored my show desktop and workspace icons to my panel, just need one more.  Thanx

---

### Post by Wartender on 2009-02-08
i believe that is the window list... thingy

---

### Post by overlord.gaurav on 2009-02-08
Yes, its the "Window List".

If you've messed up your panels and you wish to restore it to its defaults, try this:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by philidox on 2009-02-08
Thank you, thank you, thank you

---

### Post by abbaseo on 2009-02-08
indeed it worked for novice like me too, cheers

---

