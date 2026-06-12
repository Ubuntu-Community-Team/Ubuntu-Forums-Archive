---
title: "[SOLVED] How to use Emerald instead of Metacity, with Compiz Fusion on Gutsy?"
date: 2007-12-05
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-12-05
Do I just install Emerald via Synaptic?

---

### Post by divague on 2007-12-05
yes, and next time you login it'll be instead of metacity

---

### Post by rainwalker on 2007-12-05
Ooh neat!
Are there any known problems with using Emerald?

---

### Post by divague on 2007-12-05
i installed emerald last week, and so far i haven't got any problems

---

### Post by rainwalker on 2007-12-05
If I want to go back to using Metacity (for good), do I just uninstall Emerald?

---

### Post by divague on 2007-12-05
yes, i think uninstalling emerald will enable metacity

---

### Post by rainwalker on 2007-12-06
Yep, that did it

---

### Post by FuturePilot on 2007-12-06
You can also do
```
gedit .config/compiz/compiz-manager
```
And paste this in there
```
USE_EMERALD="no"
```
That will make it use the gtk-window-decorator instead. If you want Emerald again, change it to "yes"

---

