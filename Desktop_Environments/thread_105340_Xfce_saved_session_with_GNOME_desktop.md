---
title: "Xfce saved session with GNOME desktop"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Granduke on 2005-12-18
Running Xfce I pulled up Nautilus forgetting to add --no-desktop. This added the Gnome desktop to the presentation.  Then I ended the session with save settings checked.
Now when I log into Xfce Gnome is there also.  How to I stop this autostart and go back to plain Xfce?

---

### Post by aysiu on 2005-12-18
Alt-F2.
```
xfdesktop
```
Save your session again.

---

### Post by Granduke on 2005-12-18
No. That didn't work.  The desktop flickered but the brown Gnome desktop with icons 
remained.

---

### Post by psychicdragon on 2005-12-18
**killall nautilus** first then run **xfdesktop &**. Make sure to save your session on log out.

---

### Post by Granduke on 2005-12-18
Thanks pyschicdragon- that fixed it.

---

