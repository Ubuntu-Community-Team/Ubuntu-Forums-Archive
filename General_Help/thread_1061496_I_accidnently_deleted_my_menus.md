---
title: "I accidnently deleted my menus?????"
date: 2009-02-05
forum: General Help
---

### Post by Serrya on 2009-02-05
Hi I did something really stupid. I accidently deleted my menus on top (the Gnome menus) like the ones that say "Application" "Places" etc...any one know how to get them back?

---

### Post by Virtualboxbuntu on 2009-02-05
Right-click on the panel, click Add to Menu, scroll down to Menu Bar, add it to panel.

---

### Post by wstout on 2009-02-05
Give this a try. This should restore your GNOME panels back to the defaults.
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel 
pkill gnome-panel 
```

---

### Post by Serrya on 2009-02-05
OH MY GOD!!!!! Thank you SO much!! thank you thank you!! I have made a mental note to never do that again! Thank you so much again!

---

