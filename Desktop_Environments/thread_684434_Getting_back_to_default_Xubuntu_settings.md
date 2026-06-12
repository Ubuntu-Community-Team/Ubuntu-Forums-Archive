---
title: "Getting back to default Xubuntu settings"
date: 2008-02-01
forum: Desktop Environments
---

### Post by johnleonard on 2008-02-01
Hi

I have managed to bugger up the xfce4 desktop settings on my PC. Can someone tell me how I go back to the _out of the box_ configuration?

Thanks

---

### Post by wieman01 on 2008-02-01
You could create a new user account...

---

### Post by erfahren on 2008-02-01
log out and on the log in screen under "Sessions" there should be a Xfce default (or something similar) one there. Log in using that and if it looks like what you want make sure you have "save the session" checked when logging out or shutting down.

If you do create a new account you could look in the ~/.cache directory (hidden dir in your home - press Ctrl+H to view) - and copy the files out of there.

---

### Post by x1a4 on 2008-02-01
Hi,

Remove the following directories: 
~/.config/xfce4/
~/.config/xfce4-session/
```
rm -r ~/.config/xfce4/ ~/.config/xfce4-session/
```

then logout and log back in again.

---

