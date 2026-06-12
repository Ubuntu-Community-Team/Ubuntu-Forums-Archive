---
title: "Milke GTK Theme Not Applying itself to certain dialogs"
date: 2009-08-09
forum: Desktop Environments
---

### Post by coldReactive on 2009-08-09
See attachment

---

### Post by mcduck on 2009-08-09
Those programs run as root user, while you have probably only installed the theme for your normal user account.

If you want the theme to be available for all users you need to install it into /usr/share/themes.

Alternatively, there's a nice trick that makes all your normal user's themes available for root by linking your personal theme directory into root's theme directory:
```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```
This way apps running as root will always have the same theme your normal user has.

---

### Post by coldReactive on 2009-08-09
Is the linking permanent? Or would I have to do it again?

---

### Post by mcduck on 2009-08-09
The link is permanent, it's there until you remove it yourself.

---

